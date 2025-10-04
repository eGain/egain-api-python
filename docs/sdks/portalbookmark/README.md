# PortalBookmark
(*portal.bookmark*)

## Overview

### Available Operations

* [addbookmark](#addbookmark) - Add a Bookmark
* [getbookmark](#getbookmark) - Get All Bookmarks for a Portal
* [deletebookmark](#deletebookmark) - Delete a Bookmark

## addbookmark

## Overview
  * The Add a Bookmark API adds a bookmark from a portal.


### Example Usage

<!-- UsageSnippet language="python" operationID="addbookmark" method="post" path="/portals/{portalID}/bookmarks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.bookmark.addbookmark(portal_id="PROD-1000", accept_language="en-US", resource_id="PROD-9274782", user_id="1000001035", bookmark_name="DemoBookmark", resource_type=2)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                  | Type                                                                                                                                                                                                                                                                       | Required                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                                                                                                                | Example                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `portal_id`                                                                                                                                                                                                                                                                | *str*                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                         | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                                                                            | PROD-1000                                                                                                                                                                                                                                                                  |
| `accept_language`                                                                                                                                                                                                                                                          | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                                         | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                                                                            | en-US                                                                                                                                                                                                                                                                      |
| `resource_id`                                                                                                                                                                                                                                                              | *Optional[str]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The ID of the article or topic associated with this bookmark. A case ID or an article ID is composed of a 2-4 letter prefix, followed by a dash and 15 digits.<br><br>This attribute must be provided if <code>resourceType</code> is set to "1 - Article" or "2 - Topic". | DEV-7692                                                                                                                                                                                                                                                                   |
| `user_id`                                                                                                                                                                                                                                                                  | *Optional[str]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The ID of the user associated with the bookmark.                                                                                                                                                                                                                           | 1000001035                                                                                                                                                                                                                                                                 |
| `user_type`                                                                                                                                                                                                                                                                | [Optional[models.UserType]](../../models/usertype.md)                                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The type of the user associated with the bookmark.                                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                            |
| `bookmark_name`                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The name of the bookmark.                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                                            |
| `resource_type`                                                                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | Determines the type of resource:<br/><li>1 - Article</li><br/><li>2 - Topic</li><br/><li>3 - External Content</li>                                                                                                                                                         |                                                                                                                                                                                                                                                                            |
| `resource_name`                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The name of the resource associated with the bookmark.<br><br>This attribute is only available for article and topic bookmarks.                                                                                                                                            |                                                                                                                                                                                                                                                                            |
| `external_content_id`                                                                                                                                                                                                                                                      | *Optional[str]*                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                         | The ID of the external content.<br><br>This attribute must be provided if <code>resourceType</code> is set to "3 - External Content".                                                                                                                                      |                                                                                                                                                                                                                                                                            |
| `retries`                                                                                                                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                            |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## getbookmark

## Overview
  The Get All Bookmarks for a Portal API returns all bookmarks for a portal. Only the topic bookmarks that are available in the scope of the portal are returned.

## Permissions
  * The user must have the __View Author Portal__ action to access the authoring view.
  * The user must have the __View Staging Portal__ action to access the staging view.


### Example Usage

<!-- UsageSnippet language="python" operationID="getbookmark" method="get" path="/portals/{portalID}/bookmarks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.bookmark.getbookmark(accept_language="en-US", portal_id="PROD-1000")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Response

**[models.BookmarkResult](../../models/bookmarkresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## deletebookmark

## Overview
  The Delete a Bookmark API deletes a bookmark from a portal.


### Example Usage

<!-- UsageSnippet language="python" operationID="deletebookmark" method="delete" path="/portals/{portalID}/bookmarks/{bookmarkID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.bookmark.deletebookmark(accept_language="en-US", portal_id="PROD-1000", bookmark_id="4759")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `bookmark_id`                                                                                                                   | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the bookmark.                                                                                                         | 4759                                                                                                                            |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |