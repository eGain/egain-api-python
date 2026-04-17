# AiservicesPrompt
(*aiservices.prompt*)

## Overview

### Available Operations

* [execute_prompt](#execute_prompt) - Execute a predefined prompt

## execute_prompt

Execute a published and active prompt template from the AI console.

### Example Usage

<!-- UsageSnippet language="python" operationID="executePrompt" method="post" path="/prompt/{promptId}/execute" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.aiservices.prompt.execute_prompt(prompt_id="<id>", department="Service", language_code="en-US", event_type="generate", client_session_id="123e4567-e89b-12d3-a456-426614174000", streaming=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `prompt_id`                                                                                      | *str*                                                                                            | :heavy_check_mark:                                                                               | ID of the prompt template from the AI console. Only published and active prompt IDs are allowed. |                                                                                                  |
| `department`                                                                                     | *str*                                                                                            | :heavy_check_mark:                                                                               | Name of the department. Must be a valid department name.                                         | Service                                                                                          |
| `language_code`                                                                                  | [models.LanguageCodeRequestBody](../../models/languagecoderequestbody.md)                        | :heavy_check_mark:                                                                               | The language used for the prompt template.                                                       | en-US                                                                                            |
| `replacements`                                                                                   | List[[models.Replacement](../../models/replacement.md)]                                          | :heavy_minus_sign:                                                                               | List of variable replacements (either static or search).                                         |                                                                                                  |
| `event_type`                                                                                     | [Optional[models.EventTypeRequestBody]](../../models/eventtyperequestbody.md)                    | :heavy_minus_sign:                                                                               | Event type logged when the API executes successfully.                                            | generate                                                                                         |
| `client_session_id`                                                                              | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | Client provided sessionID to store events against.                                               | 123e4567-e89b-12d3-a456-426614174000                                                             |
| `streaming`                                                                                      | *Optional[bool]*                                                                                 | :heavy_minus_sign:                                                                               | Whether to stream the response instead of returning inline.                                      | false                                                                                            |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |
| `server_url`                                                                                     | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | An optional server URL to use.                                                                   | http://localhost:8080                                                                            |

### Response

**[models.ExecutePromptResponse](../../models/executepromptresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.BadRequestError   | 400                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |