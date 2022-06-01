## Metrics

The metrics API can be queried to obtain metrics data that is pushed by the service to CloudMC metric data store.

### Retrieve Metrics for a Specified Interval

<!-- GET METRICS FOR INTERVAL -->

`GET /metrics/{serviceCode}/{metricId}`

Retrieves metrics for a given metric id in a specified interval

```shell
# Retrieve metrics for a given interval
curl "https://portal.coxedge.com/api/v2/metrics/stackpath-cox-dev/ingress_bandwidth?startDate=2021-08-12T10:50:46.386Z&endDate=2021-08-15T10:50:46.386Z&size=12&unit=hours&entityId=1923471a-6a72-474d-9e19-63075bc1020b" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "ingress_bandwidth": [
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-12T12:00:00.000",
        "value": 0.27
      },
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-13T00:00:00.000",
        "value": 0.29
      },
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-13T12:00:00.000",
        "value": 0.25
      },
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-14T00:00:00.000",
        "value": 0.37
      },
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-14T12:00:00.000",
        "value": 0.26
      },
      {
        "entityId": "1923471a-6a72-474d-9e19-63075bc1020b",
        "label": "2021-08-15T00:00:00.000",
        "value": 0.21
      }
    ]
  }
}
```

| Path Parameters            | &nbsp;                                                           |
| -------------------------- | ---------------------------------------------------------------- |
| `serviceCode`<br/>_string_ | A globally unique code that identifies this service connection.. |
| `metricId`<br/>_string_    | A unique identifier used to define a `MetricDescriptor`.         |

| Required Query Parameters | &nbsp;                                                                                                                                                    |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `startDate`<br/>_Date_    | The start date of the interval to query metrics for. The date must be in a valid ISO-8601 format. The start date must be provided to query this endpoint. |
| `endDate`<br/>_Date_      | The start date of the interval to query metrics for. The date must be in a valid ISO-8601 format. The end date must be provided to query this endpoint.   |

| Optional Query Parameters      | &nbsp;                                                                                                                                                                                                                       |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `environment`<br/>_string_     | The name of the environment to query metrics for.                                                                                                                                                                            |
| `aggregationType`<br/>_string_ | How the queried metrics should be aggregated. The possible values are sum, count, min, max, avg (average). When not provided, the default value used is `average`.                                                           |
| `size`<br/>_integer_           | The size of the data points granularity in the response. The size must be a positive integer value. When combined with `unit`, this forms an expression similar to `1 hour`, or `1 day`, etc. The default value used is `5`. |
| `unit`<br/>_string_            | The unit of the data points granularity in the response. The unit must be a valid Java Chronounit. The default value is `MINUTES`.                                                                                           |
| `entityType`<br/>_String_      | The type of entity to query metrics for. When provided, only those metric records that have the provided `entityType` are aggregated.                                                                                        |
| `entityId`<br/>_UUID_          | The id of the entity to query metrics for. When provided, only those metric records that have the provided `entityId` are aggregated.                                                                                        |

| Attributes            | &nbsp;                                                           |
| --------------------- | ---------------------------------------------------------------- |
| `label`<br/>_UUID_    | The UTC timestamp used to label the value returned by the query. |
| `value`<br/>_Number_  | The value of the metric at the given timestamp.                  |
| `entityId`<br/>_UUID_ | The id of the entity metrics data was queried for.               |
