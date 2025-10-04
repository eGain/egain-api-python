# Health
(*content.health*)

## Overview

### Available Operations

* [get_health](#get_health) - Check service health status

## get_health

# Service Health Check

## Overview
This API provides comprehensive health status information for the Import Content service. It's designed for infrastructure monitoring, load balancer health checks, and operational monitoring to ensure service availability and performance.

## Health Check Features
- **Service Status**: Overall service health (healthy/unhealthy)
- **Version Information**: Current API version and build details

## Monitoring Use Cases
- **Load Balancers**: Automatic health checks for traffic routing
- **Alerting Systems**: Automated notifications for service issues

## Health Status Values
- **Healthy**: Service is operating normally
- **Unhealthy**: Service is experiencing critical issues
- **Maintenance**: Service is under planned maintenance

## Response Components
- **Status**: Current health state
- **Timestamp**: When health check was performed
- **Version**: API version information
- **Uptime**: Service uptime since last restart

## Monitoring Best Practices
- **Check Frequency**: Monitor every 1-2 minutes for production
- **Response Time**: Track health check response times

## Permissions
| Actor | Permission |
| ------- | --------|
| System |<ul><li>No authentication required for basic health checks.</li><li>This endpoint is designed for infrastructure monitoring.</li><li>Rate limiting applies to prevent abuse.</li></ul>|


### Example Usage

<!-- UsageSnippet language="python" operationID="getHealth" method="get" path="/import/content/health" -->
```python
from egain_api_python import Egain
import os


with Egain(
    access_token=os.getenv("EGAIN_ACCESS_TOKEN", ""),
) as egain:

    res = egain.content.health.get_health()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |
| `server_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | An optional server URL to use.                                      |

### Response

**[models.GetHealthResponse](../../models/gethealthresponse.md)**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ServiceUnavailableError | 503                            | application/json               |
| errors.EgainDefaultError       | 4XX, 5XX                       | \*/\*                          |