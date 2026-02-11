# Prompt
(*prompt*)

## Overview

APIs for AssistGPT

### Available Operations

* [get_prompt_templates](#get_prompt_templates) - Get Prompt Templates
* [get_prompt_template_by_id](#get_prompt_template_by_id) - Get Prompt Template By ID

## get_prompt_templates

Retrieve prompt templates filtered by department and language.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPromptTemplates" method="get" path="/prompts/prompttemplates" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.prompt.get_prompt_templates(accept_language="en-US", department="Service", language_code="en-US", name="Generate email", use_for="knowledge")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `department`                                                                                                                    | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | Name of the department. Must be a valid department name.                                                                        | Service                                                                                                                         |
| `language_code`                                                                                                                 | [models.GetPromptTemplatesLanguageCode](../../models/getprompttemplateslanguagecode.md)                                         | :heavy_check_mark:                                                                                                              | The language used while writing the prompt templates.                                                                           | en-US                                                                                                                           |
| `name`                                                                                                                          | *Optional[str]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | Fetch only templates with this exact name.                                                                                      | Generate email                                                                                                                  |
| `use_for`                                                                                                                       | [Optional[models.GetPromptTemplatesUseFor]](../../models/getprompttemplatesusefor.md)                                           | :heavy_minus_sign:                                                                                                              | Filter prompt templates based on console.                                                                                       | knowledge                                                                                                                       |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |
| `server_url`                                                                                                                    | *Optional[str]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | An optional server URL to use.                                                                                                  | http://localhost:8080                                                                                                           |

### Response

**[models.GetPromptTemplatesResponse](../../models/getprompttemplatesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_prompt_template_by_id

Retrieve a prompt template filtered by department and language.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPromptTemplateById" method="get" path="/prompts/prompttemplates/{promptID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.prompt.get_prompt_template_by_id(accept_language="en-US", department="Service", language_code="en-US", prompt_id="PROD-4582")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `department`                                                                                                                    | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | Name of the department. Must be a valid department name.                                                                        | Service                                                                                                                         |
| `language_code`                                                                                                                 | [models.GetPromptTemplateByIDLanguageCode](../../models/getprompttemplatebyidlanguagecode.md)                                   | :heavy_check_mark:                                                                                                              | The language used while writing the prompt templates.                                                                           | en-US                                                                                                                           |
| `prompt_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The promptID of the prompt template you want to fetch details for.                                                              | PROD-4582                                                                                                                       |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |
| `server_url`                                                                                                                    | *Optional[str]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | An optional server URL to use.                                                                                                  | http://localhost:8080                                                                                                           |

### Response

**[models.PromptTemplate](../../models/prompttemplate.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |