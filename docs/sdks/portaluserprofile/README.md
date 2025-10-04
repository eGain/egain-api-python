# PortalUserprofile
(*portal.userprofile*)

## Overview

### Available Operations

* [get_all_user_profiles](#get_all_user_profiles) - Get All User Profiles Assigned to User
* [select_user_profile](#select_user_profile) - Select User Profile

## get_all_user_profiles

## Overview
  The Get All User Profiles Assigned to User API retrieves all user profiles in the portal that are assigned to the user, displayed in ascending order of name.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllUserProfiles" method="get" path="/portals/{portalID}/userprofiles" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.userprofile.get_all_user_profiles(accept_language="en-US", portal_id="PROD-1000", language="en-US")

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

**[models.UserProfiles](../../models/userprofiles.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## select_user_profile

## Overview
  The Select User Profile API allows a user to set the user profile for a portal.


### Example Usage

<!-- UsageSnippet language="python" operationID="selectUserProfile" method="put" path="/portals/{portalID}/userprofiles/{userProfileID}/select" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.userprofile.select_user_profile(accept_language="en-US", portal_id="PROD-1000", user_profile_id="PROD-3210")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `user_profile_id`                                                                                                               | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the user profile. <br/>                                                                                               | PROD-3210                                                                                                                       |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |