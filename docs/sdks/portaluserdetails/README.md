# PortalUserdetails
(*portal.userdetails*)

## Overview

### Available Operations

* [get_user_details](#get_user_details) - Get User Details

## get_user_details

## Overview
  The Get User Details API retrieves details of a knowledge user.


### Example Usage

<!-- UsageSnippet language="python" operationID="getUserDetails" method="get" path="/portals/user" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.userdetails.get_user_details(accept_language="en-US")

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

**[models.UserDetails](../../models/userdetails.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 406       | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |