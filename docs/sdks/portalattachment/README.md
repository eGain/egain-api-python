# PortalAttachment
(*portal.attachment*)

## Overview

### Available Operations

* [create_signed_url](#create_signed_url) - Generate Signed URL to Upload API

## create_signed_url

## Overview
   The Generate Signed URL to Upload API produces a signature that is used to upload an attachment. 


### Example Usage

<!-- UsageSnippet language="python" operationID="createSignedURL" method="post" path="/attachment/preupload" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.attachment.create_signed_url(accept_language="en-US", name="article.png", size=11889)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `name`                                                                                                                          | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The name of the attachment.                                                                                                     |                                                                                                                                 |
| `size`                                                                                                                          | *int*                                                                                                                           | :heavy_check_mark:                                                                                                              | The size of the attachment in bytes. The maximum size is limited to 25MB.                                                       |                                                                                                                                 |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Response

**[models.Attachment](../../models/attachment.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |