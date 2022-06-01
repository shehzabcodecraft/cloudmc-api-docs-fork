## Service connections

Service connections are the services that you can create resources for (e.g. compute, object storage). Service connections are scoped to [Organizations](#administration-organizations). Thus, the relationship between a service connection and an organization can be either **ownership** _(where the organization owns the connection)_ or **assignation** _(where the connection is assigned to an organization but is owned by another)_ [Environments](#administration-environments) are created for a specific service which allows you to create and manage resources within that service.

<!-------------------- LIST SERVICE CONNECTIONS -------------------->

### List service connections

`GET /services/connections?organizationId=9571b279-abaf-4a37-9f39-85d1a915af7d`

```json
{
  "data": [
    {
      "id": "adfbdb51-493b-45b1-8802-3f6327afb9e6",
      "serviceCode": "compute-qc",
      "creationDate": "2021-12-09T21:02:16.000Z",
      "name": "Compute - Québec",
      "type": "CloudCA",
      "status": {
        "lastUpdated": "2017-08-15T12:00:00.000Z",
        "reachable": true
      },
      "organization": {
        "name": "System",
        "id": "5d841eb6-5913-4244-b001-917228e7aa64"
      },
      "metricsEnabled": true,
      "supportsQuotas": true,
      "supportsPricingV2": true,
      "supportsPolicies": true,
      "hasWidgets": false,
      "supportsUsage": true,
      "supportsInfra": true,
      "lastUsageRecord": "2022-03-28T18:59:59.000Z",
      "quotas": [
        {
          "name": "DefaultQuota",
          "id": "081b1ebb-16c4-49e0-8120-a5b8b356b269"
        },
        {
          "name": "CsQuota",
          "id": "3734dfed-9d43-4543-ac01-bdd32875e0eb"
        }
      ]
    }
  ]
}
```

List service connections that are owned by a organization.

| Attributes                        | &nbsp;                                                                                                        |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                   | The id of the service connection.                                                                             |
| `serviceCode`<br/>_string_        | The service code of the service connection. It is used in the endpoint of the services API.                   |
| `creationDate`<br/>_string_       | The date the service connection was created.                                                                  |
| `name`<br/>_string_               | The name of the service connection.                                                                           |
| `type`<br/>_string_               | The type of the service connection.                                                                           |
| `status`<br/>_Object_             | Status of the service connection. Tells you if the service is up.<br/>_includes_: `lastUpdated`, `reachable`. |
| `organization`<br/>_Object_       | Organization that owns this service connection.<br/>_includes_: `id`, `name`                                  |
| `metricsEnabled`<br/>_boolean_    | Is metric collection allowed on this service connection.                                                      |
| `supportsQuotas`<br/>_boolean_    | Are quotas supported on this service connection.                                                              |
| `supportsPricingV2`<br/>_boolean_ | Is the V2 pricing engine supported on this service connection.                                                |
| `supportsPolicies`<br/>_boolean_  | Are policies supported on this service connection.                                                            |
| `supportsUsage`<br/>_boolean_     | Is usage collection supported on this service connection.                                                     |
| `supportsInfra`<br/>_boolean_     | Is infra supported on this service connection.                                                                |
| `hasWidgets`<br/>_boolean_        | Does this service connection have widgets.                                                                    |
| `lastUsageRecord`<br/>_string_    | The date which the latest usage record was recorded.                                                          |
| `quotas`<br/>_Array[object]_      | The list of quota assigned to the organization.<br/>_includes_: `id`, `name`                                  |

| Optional query parameters     | &nbsp;                                                                                                                                |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `organizationId`<br/>_string_ | The organization whose connections are to be retrieved. If this is not provided then the request defaults to the user's organization. |

<!-------------------- GET SERVICE CONNECTION -------------------->

### Retrieve a service connection

`GET /services/connections/:id`

```json
{
  "data": [
    {
      "id": "adfbdb51-493b-45b1-8802-3f6327afb9e6",
      "serviceCode": "compute-qc",
      "creationDate": "2021-12-09T21:02:16.000Z",
      "name": "Compute - Québec",
      "type": "CloudCA",
      "status": {
        "lastUpdated": "2017-08-15T12:00:00.000Z",
        "reachable": true
      },
      "organization": {
        "name": "System",
        "id": "5d841eb6-5913-4244-b001-917228e7aa64"
      },
      "metricsEnabled": true,
      "supportsQuotas": true,
      "supportsPricingV2": true,
      "supportsPolicies": true,
      "hasWidgets": false,
      "supportsUsage": true,
      "supportsInfra": true,
      "lastUsageRecord": "2022-03-28T18:59:59.000Z",
      "quotas": [
        {
          "name": "DefaultQuota",
          "id": "081b1ebb-16c4-49e0-8120-a5b8b356b269"
        },
        {
          "name": "CsQuota",
          "id": "3734dfed-9d43-4543-ac01-bdd32875e0eb"
        }
      ]
    }
  ]
}
```

Fetch a service connection.

| Attributes                        | &nbsp;                                                                                                        |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                   | The id of the service connection.                                                                             |
| `serviceCode`<br/>_string_        | The service code of the service connection. It is used in the endpoint of the services API.                   |
| `creationDate`<br/>_string_       | The date the service connection was created.                                                                  |
| `name`<br/>_string_               | The name of the service connection.                                                                           |
| `type`<br/>_string_               | The type of the service connection.                                                                           |
| `status`<br/>_Object_             | Status of the service connection. Tells you if the service is up.<br/>_includes_: `lastUpdated`, `reachable`. |
| `organization`<br/>_Object_       | Organization that owns this service connection.<br/>_includes_: `id`, `name`                                  |
| `metricsEnabled`<br/>_boolean_    | Is metric collection allowed on this service connection.                                                      |
| `supportsQuotas`<br/>_boolean_    | Are quotas supported on this service connection.                                                              |
| `supportsPricingV2`<br/>_boolean_ | Is the V2 pricing engine supported on this service connection.                                                |
| `supportsPolicies`<br/>_boolean_  | Are policies supported on this service connection.                                                            |
| `supportsUsage`<br/>_boolean_     | Is usage collection supported on this service connection.                                                     |
| `supportsInfra`<br/>_boolean_     | Is infra supported on this service connection.                                                                |
| `hasWidgets`<br/>_boolean_        | Does this service connection have widgets.                                                                    |
| `lastUsageRecord`<br/>_string_    | The date which the latest usage record was recorded.                                                          |
| `quotas`<br/>_Array[object]_      | The list of quota assigned to the organization.<br/>_includes_: `id`, `name`                                  |

<!-------------------- GET APIINFO -------------------->

### Retrieve API credentials

`GET /services/connections/:id/apiInfo`

```shell
# Retrieve your API credentials
curl -X GET \
  "https://portal.coxedge.com/api/v2/services/connections/378442e0-d9a4-4e55-83e3-220ba1f909a8/apiInfo?environmentId=c880f6b2-f52e-40d5-b289-7211c0319ebc" \
  -H "MC-Api-Key: your_api_key" \
# Response body example
```

```json
{
  "data": {
    "canRegenerateCredentials": true,
    "fields": [
      {
        "key": "endpoint",
        "value": "https://your_endpoint.com/auth",
        "sensitive": false,
        "environmentSpecific": false
      },
      {
        "key": "api_key",
        "value": "my_api_key",
        "sensitive": true,
        "environmentSpecific": false
      },
      {
        "key": "secret_key",
        "value": "my_secret_key",
        "sensitive": true,
        "environmentSpecific": false
      },
      {
        "key": "project_id",
        "value": "079bdead-61b5-4b38-86ed-dbbf963808ec",
        "sensitive": false,
        "environmentSpecific": false
      }
    ]
  }
}
```

Retrieve your API keys for some environment within a service. A user can only access their own API keys and only for environments where they are a member.

| Query Parameters (_required_) | &nbsp;                     |
| ----------------------------- | -------------------------- |
| `environmentId`<br/>_UUID_    | The id of the environment. |

| Attributes                               | &nbsp;                                                                                                                                                                                                                       |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `canRegenerateCredentials`<br/>_boolean_ | True if the user can regenerate their API keys for the service.                                                                                                                                                              |
| `fields`<br/>_Array[object]_             | An array of objects that describe the different parameters (_e.g. endpoint, api_key, secret_key, project_id_) comprised in the users' API credentials.<br/>_includes_: `key`, `value`, `sensitive` and `environmentSpecific` |

<!-------------------- GET PARAMETERS -------------------->

### Retrieve connection parameters

`GET /services/connections/:id/parameters`

```shell
# Retrieve the connection parameters
curl -X GET \
  "https://portal.coxedge.com/api/v2/services/connections/378442e0-d9a4-4e55-83e3-220ba1f909a8/parameters" \
  -H "MC-Api-key: your_api_key" \
# Response body example
```

```json
{
  "data": [
    {
      "parameter": "jsonCredentials",
      "id": "ee7f5ba3-3efc-4efd-819b-1dd947b3473a",
      "value": "JSON representation of credentials here",
      "serviceConnection": {
        "id": "d461e683-30c9-4b4e-bab6-def1a3575227"
      }
    },
    {
      "parameter": "billingAccountId",
      "id": "cd404ae3-884d-4b38-a9b7-cd1bba5c0a46",
      "value": "02C9H96Q-2H1JS2-K9SJD8",
      "serviceConnection": {
        "id": "d461e683-30c9-4b4e-bab6-def1a3575227"
      }
    }
  ]
}
```

Retrieve a service connection's parameters, used to create and manage connections to services. You can retreive these parameteres only if you are assigned a role that has the `Manage Service connections` permission granted to it.

| Attributes                 | &nbsp;                                                                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `data`<br/>_Array[object]_ | An array of objects that describe the service connection parameters.<br/>_includes_: `parameter`, `id`, `value` and `serviceConnection.id` |

<!-------------------- GET SERVICE DESCRIPTOR PARAMETERS -------------------->

### Retrieve descriptor parameters

`GET /services/descriptors/:pluginType/parameters`

```shell
# Retrieve service connection parameters

curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/descriptors/gcp/parameters"
```

> Request body example:

```json
{
  "data": [
    {
      "field": "parentType",
      "label": "gcp.service_configuration.parameters.parent_type.label",
      "options": [
        {
          "value": "folder",
          "type": "option",
          "name": "gcp.service_configuration.parameters.parent_type.folder",
          "is18n": true
        },
        {
          "value": "organization",
          "type": "option",
          "name": "gcp.service_configuration.parameters.parent_type.organization",
          "is18n": true
        }
      ],
      "required": true,
      "disabled": false,
      "sectionsToReload": [],
      "type": "select"
    },
    {
      "field": "parentId",
      "label": "gcp.service_configuration.parameters.parent_id.label",
      "descriptionLabel": "gcp.service_configuration.parameters.parent_id.description",
      "required": true,
      "disabled": false,
      "sectionsToReload": [],
      "type": "text"
    },
    {
      "field": "jsonCredentials",
      "label": "gcp.service_configuration.parameters.json_credentials.label",
      "required": true,
      "disabled": false,
      "sectionsToReload": [],
      "type": "textarea"
    },
    {
      "field": "billingAccountId",
      "label": "gcp.service_configuration.parameters.billing_account.label",
      "descriptionLabel": "gcp.service_configuration.parameters.billing_account.description",
      "required": true,
      "disabled": false,
      "sectionsToReload": [],
      "type": "text"
    }
  ]
}
```

| Attributes                            | &nbsp;                                                                                                  |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `data`<br/>_Array_                    | An array of connection parameters, each with the following properties.                                  |
| `field`<br/>_string_                  | The name of connection parameter.                                                                       |
| `type`<br/>_string_                   | The type of the connection parameter. Possible values are `text`, `textarea`, `select`, `checkbox`.     |
| `options`<br/>_Array[select options]_ | A list of possible options for parameters of `type` = `select`                                          |
| `required`<br/>_boolean_              | An indication as to whether or not this parameter is a required one when creating a service connection. |
| `disabled`<br/>_boolean_              | Whether or not this parameter is a disabled.                                                            |
| `options`<br/>_Array[string]_         | A list of sections to reload when this field is modified.                                               |

This call returns a list of parameters that must be provided _(when creating a new `ServiceConnection`)_ for CloudMc to be able to successfully connect to service. While, the response includes a variety of information, the `field` attribute of each paramter object returned is the parameter identifier. This is used together with some value to provide the connection parameters when [creating a new `ServiceConnection`](#administration-create-service-connection).

<!-------------------- CREATE SERVICE CONNECTION -------------------->

### Create service connection

`POST /services/connections`

```shell
# Create a service connection

curl -X POST "https://portal.coxedge.com/api/v2/services/connections" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request_body"
```

> Request body example:

```json
{
  "name": "GCP-AmericasRegion",
  "type": "gcp",
  "serviceCode": "gcp-americas",
  "trialEnabled": false,
  "usageEnabled": false,
  "metricsEnabled": false,
  "commitmentTrackingEnabled": false,
  "groupedParameters": [],
  "dependentConnection": null,
  "locations": [],
  "organization": {
    "id": "9571b279-abaf-4a37-9f39-85d1a915af7d"
  },
  "parameters": [
    {
      "parameter": "parentType",
      "value": "folder"
    },
    {
      "parameter": "parentId",
      "value": "9123843023"
    },
    {
      "parameter": "jsonCredentials",
      "value": "<GCP-SERVICE-ACCOUNT-CREDENTIALS>"
    },
    {
      "parameter": "billingAccountId",
      "value": "141F7D-FDK3D0-F99HW2"
    },
    {
      "parameter": "billingSubAccountsEnabled",
      "value": ""
    },
    {
      "parameter": "billingDatasetName",
      "value": "cmc_usage"
    }
  ]
}
```

Create a new service connection in a specific organization. You will need the `Reseller connections` permission to execute this operation.

| Required                                                                                         | &nbsp;                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`<br/>_string_                                                                              | The name of the new service connection.                                                                                                                                                                                                                                                                                               |
| `type`<br/>_string_                                                                              | The type of new service connection. _(e.g. gcp, azure, aws, cloudca, swift, etc.)_                                                                                                                                                                                                                                                    |
| `serviceCode`<br/>_string_                                                                       | A globally unique code that identifies this service connection.                                                                                                                                                                                                                                                                       |
| `organization`<br/>_[Organization](#administration-organizations)_                               | The organization that the service connection should be created in. <br/>_required attributes of the organization_: `id`                                                                                                                                                                                                               |
| `parameters`<br/>_Array[connection parameters](#administration-retrieve-connection-parameters)]_ | An array of connection parameters specific to this connection type along with their values. This array should contain all `required` parameters from the list returned from the [retrieve connection parameters](#administration-retrieve-connection-parameters) API. <br/>_required attributes per parameter_: `parameter`, `value`. |

| Optional query parameters                | &nbsp;                                                                                              |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `trialEnabled`<br/>_string_              | Are trials allowed on this service connection.                                                      |
| `usageEnabled`<br/>_string_              | Is usage collection enabled on this service connection.                                             |
| `metricsEnabled`<br/>_string_            | Is metric collection enabled on this service connection.                                            |
| `commitmentTrackingEnabled`<br/>_string_ | Is commitment tracking enabled on this service connection.                                          |
| `dependentConnection`<br/>_object_       | The dependent connection if there is one.                                                           |
| `locations`<br/>_Array[object]_          | Locations of a service connection region.<br/>_includes_: `name`, `lat` and `lng`                   |
| `groupedParameters`<br/>_Array[object]_  | An array of grouped connection parameters specific to this connection type along with their values. |

<!-------------------- TEST NEW SERVICE CONNECTION -------------------->

### Test new service connection

`POST /services/connections/test`

```shell
# Test a new service connection

curl -X POST "https://portal.coxedge.com/api/v2/services/connections/test" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request_body"
```

> Request body example:

```json
# requires the same request body
# as outlined in the 'Create service connection' section
```

Test a new service connection before creating it. The request body is the same as that which is used when creating a new service connection.

<!-------------------- TEST EXISTING SERVICE CONNECTION -------------------->

### Test existing service connection

`POST /services/connections/:id/test`

```shell
# Test a new service connection

curl -X POST "https://portal.coxedge.com/api/v2/services/connections/9571b279-abaf-4a37-9f39-85d1a915af7d/test" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json"
```

Test an existing service connection. This request does not require a body. The `connection id` is passed as a path parameter in the request.

<!-------------------- GET CONNECTION POLICY DESCRIPTORS -------------------->

### Retrieve connection policy descriptors

`GET /services/connections/:id/policies/descriptors`

| Query Parameters       | &nbsp;                                                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `section`<br/>_string_ | The name of the policy section to load. Only the policy section matching the section name provided will return all required FormElements and the connection entity. |

```shell
# Retrieve connection policy descriptors
curl "https://portal.coxedge.com/api/v2/services/connections/03bc22bd-adc4-46b8-988d-afddc24c0cb5/policies/descriptors?section=trials" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "name": "general",
      "label": "general",
      "optional": false,
      "subsection": false
    },
    {
      "name": "trials",
      "formElements": [
        {
          "label": "cloudstack.service_configuration.policies.trials.network_config_for_trial_env.label",
          "descriptionLabel": "cloudstack.service_configuration.policies.trials.network_config_for_trial_env.description",
          "interpolation": {},
          "options": [
            {
              "value": "isolatedNetwork",
              "type": "option",
              "name": "cloudstack.service_configuration.policies.trials.network_config_for_trial_env.options.isolated_network",
              "is18n": true
            },
            {
              "value": "singleNetwork",
              "type": "option",
              "name": "cloudstack.service_configuration.policies.trials.network_config_for_trial_env.options.single_subnet_vpc",
              "is18n": true
            }
          ],
          "disabled": false,
          "required": true,
          "subsection": false,
          "field": "trials:network_config_for_trial_envs",
          "reloadOnChange": false,
          "sectionsToReload": [],
          "type": "select"
        }
      ],
      "entity": {
        "id": "7486dfbf-740d-49b1-ba68-6e4b0070ebbb",
        "name": "Google Cloud Connection",
        "policies": {
          "version": "1.0",
          "cacheEnabled": "false",
          "regions": "us-east,eu-west"
        }
      }
    }
  ]
}
```

Retrieve the policy descriptors of an service connection.

| Attributes                 | &nbsp;                                                                                                                                                                  |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`<br/>_string_        | The name of the policy section.                                                                                                                                         |
| `label`<br/>_string_       | The label key for the policy section name.                                                                                                                              |
| `formElements`<br/>_Array_ | The FormElements returned by the policy section. Form elements are only returned for a given section if the query param `section` matches the name of a policy section. |
| `optional`<br/>_boolean_   | Specifies if the policy section is required or not.                                                                                                                     |
| `subsection`<br/>_boolean_ | Specifies if the policy has a subsection.                                                                                                                               |
| `entity`<br/> _Object_     | The service connection entity which includes a string to string map of the `ServiceConnectionPolicy::name` to `ServiceConnectionPolicy::value`.                         |

