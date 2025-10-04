# General
(*portal.general*)

## Overview

### Available Operations

* [get_all_portals](#get_all_portals) - Get All Portals
* [get_my_portals](#get_my_portals) - Get All Portals Accessible To User
* [get_portal_details_by_id](#get_portal_details_by_id) - Get Portal Details By ID
* [get_tag_categories_for_interest_for_portal](#get_tag_categories_for_interest_for_portal) - Get Tag Categories for Interest for a Portal

## get_all_portals

## Overview
  The Get All Portals API returns all portals in a partition or department.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllPortals" method="get" path="/portals" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.general.get_all_portals(accept_language="en-US", department_id="999", language="en-US", pagenum=1, pagesize=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `department_id`                                                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | The ID of the department.                                                                                                                                                                                             | 999                                                                                                                                                                                                                   |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `pagenum`                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                                                                                    |                                                                                                                                                                                                                       |
| `pagesize`                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                                                                                                                |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.PortalResult](../../models/portalresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_my_portals

## Overview
  The Get All Portals Accessible to User API allows a user to fetch all portals accessible to user across all department.
  * If no access tags are specified for a portal, then any user can access the portal.
  * If access tags are specified for a portal, users with a user profile that allows access have access to the portal. For users with multiple user profiles, the user profile that allows access does not need to be the active user profile.
  * All the global users(partition) cannot be assigned user profiles; their access is limited to portals without access restrictions.
  * The only articles returned are associated to an Article type when the parameter, “Include in browse on portals” is set to "Yes".
  * When the "shortUrlTemplate" query parameter is provided, the API filters accessible portals according to the specified language and template name. Portal Short URL specific to to the "shortUrlTemplate" query parameter value is returned in the response.
  * When there is no short URL available for a specific language, the API returns a portal object with an empty "shortURL" field.


### Example Usage

<!-- UsageSnippet language="python" operationID="getMyPortals" method="get" path="/myportals" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.general.get_my_portals(accept_language="en-US", language="en-US", department="service", filter_text="master", short_url_template="silver", pagenum=1, pagesize=25)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                            | Type                                                                                                                                                 | Required                                                                                                                                             | Description                                                                                                                                          | Example                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                    | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                              | :heavy_check_mark:                                                                                                                                   | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                      | en-US                                                                                                                                                |
| `language`                                                                                                                                           | [models.MandatoryLanguageQueryParameter](../../models/mandatorylanguagequeryparameter.md)                                                            | :heavy_check_mark:                                                                                                                                   | The language used for fetching the details of a resource. Resources available in different languages may differ from each other.                     | en-US                                                                                                                                                |
| `department`                                                                                                                                         | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | The Name of the department for which portals are to be fetched                                                                                       | service                                                                                                                                              |
| `filter_text`                                                                                                                                        | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Portal name starting with a specific character are considered to filter the result.                                                                  | master                                                                                                                                               |
| `short_url_template`                                                                                                                                 | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | The Name of the template used while creating Short URL.                                                                                              | silver                                                                                                                                               |
| `sort`                                                                                                                                               | [Optional[models.SortIDNameDepartment]](../../models/sortidnamedepartment.md)                                                                        | :heavy_minus_sign:                                                                                                                                   | Objects returned in server response are sorted based on the attribute supplied under $sort. <br>_Default value_: name.                               |                                                                                                                                                      |
| `order`                                                                                                                                              | [Optional[models.Order]](../../models/order.md)                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Common query parameter $order.                                                                                                                       |                                                                                                                                                      |
| `pagenum`                                                                                                                                            | *Optional[int]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                   |                                                                                                                                                      |
| `pagesize`                                                                                                                                           | *Optional[int]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.<br>Valid range of 5-75<br>_Default value_: 25 |                                                                                                                                                      |
| `retries`                                                                                                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                     | :heavy_minus_sign:                                                                                                                                   | Configuration to override the default retry behavior of the client.                                                                                  |                                                                                                                                                      |

### Response

**[models.AllAccessiblePortals](../../models/allaccessibleportals.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_portal_details_by_id

## Overview
  The Get Portal Details By ID API allows a user to fetch details of a portal by the ID.


### Example Usage

<!-- UsageSnippet language="python" operationID="getPortalDetailsById" method="get" path="/portals/{portalID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.general.get_portal_details_by_id(accept_language="en-US", portal_id="PROD-1000", language="en-US")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.Portal](../../models/portal.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_tag_categories_for_interest_for_portal

## Overview
  The Get Tag Categories for Interest for a Portal API retrieves the Tag Categories for Interest configured for a portal.
  * Tag Categories are ordered in order of their addition in the "Tag Categories for Interest" in the Portal configuration.
  * Tags are ordered as per their order defined in their Tag Category.
  * Tag Groups are sorted by their name, in ascending order.


### Example Usage

<!-- UsageSnippet language="python" operationID="getTagCategoriesForInterestForPortal" method="get" path="/portals/{portalID}/tagcategoriesforinterest" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.general.get_tag_categories_for_interest_for_portal(accept_language="en-US", portal_id="PROD-1000", language="en-US")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      | Example                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                          | :heavy_check_mark:                                                                                                               | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).  | en-US                                                                                                                            |
| `portal_id`                                                                                                                      | *str*                                                                                                                            | :heavy_check_mark:                                                                                                               | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.  | PROD-1000                                                                                                                        |
| `language`                                                                                                                       | [models.MandatoryLanguageQueryParameter](../../models/mandatorylanguagequeryparameter.md)                                        | :heavy_check_mark:                                                                                                               | The language used for fetching the details of a resource. Resources available in different languages may differ from each other. | en-US                                                                                                                            |
| `retries`                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                 | :heavy_minus_sign:                                                                                                               | Configuration to override the default retry behavior of the client.                                                              |                                                                                                                                  |

### Response

**[models.TagCategoriesForInterest](../../models/tagcategoriesforinterest.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |