# Import
(*content.import_*)

## Overview

### Available Operations

* [create_import_job](#create_import_job) - Create Import Job
* [get_validation_hooks](#get_validation_hooks) - Get validation hooks
* [create_validation_hook](#create_validation_hook) - Create validation hook
* [get_validation_hook_versions](#get_validation_hook_versions) - Get all versions for a validation hook
* [create_validation_hook_version](#create_validation_hook_version) - Update validation hook version
* [get_validation_hook_version](#get_validation_hook_version) - Get validation hook version details
* [get_import_status](#get_import_status) - Get Job Status
* [create_import_validation_job](#create_import_validation_job) - Create Validation Job
* [cancel_import](#cancel_import) - Cancel Job

## create_import_job

# Import Content

## Overview
This API initiates a bulk content import operation from Data Sources. It creates an asynchronous import job that processes content in the background, allowing you to import large volumes of content without blocking your application.

## Pre-requisties
1. Content in Data Source needs to be in this format: [Guide to Data Import Format](https://apidev.egain.com/developer-portal/guides/ingestion/data-import-format-guide/)

## How It Works
1. **Job Creation**: The API creates an import job and returns a unique job ID
2. **Content Processing**: Content is processed asynchronously in the background
3. **Status Monitoring**: Use the job ID to monitor progress via the Status API
4. **Completion**: Job completes when all content is processed or errors occur

**Note:** After a successful import, please allow for a brief delay before the content is fully available for use. The system's search service synchronizes all new and updated content every 30 minutes.

## Supported Operations
- **Import**: Add new content to the knowledge base
- **Update**: Modify existing content

## Data Source Types
- AWS S3 bucket
- Shared file path

## Best Practices
- **Scheduling**: Use scheduleTime for off-peak imports to minimize system impact. Please note that jobs can only be scheduled for a maximum of 7 days from the current date and time.
- **Monitoring**: Regularly check job status and logs for any issues
- **Error Handling**: Review failed items and retry with corrections

## Job Timing Controls
- **scheduleTime.stopDate**: Defines a specific date time to cease operations regardless of progress (e.g., "Stop exactly at 5:00 PM").


### Example Usage

<!-- UsageSnippet language="python" operationID="createImportJob" method="post" path="/import/content" -->
```python
from egain_api_python import Egain
from egain_api_python.utils import parse_datetime
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.create_import_job(data_source={
        "type": "AWS S3 bucket",
        "path": "s3://mybucket/myfolder/",
        "region": "us-east-1",
        "credentials": {
            "access_key_id": "AKIAIOSFODNN7EXAMPLE",
            "secret_access_key": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
        },
    }, operation="import", schedule_time={
        "date_": parse_datetime("2024-03-01T10:00:00.000Z"),
        "stop_date": parse_datetime("2024-03-05T10:00:00.000Z"),
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `data_source`                                                             | [models.ImportContentDataSource](../../models/importcontentdatasource.md) | :heavy_check_mark:                                                        | N/A                                                                       |
| `operation`                                                               | [models.Operation](../../models/operation.md)                             | :heavy_check_mark:                                                        | N/A                                                                       |
| `schedule_time`                                                           | [Optional[models.ScheduleTime]](../../models/scheduletime.md)             | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |
| `server_url`                                                              | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | An optional server URL to use.                                            |

### Response

**[models.CreateImportJobResponse](../../models/createimportjobresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.SchemasWSErrorCommon | 406                         | application/json            |
| errors.WSErrorCommon        | 400, 401, 403, 412          | application/json            |
| errors.WSErrorCommon        | 500                         | application/json            |
| errors.EgainDefaultError    | 4XX, 5XX                    | \*/\*                       |

## get_validation_hooks

Retrieve all validation hooks configured for the current environment. Only the current version of each hook is returned.


### Example Usage

<!-- UsageSnippet language="python" operationID="getValidationHooks" method="get" path="/import/config/hooks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.get_validation_hooks()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `type`                                                              | [Optional[models.HookTypeParam]](../../models/hooktypeparam.md)     | :heavy_minus_sign:                                                  | Filter by hook type.                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Response

**[models.Hooks](../../models/hooks.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 401                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## create_validation_hook

# Create Validation Hook

## Overview
This API allows you to create custom JavaScript-based validation hooks that execute during the bulk content ingestion process. Validation hooks enable organizations to enforce specific business rules, verify metadata compliance, and perform complex data integrity checks that go beyond standard system validation.

## Usage Requirements
To ensure successful hook creation and execution, please adhere to the following:
- **Content Encoding**: The `fileObject.file.content` property must be a **Base64 encoded** string of your JavaScript logic.
- **File Naming**: The filename should use the `.js` extension.
- **Logic Return**: Your script must return a `result` object containing a boolean `success` property.
- **Size Limit**: The encoded content must not exceed 1.5MB.

## Hook Types
- **Pre-Validation Hooks (`import_pre_validation_hook`)**: These execute **before** the standard system validation. They are ideal for enforcing custom business rules, such as ensuring all articles contain specific metadata.
- **Post-Validation Hooks (`import_post_validation_hook`)**: These execute **after** the standard system validation. They have access to the `validationResults` from the system check, allowing you to block an import based on the severity of errors found.

## Execution Environment
Hooks run in a secure, sandboxed JavaScript environment (ES5/ES6). 
- **Prohibited**: File system access (`fs`), network access (HTTP requests), and module loading (`require`).
- **Supported**: Standard JavaScript logic, `console.log()` for debugging, and a specialized `helpers` utility library for safe data access.

## Implementation Examples

### Example: Pre-Validation Logic
This example demonstrates checking that every article contains a specific metadata field.
```javascript
// Initialize result
var result = { success: true };

// Verify data exists
if (helpers.hasField(data, 'articles') && helpers.isNotEmpty(data.articles)) {
  
  var invalidArticles = [];
  
  for (var i = 0; i < data.articles.length; i++) {
    var article = data.articles[i];
    
    if (!helpers.hasField(article, 'name')) {
      invalidArticles.push({ index: i, issue: "Missing name" });
      continue;
    }

    // Custom Rule: Check if 'description' exists in metadata
    if (!helpers.hasField(article, 'metadata') || 
        !helpers.hasField(article.metadata, 'description') || 
        helpers.isEmpty(article.metadata.description)) {
          
      invalidArticles.push({ 
        name: article.name, 
        issue: "Missing required description metadata" 
      });
    }
  }
  
  if (invalidArticles.length > 0) {
    result = {
      success: false,
      error: 'Articles failed custom metadata validation',
      details: { count: invalidArticles.length, errors: invalidArticles }
    };
  }
}
result;
```

### Example: Post-Validation Logic
This example checks the standard validation results. If there are standard errors, it logs them and fails the job explicitly.
```javascript
var result = { success: true };

// Check if standard validation found errors
if (helpers.hasField(validationResults, 'errors') && validationResults.errors.length > 0) {
  
  var errorCount = validationResults.errors.length;
  console.log('Standard validation found ' + errorCount + ' errors.');

  var errorTypes = {};
  validationResults.errors.forEach(function(err) {
    var type = err.type || 'unknown';
    errorTypes[type] = (errorTypes[type] || 0) + 1;
  });

  result = {
    success: false,
    error: 'Standard validation failed with ' + errorCount + ' errors.',
    details: {
      summary: errorTypes,
      firstError: validationResults.errors[0].message
    }
  };
}
result;
```

## Further Documentation
For more detailed context on available objects (`data`, `metadata`, `helpers`) and best practices, refer to the [Validation Hook Guide](https://apidev.egain.com/developer-portal/guides/ingestion/validation-hook-guide/#example-pre-validation-logic).


### Example Usage

<!-- UsageSnippet language="python" operationID="createValidationHook" method="post" path="/import/config/hooks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.content.import_.create_validation_hook(type_="import_post_validation_hook", file_object={
        "file": {
            "name": "check_dept_tags.js",
            "content": "dmFyIGl0ZW0gPSBjb250ZXh0Lml0ZW07",
        },
    })

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `type`                                                              | [models.HookType](../../models/hooktype.md)                         | :heavy_check_mark:                                                  | N/A                                                                 |
| `file_object`                                                       | [models.FileObject](../../models/fileobject.md)                     | :heavy_check_mark:                                                  | N/A                                                                 |
| `hook_id`                                                           | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | ID of hook                                                          |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Name of the hook.                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_validation_hook_versions

Retrieve a history of all versions uploaded for a specific validation hook.

### Example Usage

<!-- UsageSnippet language="python" operationID="getValidationHookVersions" method="get" path="/import/config/hooks/{hookID}/version" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.get_validation_hook_versions(hook_id=923549)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `hook_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Integer ID of the Hook resource.                                    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Response

**[List[models.FileObject]](../../models/.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 404                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## create_validation_hook_version

Upload a new version of the JavaScript logic for an existing hook.

### Example Usage

<!-- UsageSnippet language="python" operationID="createValidationHookVersion" method="post" path="/import/config/hooks/{hookID}/version" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.content.import_.create_validation_hook_version(hook_id=410019)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `hook_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Integer ID of the Hook resource.                                    |
| `file_id`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | ID of Hook File                                                     |
| `created_date`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The date on which the resource was last modified.                   |
| `created_by`                                                        | [Optional[models.CreatedBy]](../../models/createdby.md)             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `modified_date`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | The date on which the resource was last modified.                   |
| `modified_by`                                                       | [Optional[models.ModifiedBy]](../../models/modifiedby.md)           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `version`                                                           | [Optional[models.Version]](../../models/version.md)                 | :heavy_minus_sign:                                                  | N/A                                                                 |
| `file`                                                              | [Optional[models.File]](../../models/file.md)                       | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 404                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_validation_hook_version

Get details and content URL for a specific version of a hook.

### Example Usage

<!-- UsageSnippet language="python" operationID="getValidationHookVersion" method="get" path="/import/config/hooks/{hookID}/version/{versionID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.get_validation_hook_version(hook_id=276494, version_id=148818)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `hook_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Integer ID of the Hook resource.                                    |
| `version_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | The sequential version number of the hook (e.g., 1, 2, 3).          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Response

**[models.FileObject](../../models/fileobject.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 404                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_import_status

# Get Import Job Status

## Overview
This API provides real-time status information for content import and validation operations. Use this endpoint to monitor job progress, check completion status, and access detailed logs and error information.

## Status Values
- **Scheduled**: Job is queued and waiting for scheduled execution time
- **In Progress**: Job is actively processing content
- **Completed**: Job finished successfully
- **Failed**: Job encountered errors and could not complete
- **Cancelled**: Job was manually cancelled by user

## Response Information
- **Current Status**: Real-time job status
- **Progress Metrics**: Items processed, total items, completion percentage
- **Log Files**: Location of detailed operation logs
- **Error Details**: Specific errors encountered during processing
- **Timing Information**: Start time, estimated completion, actual completion

## Log File Access
Log files contain detailed information about:
- Content processing steps
- Validation results
- Error details with context


### Example Usage

<!-- UsageSnippet language="python" operationID="getImportStatus" method="get" path="/import/content/{job_id}/status" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.get_import_status(job_id="7A84B875-6F75-4C7B-B137-0632B62DB0BD")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                      | Type                                                                                                                                                                                                                                                                                                                           | Required                                                                                                                                                                                                                                                                                                                       | Description                                                                                                                                                                                                                                                                                                                    | Example                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `job_id`                                                                                                                                                                                                                                                                                                                       | *str*                                                                                                                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                                                                                             | **Job ID Parameter**<br/><br/>The unique identifier for the import or validation job. This ID was returned when the job was created via the Import or Validate API.<br/><br/>**Format:** UUID v4 (e.g., 7A84B875-6F75-4C7B-B137-0632B62DB0BD)<br/><br/>**Example Usage:**<br/>```bash<br/>GET /import/content/7A84B875-6F75-4C7B-B137-0632B62DB0BD/status<br/>```<br/> | 7A84B875-6F75-4C7B-B137-0632B62DB0BD                                                                                                                                                                                                                                                                                           |
| `retries`                                                                                                                                                                                                                                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                             | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                |
| `server_url`                                                                                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                             | An optional server URL to use.                                                                                                                                                                                                                                                                                                 | http://localhost:8080                                                                                                                                                                                                                                                                                                          |

### Response

**[models.ImportStatus](../../models/importstatus.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.WSErrorCommon        | 400, 401, 403, 404          | application/json            |
| errors.SchemasWSErrorCommon | 406                         | application/json            |
| errors.WSErrorCommon        | 500                         | application/json            |
| errors.EgainDefaultError    | 4XX, 5XX                    | \*/\*                       |

## create_import_validation_job

# Validate Import Content

## Overview
This API enables users to validate content structure, format, and compliance before importing it into the production knowledge base. Validation is a non-destructive operation that checks content without making any changes to your existing data.

## What Validation Checks
- **Content Structure**: Verifies required fields and data types
- **Format Compliance**: Ensures content meets platform requirements
- **Language Support**: Validates content against supported languages
- **Metadata Mapping**: Checks field mappings and transformations
- **Business Rules**: Validates against department-specific rules

## Validation Benefits
- **Risk Mitigation**: Identify issues before affecting production data
- **Quality Assurance**: Ensure content meets organizational standards
- **Cost Savings**: Avoid failed imports that waste processing time
- **Compliance**: Meet regulatory and internal content requirements

## Validation Process
1. **Content Analysis**: System analyzes content structure and format
2. **Rule Validation**: Applies business rules and validation logic
3. **Quality Assessment**: Evaluates content quality and completeness
4. **Report Generation**: Creates detailed validation report
5. **Issue Categorization**: Classifies issues by severity and type

## Common Validation Issues
- **Missing Required Fields**: Title, description, category, etc.
- **Invalid Data Types**: Incorrect field formats (dates, numbers, etc.)
- **Language Mismatches**: Content language not supported by department

## Best Practices
- **Always Validate First**: Run validation before any import operation
- **Review Reports**: Carefully examine validation results and warnings
- **Fix Issues**: Address validation errors before proceeding with import
- **Test Small Batches**: Validate with small content samples first
- **Iterate**: Use validation feedback to improve content quality


### Example Usage

<!-- UsageSnippet language="python" operationID="createImportValidationJob" method="post" path="/import/content/validate" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.import_.create_import_validation_job(data_source={
        "type": "AWS S3 bucket",
        "path": "s3://mybucket/myfolder/",
        "region": "us-east-1",
        "credentials": {
            "access_key_id": "AKIAIOSFODNN7EXAMPLE",
            "secret_access_key": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
        },
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                 | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `data_source`                                                                             | [models.ValidateImportContentDataSource](../../models/validateimportcontentdatasource.md) | :heavy_check_mark:                                                                        | N/A                                                                                       |
| `retries`                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                          | :heavy_minus_sign:                                                                        | Configuration to override the default retry behavior of the client.                       |
| `server_url`                                                                              | *Optional[str]*                                                                           | :heavy_minus_sign:                                                                        | An optional server URL to use.                                                            |

### Response

**[models.CreateImportValidationJobResponse](../../models/createimportvalidationjobresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.SchemasWSErrorCommon | 406                         | application/json            |
| errors.WSErrorCommon        | 400, 401, 403, 412          | application/json            |
| errors.WSErrorCommon        | 500                         | application/json            |
| errors.EgainDefaultError    | 4XX, 5XX                    | \*/\*                       |

## cancel_import

# Cancel Import or Validation Job

## Overview
This API allows users to cancel import or validation operations that are currently in progress or scheduled for future execution. Cancellation is immediate for scheduled jobs and graceful for running jobs.

## Cancellation Behavior
- **Scheduled Jobs**: Immediate cancellation, no processing occurs
- **In Progress Jobs**: Graceful shutdown, current item completes, no new items start
- **Completed Jobs**: Cannot be cancelled (returns error)
- **Failed Jobs**: Cannot be cancelled (already stopped)

## When to Cancel
- **Content Issues**: Discover problems with source content
- **Timing Changes**: Need to reschedule for different time
- **Resource Constraints**: System resources are needed elsewhere
- **User Request**: Manual cancellation by authorized users
- **System Maintenance**: Planned maintenance windows

## Cancellation Process
1. **Request Received**: System receives cancellation request
2. **Status Check**: Verifies current job status
3. **Graceful Shutdown**: For running jobs, completes current item
4. **Resource Cleanup**: Releases allocated system resources
5. **Status Update**: Marks job as cancelled
6. **Notification**: Updates job status and logs

## Post-Cancellation
- **Job Status**: Changes to "Cancelled"
- **Partial Results**: Any completed items remain in system
- **Logs**: Cancellation reason and timing recorded
- **Resources**: System resources freed for other operations

## Best Practices
- **Monitor Jobs**: Regularly check job status to identify candidates for cancellation
- **Plan Cancellations**: Schedule cancellations during low-usage periods
- **Resource Planning**: Consider resource impact before cancelling large jobs


### Example Usage

<!-- UsageSnippet language="python" operationID="cancelImport" method="post" path="/import/content/{job_id}/cancel" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.content.import_.cancel_import(job_id="7A84B875-6F75-4C7B-B137-0632B62DB0BD")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                      | Type                                                                                                                                                                                                                                                                                                                           | Required                                                                                                                                                                                                                                                                                                                       | Description                                                                                                                                                                                                                                                                                                                    | Example                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `job_id`                                                                                                                                                                                                                                                                                                                       | *str*                                                                                                                                                                                                                                                                                                                          | :heavy_check_mark:                                                                                                                                                                                                                                                                                                             | **Job ID Parameter**<br/><br/>The unique identifier for the import or validation job. This ID was returned when the job was created via the Import or Validate API.<br/><br/>**Format:** UUID v4 (e.g., 7A84B875-6F75-4C7B-B137-0632B62DB0BD)<br/><br/>**Example Usage:**<br/>```bash<br/>GET /import/content/7A84B875-6F75-4C7B-B137-0632B62DB0BD/status<br/>```<br/> | 7A84B875-6F75-4C7B-B137-0632B62DB0BD                                                                                                                                                                                                                                                                                           |
| `retries`                                                                                                                                                                                                                                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                             | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                |
| `server_url`                                                                                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                             | An optional server URL to use.                                                                                                                                                                                                                                                                                                 | http://localhost:8080                                                                                                                                                                                                                                                                                                          |

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.WSErrorCommon        | 401, 403, 404               | application/json            |
| errors.SchemasWSErrorCommon | 406                         | application/json            |
| errors.WSErrorCommon        | 500                         | application/json            |
| errors.EgainDefaultError    | 4XX, 5XX                    | \*/\*                       |