<!-------------------- UPDATE CONNECTION POLICIES -------------------->

### Update connection policies

`PUT /services/connections/:id/policies`

```shell
curl -X PUT \
   -H "Content-Type: application/json" \
   -H "MC-Api-Key: your_api_key" \
   -d "[{"name": "serviceVersion", "value": "1.1"}, {"name": "cacheEnabled", "value": "true"}]" \
   "https://portal.coxedge.com/api/v2/services/connections/03bc22bd-adc4-46b8-988d-afddc24c0cb5/policies"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "id": "003c32af-e4e0-440c-871e-f20a81e6c0b7",
      "name": "serviceVersion",
      "value": "1.1"
    },
    {
      "id": "a31f100a-f7c8-43d5-b64d-ee2db466f37d",
      "name": "cacheEnabled",
      "value": "true"
    },
    {
      "id": "c681774a-a96c-4dff-a2a6-2e9651459de7",
      "name": "regions",
      "value": "us-east,eu-west"
    }
  ]
}
```

| Attributes           | &nbsp;                  |
| -------------------- | ----------------------- |
| `name`<br/>_string_  | The name of the policy. |
| `value`<br/>_string_ | The policy value.       |

<!-------------------- LIST ASSIGNED ORGANIZATIONS CONNECTIONS -------------------->

### List organizations assigned to a service connection

`GET /services/connections/:id/assigned_organizations?organizationId=:orgId`

```json
{
  "data": [
    {
      "id": "679fe078-a67a-4383-ab4e-51f5ef3a9287",
      "name": "MyOrg",
      "entryPoint": "my-org",
      "state": "PROVISIONED",
      "quota": {
        "id": "90c3e469-71c7-4231-b27b-31dcf3a820ad",
        "name": "Unlimited"
      }
    },
    {
      "id": "9571b279-abaf-4a37-9f39-85d1a915af7d",
      "name": "Sysco Labs",
      "entryPoint": "syscolab",
      "state": "PROVISIONED",
      "quota": {
        "id": "66a773e8-a7e9-498b-a01d-68c8f9df2fd4",
        "name": "trial"
      }
    },
    {
      "id": "d84125c6-1417-4aa3-8293-a5ddde2bfeac",
      "name": "Symcentric",
      "entryPoint": "symcentric",
      "state": "PROVISIONED",
      "quota": {
        "id": "66a773e8-a7e9-498b-a01d-68c8f9df2fd4",
        "name": "trial"
      }
    }
  ]
}
```

Returns a list of organizations to which the service connection is assigned. Only organizations that the caller has access to will be returned. _Read description of the `organizationId` query parameter below for more details about the returned list._

| Attributes                | &nbsp;                                                                                                                                                     |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_           | The id of the organization.                                                                                                                                |
| `name`<br/>_string_       | The name of the organization.                                                                                                                              |
| `entryPoint`<br/>_string_ | The entry point of the organization. Also refered to as the organization code.                                                                             |
| `state`<br/>_string_      | The provisioning state of the organization on the backend service. States: `PENDING`, `PROVISIONING`, `PROVISIONED`, `PENDING_PURGE`, `PURGING`, `PURGED`. |
| `quota`<br/>_Object_      | The quota assigned to the organization (may be null depending on if the connection supports quotas or not).<br/>_includes_: `id`, `name`                   |

| Optional query parameters     | &nbsp;                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organizationId`<br/>_string_ | The organization from whose scope the request is being made. Based on this the returned list may vary. Organizations that are above this organization _(represented by the id)_ in the organization tree hierarchy will be filtered from the returned list even if they have the connection assigned to them. If this is not provided then the request defaults to the user's organization. |
