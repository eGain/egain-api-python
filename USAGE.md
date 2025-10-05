<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.aiservices.retrieve.retrieve_chunks(q="fair lending", portal_id="PROD-1000", dollar_filter_user_profile_id="PROD-3210", language="en-US", dollar_filter_tags={
        "PROD-1234": [
            "PROD-2000",
            "PROD-2003",
        ],
        "PROD-2005": [
            "PROD-2007",
        ],
    }, channel={
        "name": "Eight Bank Website",
    })

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from egain_api_python import Egain
import os

async def main():

    async with Egain(
        access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
    ) as egain:

        res = await egain.aiservices.retrieve.retrieve_chunks_async(q="fair lending", portal_id="PROD-1000", dollar_filter_user_profile_id="PROD-3210", language="en-US", dollar_filter_tags={
            "PROD-1234": [
                "PROD-2000",
                "PROD-2003",
            ],
            "PROD-2005": [
                "PROD-2007",
            ],
        }, channel={
            "name": "Eight Bank Website",
        })

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->