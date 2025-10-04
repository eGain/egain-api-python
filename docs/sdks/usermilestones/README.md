# Usermilestones
(*portal.usermilestones*)

## Overview

### Available Operations

* [get_user_milestones](#get_user_milestones) - Get User Milestones

## get_user_milestones

## Overview
The User Milestones API provides information about the milestones of an agent within the article workflow. 
This API helps track the progress of articles by grouping them into relevant milestones based on their current stage.

For example, an article might go through Knowledge Workflow Stages like Draft, Initial Review, Staging, Final Review and Publish. 
       Articles in the Draft and Initial Review stages are part of the "authoring milestone", while articles in the Staging and Final Review stages are part of the "staging milestone".


### Example Usage

<!-- UsageSnippet language="python" operationID="getUserMilestones" method="get" path="/portals/user/milestones" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.usermilestones.get_user_milestones(accept_language="en-US")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Response

**[models.Milestones](../../models/milestones.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 406       | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |