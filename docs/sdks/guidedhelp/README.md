# Guidedhelp
(*portal.guidedhelp*)

## Overview

### Available Operations

* [get_all_casebases_releases](#get_all_casebases_releases) - Get Available Casebases Releases
* [get_casebase_release_by_id](#get_casebase_release_by_id) - Get Details of a Casebase Release
* [get_cluster_by_casebase_release_id](#get_cluster_by_casebase_release_id) - Get Cluster Details of a Casebase Release
* [get_all_profiles_in_portal](#get_all_profiles_in_portal) - Get All Profiles Available in Portal
* [start_gh_search](#start_gh_search) - Start a Guided Help Search
* [step_gh_search](#step_gh_search) - Perform a Step in a Guided Help Search
* [get_all_cases](#get_all_cases) - Get All Cases of a Cluster in Release
* [get_case_by_id](#get_case_by_id) - Get Details of a Case
* [accept_gh_solution](#accept_gh_solution) - Accept Solution
* [reject_gh_solution](#reject_gh_solution) - Reject Solution
* [create_quickpick](#create_quickpick) - Create Quickpick
* [get_all_quick_picks](#get_all_quick_picks) - Get All Quickpicks for a Portal
* [restore_quickpick](#restore_quickpick) - Resume a Quickpick

## get_all_casebases_releases

## Overview
  The Get Available Casebases Releases API retrieves all Casebase Releases associated with a portal.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllCasebasesReleases" method="get" path="/portals/{portalID}/gh/casebasereleases" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_all_casebases_releases(accept_language="en-US", portal_id="PROD-1000", language="en-US", pagenum=1, pagesize=10)

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
| `pagenum`                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                                                                                    |                                                                                                                                                                                                                       |
| `pagesize`                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                                                                                                                |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.CasebaseResult](../../models/casebaseresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_casebase_release_by_id

## Overview
  The Get Details of a Casebase Release API retrieves details of Casebase Release.


### Example Usage

<!-- UsageSnippet language="python" operationID="getCasebaseReleaseById" method="get" path="/portals/{portalID}/gh/casebasereleases/{casebaseReleaseID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_casebase_release_by_id(accept_language="en-US", portal_id="PROD-1000", casebase_release_id="202201000000002", language="en-US", languages=True)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase Release for which details is to be fetched.                                                                                                                                          | 202201000000002                                                                                                                                                                                                       |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `languages`                                                                                                                                                                                                           | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Display langages of Casebase Releases.                                                                                                                                                                                |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.CasebaseResult](../../models/casebaseresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_cluster_by_casebase_release_id

## Overview
  The Get Cluster Details of a Casebase Release API retrieves cluster details of Casebase Release.


### Example Usage

<!-- UsageSnippet language="python" operationID="getClusterByCasebaseReleaseId" method="get" path="/portals/{portalID}/gh/casebasereleases/{casebaseReleaseID}/clusters" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_cluster_by_casebase_release_id(accept_language="en-US", portal_id="PROD-1000", casebase_release_id="202201000000002", language="en-US", pagenum=1, pagesize=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase Release for which details is to be fetched.                                                                                                                                          | 202201000000002                                                                                                                                                                                                       |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `pagenum`                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                                                                                    |                                                                                                                                                                                                                       |
| `pagesize`                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                                                                                                                |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.ClusterResults](../../models/clusterresults.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_all_profiles_in_portal

## Overview
  The Get All Profiles Available in Portal API retrieves all Guided Help profiles associated with a portal.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllProfilesInPortal" method="get" path="/portals/{portalID}/gh/profiles" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_all_profiles_in_portal(accept_language="en-US", portal_id="PROD-1000", filter_casebase_release="202201000000002", pagenum=1, pagesize=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `filter_casebase_release`                                                                                                       | *Optional[str]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | Filter by Casebase Release                                                                                                      | 202201000000002                                                                                                                 |
| `pagenum`                                                                                                                       | *Optional[int]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.              |                                                                                                                                 |
| `pagesize`                                                                                                                      | *Optional[int]*                                                                                                                 | :heavy_minus_sign:                                                                                                              | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                          |                                                                                                                                 |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Response

**[models.ProfileResult](../../models/profileresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## start_gh_search

## Overview
   The Start a Guided Help search can be used to start a search session in the Guided Help. 
   
   A Guided Help profile can also be specified while starting the session and it is used to filter the results of search.
   If this is not passed in the request, the default profile of the portal is used. Questions can also be answered at time of starting the search session. 
   
   A Guided Help search session can be started in following ways:
   * Launch session for a specific Casebase Release.
   * Launch session for a Casebase and specify the release type.
   * Use a Guided Help session Article and pass the required session parameters.

## Prerequisites
   * A Guided Help profile must be assigned to the user.
   * Casebase Release passed in the request must be associated with the portal passed in URI. 
   


### Example Usage

<!-- UsageSnippet language="python" operationID="startGHSearch" method="post" path="/portals/{portalID}/gh/search" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.start_gh_search(accept_language="en-US", portal_id="PROD-1000", casebase_id="202201000000002", language="en-US", gh_custom_additional_attributes="question.custom.score", questions=[
        {
            "id": "1000003852",
            "answers": [
                {
                    "id": "1000000004",
                },
            ],
        },
    ], ghs_article_id="100000000001035")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_id`                                                                                                                                                                                                         | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase.                                                                                                                                                                                     | 409601000000001                                                                                                                                                                                                       |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `gh_custom_additional_attributes`                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                   |                                                                                                                                                                                                                       |
| `questions`                                                                                                                                                                                                           | List[[models.StartQuestionAndAnswer](../../models/startquestionandanswer.md)]                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                    | Pre-answered Questions in Guided Help search                                                                                                                                                                          |                                                                                                                                                                                                                       |
| `profile_id`                                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | The ID of the guided help profile.<br><br/>1 will always be the **system profile**.<br/>                                                                                                                              |                                                                                                                                                                                                                       |
| `session_variable`                                                                                                                                                                                                    | List[[models.SessionContextVariable](../../models/sessioncontextvariable.md)]                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                    | Session variables used to give Guided Help additional context.                                                                                                                                                        |                                                                                                                                                                                                                       |
| `start_over`                                                                                                                                                                                                          | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Restart the current Guided Help search with the existing context along with session variable context.                                                                                                                 |                                                                                                                                                                                                                       |
| `use_live_release`                                                                                                                                                                                                    | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Use current live release snapshot of the Casebase otherwise use the authoring release.                                                                                                                                |                                                                                                                                                                                                                       |
| `ghs_article_id`                                                                                                                                                                                                      | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Numeric ID of the guided help session article used for starting search.                                                                                                                                               | 100000000001035                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.StartGHSearchResponse](../../models/startghsearchresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 429                      | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## step_gh_search

## Overview
   The Perform a Step in a Guided Help Search API can be used to answer one or more questions (perform a step) in Guided Help search.

## Prerequisites
   * A Guided Help session must be in progress before this API is invoked.


### Example Usage

<!-- UsageSnippet language="python" operationID="stepGHSearch" method="put" path="/portals/{portalID}/gh/search" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.step_gh_search(accept_language="en-US", portal_id="PROD-1000", casebase_id="202201000000002", questions=[
        {
            "id": "1000000322",
            "answers": [
                {
                    "id": "1000000303",
                },
            ],
        },
        {
            "id": "1000000327",
            "answers": [
                {
                    "id": "1000000842",
                },
            ],
        },
        {
            "id": "1000001006",
            "answers": [
                {
                    "id": "1000001001",
                },
            ],
        },
    ], language="en-US", gh_custom_additional_attributes="question.custom.score", use_live_release=True, ghs_article_id="100000000001035")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_id`                                                                                                                                                                                                         | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase.                                                                                                                                                                                     | 409601000000001                                                                                                                                                                                                       |
| `questions`                                                                                                                                                                                                           | List[[models.QuestionAndAnswer](../../models/questionandanswer.md)]                                                                                                                                                   | :heavy_check_mark:                                                                                                                                                                                                    | Pre-answered Questions in Guided Help search                                                                                                                                                                          |                                                                                                                                                                                                                       |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `gh_custom_additional_attributes`                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                   |                                                                                                                                                                                                                       |
| `profile_id`                                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | The ID of the guided help profile.<br><br/>1 will always be the **system profile**.<br/>                                                                                                                              |                                                                                                                                                                                                                       |
| `session_variable`                                                                                                                                                                                                    | List[[models.SessionContextVariable](../../models/sessioncontextvariable.md)]                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                    | Session variables used to give Guided Help additional context.                                                                                                                                                        |                                                                                                                                                                                                                       |
| `start_over`                                                                                                                                                                                                          | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Restart the current Guided Help search with the existing context along with session variable context.                                                                                                                 |                                                                                                                                                                                                                       |
| `use_live_release`                                                                                                                                                                                                    | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Use current live release snapshot of the Casebase otherwise use the authoring release.                                                                                                                                |                                                                                                                                                                                                                       |
| `ghs_article_id`                                                                                                                                                                                                      | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Numeric ID of the guided help session article used for starting search.                                                                                                                                               | 100000000001035                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.GHSearchResult](../../models/ghsearchresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_all_cases

## Overview
  The Get All Cases of a Cluster in Release API retrieves all cases in cluster of a Casebase Release. A Case is a group of Questions, Articles, and control actions that work together to guide users through a series of questions and scenarios in a Guided Help session.  

## Prerequisites
  A Guided Help search session for the provided Casebase Release must be in progress before this API is invoked.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllCases" method="get" path="/portals/{portalID}/gh/casebasereleases/{casebaseReleaseID}/clusters/{clusterID}/cases" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_all_cases(accept_language="en-US", portal_id="PROD-1000", casebase_release_id="202201000000002", cluster_id="1000000402", language="en-US", pagenum=1, pagesize=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase Release for which details is to be fetched.                                                                                                                                          | 202201000000002                                                                                                                                                                                                       |
| `cluster_id`                                                                                                                                                                                                          | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | ID of Cluster.                                                                                                                                                                                                        | 1000000402                                                                                                                                                                                                            |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `pagenum`                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                                                                                    |                                                                                                                                                                                                                       |
| `pagesize`                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                                                                                                                |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.CaseListResults](../../models/caselistresults.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_case_by_id

## Overview
  The Get Details of a Case API retrieves details of a case in a release.

## Prerequisites
  * A Guided Help search session for the provided Casebase Release must be in progress before this API is invoked.


### Example Usage

<!-- UsageSnippet language="python" operationID="getCaseById" method="get" path="/portals/{portalID}/gh/casebasereleases/{casebaseReleaseID}/cases/{caseID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_case_by_id(accept_language="en-US", portal_id="PROD-1000", casebase_release_id="202201000000002", case_id="1000001085", language="en-US", case_additional_attributes=[
        "actions",
    ])

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase Release for which details is to be fetched.                                                                                                                                          | 202201000000002                                                                                                                                                                                                       |
| `case_id`                                                                                                                                                                                                             | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Case for which details is to be fetched.                                                                                                                                                      | 1000001085                                                                                                                                                                                                            |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `case_additional_attributes`                                                                                                                                                                                          | List[[models.CaseAdditionalAttributes](../../models/caseadditionalattributes.md)]                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | Additional case attributes to be fetched.                                                                                                                                                                             |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.Case](../../models/case.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## accept_gh_solution

## Overview
  The Accept Solution API can be used to accept and add positive score to a solution of a Guided Help case.

## Prerequisites
   * A Guided Help search session must be started before invoking this API.


### Example Usage

<!-- UsageSnippet language="python" operationID="acceptGHSolution" method="post" path="/portals/{portalID}/gh/cases/{caseID}/accept" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.guidedhelp.accept_gh_solution(accept_language="en-US", portal_id="PROD-1000", case_id="1000001085", id="120000001201010", name="HPE Solution Article", profile_id="120450120000001")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `case_id`                                                                                                                       | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The numerical ID of the Case for which details is to be fetched.                                                                | 1000001085                                                                                                                      |
| `id`                                                                                                                            | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The numerical ID of the Casebase Release.                                                                                       | 409601000000001                                                                                                                 |
| `name`                                                                                                                          | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | name of the case or article                                                                                                     |                                                                                                                                 |
| `profile_id`                                                                                                                    | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the guided help profile.<br><br/>1 will always be the **system profile**.<br/>                                        |                                                                                                                                 |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## reject_gh_solution

## Overview
  The Reject Solution API can be used to reject and add negative score to a solution of a Guided Help case.

## Prerequisites
   * A Guided Help search session must be started before invoking this API.


### Example Usage

<!-- UsageSnippet language="python" operationID="rejectGHSolution" method="post" path="/portals/{portalID}/gh/cases/{caseID}/reject" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.guidedhelp.reject_gh_solution(accept_language="en-US", portal_id="PROD-1000", case_id="1000001085", id="123101210000102", name="HPE Solution Article", profile_id="100101210000002")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     | Example                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                               | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                         | :heavy_check_mark:                                                                                                              | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses). | en-US                                                                                                                           |
| `portal_id`                                                                                                                     | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits. | PROD-1000                                                                                                                       |
| `case_id`                                                                                                                       | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The numerical ID of the Case for which details is to be fetched.                                                                | 1000001085                                                                                                                      |
| `id`                                                                                                                            | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The numerical ID of the Casebase Release.                                                                                       | 409601000000001                                                                                                                 |
| `name`                                                                                                                          | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | name of the case or article                                                                                                     |                                                                                                                                 |
| `profile_id`                                                                                                                    | *str*                                                                                                                           | :heavy_check_mark:                                                                                                              | The ID of the guided help profile.<br><br/>1 will always be the **system profile**.<br/>                                        |                                                                                                                                 |
| `retries`                                                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                | :heavy_minus_sign:                                                                                                              | Configuration to override the default retry behavior of the client.                                                             |                                                                                                                                 |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## create_quickpick

## Overview
   The Create Quickpick API can be used to create a new quickpick(bookmark) for current Guided Help search session.

  Note: If "linkToActivity" attribute is passed as true in request body then one of below must be passed in header
   * <code>XEgainTenantId</code>
   * <code>xEgainActivityId</code>
   * <code>XInteractionId</code>

## Prerequisites
   * A Guided Help search session must be in progress before this API is invoked.
   * QuickPick can only be created for a live release of a Casebase.
   


### Example Usage

<!-- UsageSnippet language="python" operationID="createQuickpick" method="post" path="/portals/{portalID}/gh/quickpicks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    egain.portal.guidedhelp.create_quickpick(accept_language="en-US", portal_id="PROD-1000", casebase_release_id="102312010000000", language="en-US", name="QuickPick82700245", comment="demo quickpick", link_to_activity=False)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of Live release of the Casebase.                                                                                                                                                                     | 409601000000001                                                                                                                                                                                                       |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `name`                                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | name of the quick pick                                                                                                                                                                                                |                                                                                                                                                                                                                       |
| `comment`                                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | comment about quick pick                                                                                                                                                                                              |                                                                                                                                                                                                                       |
| `link_to_activity`                                                                                                                                                                                                    | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | indicates if quickpick is to be linked with activity                                                                                                                                                                  |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## get_all_quick_picks

## Overview
  The Get All Quickpicks for a Portal API retrieves details of quickpicks created for the Casebase.

## Conditions
   If "getLastSavedQuickPickForInteraction" query parameter is passed as "Yes" then one of below must be passed in request header.
   * X-ext-integration-id
   * X-egain-activity-id
   * X-ext-interaction-id
  Either casebaseID or getLastSavedQuickPickForInteraction must be passed in request.


### Example Usage

<!-- UsageSnippet language="python" operationID="getAllQuickPicks" method="get" path="/portals/{portalID}/gh/quickpicks" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.get_all_quick_picks(accept_language="en-US", casebase_release_id="202201000000002", portal_id="PROD-1000", language="en-US", pagenum=1, pagesize=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `casebase_release_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The numerical ID of the Casebase Release for which details is to be fetched.                                                                                                                                          | 202201000000002                                                                                                                                                                                                       |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `pagenum`                                                                                                                                                                                                             | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the page number of results to be returned. Used in conjunction with $pagesize.                                                                                                    |                                                                                                                                                                                                                       |
| `pagesize`                                                                                                                                                                                                            | *Optional[int]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | Pagination parameter that specifies the number of results per page. Used in conjunction with $pagenum.                                                                                                                |                                                                                                                                                                                                                       |
| `get_last_saved_quick_pick_for_interaction`                                                                                                                                                                           | *Optional[bool]*                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | To be passed retrieve quickpick associated with interaction.                                                                                                                                                          |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.QuickpickResults](../../models/quickpickresults.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |

## restore_quickpick

## Overview
  The Resume a Quickpick API can be used to restore (resume) a specific quickpick.

## Prerequisites
   * A Guided Help session for the Casebase must be started before invoking this API.


### Example Usage

<!-- UsageSnippet language="python" operationID="restoreQuickpick" method="post" path="/portals/{portalID}/gh/quickpicks/{quickpickID}" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.portal.guidedhelp.restore_quickpick(accept_language="en-US", portal_id="PROD-1000", quickpick_id="11", language="en-US", gh_custom_additional_attributes="question.custom.score")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                             | Type                                                                                                                                                                                                                  | Required                                                                                                                                                                                                              | Description                                                                                                                                                                                                           | Example                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `accept_language`                                                                                                                                                                                                     | [models.AcceptLanguage](../../models/acceptlanguage.md)                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                    | The Language locale accepted by the client (used for locale specific fields in resource representation and in error responses).                                                                                       | en-US                                                                                                                                                                                                                 |
| `portal_id`                                                                                                                                                                                                           | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the portal being accessed.<br><br>A portal ID is composed of a 2-4 letter prefix, followed by a dash and 4-15 digits.                                                                                       | PROD-1000                                                                                                                                                                                                             |
| `quickpick_id`                                                                                                                                                                                                        | *str*                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                    | The ID of the quickpick.                                                                                                                                                                                              | 11                                                                                                                                                                                                                    |
| `language`                                                                                                                                                                                                            | [Optional[models.LanguageQueryParameter]](../../models/languagequeryparameter.md)                                                                                                                                     | :heavy_minus_sign:                                                                                                                                                                                                    | The language that describes the details of a resource. Resources available in different languages may differ from each other.<li>If <code>lang</code> is not passed, then the portal's default language is used.</li> | en-US                                                                                                                                                                                                                 |
| `gh_custom_additional_attributes`                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                    | N/A                                                                                                                                                                                                                   |                                                                                                                                                                                                                       |
| `retries`                                                                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                                                                   |                                                                                                                                                                                                                       |

### Response

**[models.GHSearchResult](../../models/ghsearchresult.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.WSErrorCommon     | 400, 401, 403, 404, 406  | application/json         |
| errors.WSErrorCommon     | 500                      | application/json         |
| errors.EgainDefaultError | 4XX, 5XX                 | \*/\*                    |