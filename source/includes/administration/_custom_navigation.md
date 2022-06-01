## Custom navigation 

Custom navigation API allows to customize the navigation per-reseller. Most notably it allows to customize what tabs are shown to a user in the main menu.

<!-------------------- List CUSTOM NAV -------------------->
### List custom navigation

`GET /navigation`

```shell

curl --request GET \
  --url http://portal.coxedge.com/api/v2/navigation/:id \
  --header 'Content-Type: application/json' \
  --header 'Mc-Api-Key: your_api_key'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "reseller": {
        "id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
      },
      "alwaysShowOrgPicker": false,
      "id": "f8663571-1d84-4d48-bb86-d4e2a14ea9f9",
      "enabled": true
    }
  ]
}
```

Retrieves a list of custom navigations. Since there is only one custom navigation per reseller this list will either be of length 1 or 0.

Query Params | &nbsp;
---- | -----------
`organization_id`<br/>*UUID* | Return only the custom navigation for the provided organization id. If not provided, will default to the calling user's organization. Must be a reseller organization.


Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The custom navigations's id.
`reseller.id`<br/>*UUID* | The organization id that the custom field belongs to.
`enabled`<br/>*boolean* | Whether not custom navigation is enabled on the reseller.
`alwaysShowOrgPicker`<br/>*boolean* | Whether or not to always show the organization picker in the sidebar, even when the user has access to only a single organization.

<!-------------------- Get CUSTOM NAV -------------------->
### Get custom navigation

`GET /navigation/:id`


```shell

curl --request GET \
  --url http://portal.coxedge.com/api/v2/navigation/f8663571-1d84-4d48-bb86-d4e2a14ea9f9 \
  --header 'Content-Type: application/json' \
  --header 'Mc-Api-Key: your_api_key'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "reseller": {
      "id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
    },
    "tabs": [
      {
        "name": {
          "en": "system en",
          "fr": "system fr"
        },
        "rank": 0,
        "id": "e4f527bf-9de6-4055-9ede-6949d01156f9",
        "tag": {
          "en": "tag en",
          "fr": "tag fr"
        },
        "type": "SYSTEM",
        "key": "/users"
      },
      {
        "name": {
          "en": "system en",
          "fr": "sytem fr"
        },
        "rank": 1,
        "id": "125e296a-ae59-4cd7-8d5b-0cf354cbb1cc",
        "type": "COMING_SOON"
      }
    ],
    "alwaysShowOrgPicker": false,
    "id": "f8663571-1d84-4d48-bb86-d4e2a14ea9f9",
    "enabled": true
  }
}
```

Retrieves a detailed custom navigation by id.

Query Params | &nbsp;
---- | -----------
`organization_id`<br/>*UUID* | Return only the custom navigation for the provided organization id. If not provided, will default to the calling user's organization. Must be a reseller organization.

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The custom navigations's id.
`reseller.id`<br/>*UUID* | The organization id that the custom field belongs to.
`enabled`<br/>*boolean* | Whether not custom navigation is enabled on the reseller.
`alwaysShowOrgPicker`<br/>*boolean* | Whether or not to always show the organization picker in the sidebar, even when the user has access to only a single organization.
`tabs`<br/>*Array[Object]* | List of tabs, the the order they should be displayed in a the menu.
`tabs.name`<br/>*Object* | Mapped object containing the tab name in different languages.
`tabs.tooltip`<br/>*Object* | Mapped object containing the tab's tooltip name in different languages.
`tabs.tag`<br/>*Object* | Mapped object containing the tab's tag name in different languages.
`tabs.rank`<br/>*int* | The order in which the tab will be displayed in the menu.
`tabs.type`<br/>*String* | Valid values are `SERVICE`, `SYSTEM` and `COMING_SOON`. 
`tabs.icon`<br/>*String* | A string representing a css icon class.
`tabs.serviceConnection`<br/>*UUID* | The service connection id for a tab of type `SERVICE`.
`tabs.workspace`<br/>*String* | The workspace name for a tab of type `SERVICE`. 
`tabs.key`<br/>*String* | The view key for a tab of type `SYSTEM`. 
`tabs.skipEnvironmentList`<br/>*boolean* | Skip the environment list if there is a single environment associated with the service tab. Configurable for a tab of type `SERVICE`.
`tabs.showSubTabs`<br/>*boolean* | Whether or not to show the subtabs, as defined by the plugin, underneath the menu tab. Configurable for a tab of type `SERVICE`.
`tabs.retainEnvironment`<br/>*boolean* | Retain the selected environment when navigating between tabs with the same service connection. Configurable for a tab of type `SERVICE`. 

<!-------------------- Create CUSTOM NAV -------------------->
### Create custom navigation

`POST /navigation`

```shell 
  --request POST \
  --url http://portal.coxedge.com/api/v2/navigation \
  --header 'Content-Type: application/json' \
  --header 'Mc-Api-Key: your_api_key' \
  --data '{
  "enabled": true,
  "reseller": {
    "id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
  },
  "tabs": [
    {
      "type": "SYSTEM",
      "key": "users",
      "name": {
        "en": "Users",
        "fr": "Usagers"
      }
    },
    {
      "type": "SERVICE",
      "name": {
        "en": "Edge compute",
        "fr": "Edge compute"
      },
      "serviceConnection": {
        "id": "2d49e70f-e4f8-43e3-b730-92328174214sa21"
      },
      "workspace": "compute",
      "showSubTabs": true,
      "skipEnvironmentPicker": true
    },
    {
      "type": "COMING_SOON",
      "name": {
        "en": "hot new feature",
        "fr": "hot new feature fr"
      }
    }
  ]
}'
```

> The above command returns JSON structured like this:
 
```json
{
  "data": {
    "reseller": {
      "id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
    },
    "tabs": [
      {
        "name": {
          "en": "Users",
          "fr": "Usagers"
        },
        "rank": 0,
        "id": "d95a83ed-ba25-432b-94c9-9d59e82f8284",
        "type": "SYSTEM",
        "key": "users"
      },
      {
        "workspace": "compute",
        "name": {
          "en": "Edge compute",
          "fr": "Edge compute"
        },
        "icon": "fa fa-server",
        "rank": 1,
        "skipEnvironmentPicker": true,
        "id": "6080bdb2-ceda-4774-aa28-c7f98cd804a4",
        "showSubTabs": true,
        "type": "SERVICE",
        "serviceConnection": {
          "id": "2d49e70f-e4f8-43e3-b730-92328174214sa21"
        }
      },
      {
        "name": {
          "en": "hot new feature",
          "fr": "hot new feature fr"
        },
        "rank": 2,
        "id": "cb36c538-6f6b-47af-bfa8-daad56ce58ed",
        "type": "COMING_SOON"
      }
    ],
    "alwaysShowOrgPicker": false,
    "id": "e80adf4d-5401-4cff-b393-93a7f10f4d71",
    "enabled": true
  }
}
```

Optional | &nbsp;
---------- | -----------
`reseller.id`<br/>*UUID* | The organization id that the custom field belongs to. If not provided defaults to caller's organization.
`enabled`<br/>*boolean* | Whether not custom navigation is enabled on the reseller. Defaults to false.
`alwaysShowOrgPicker`<br/>*boolean* | Whether or not to always show the organization picker in the sidebar, even when the user has access to only a single organization. Defaults to false.
`tabs`<br/>*Array[Object]* | List of tabs, in the order they should be displayed in the menu.
`tabs.type`<br/>*Object* | *Required* in tab object. Valid values are `SERVICE`, `SYSTEM` and `COMING_SOON`. 
`tabs.name`<br/>*Object* | *Required* in tab object. Mapped object containing the tab name in different languages. Need to specify all languages for target reseller's branding.
`tabs.tooltip`<br/>*Object* | Mapped object containing the tab's tooltip name in different languages. Need to specify all languages for target reseller's branding.
`tabs.tag`<br/>*Object* | Mapped object containing the tab's tag name in different languages. Need to specify all languages for target reseller's branding.
`tabs.icon`<br/>*String* | A string representing a css icon class.
`tabs.serviceConnection`<br/>*UUID* | *Required* if type `SERVICE`. The service connection id for a tab of type `SERVICE`.
`tabs.workspace`<br/>*String* | *Required* if type `SERVICE`. The workspace name for a tab of type `SERVICE`. 
`tabs.key`<br/>*String* |  *Required* if type `SYSTEM`. The view key for a tab of type `SYSTEM`. 
`tabs.skipEnvironmentList`<br/>*boolean* | Skip the environment list if there is a single environment associated with the service tab. Configurable for a tab of type `SERVICE`.
`tabs.showSubTabs`<br/>*boolean* | Whether or not to show the subtabs, as defined by the plugin, underneath the menu tab. Configurable for a tab of type `SERVICE`.
`tabs.retainEnvironment`<br/>*boolean* | Retain the selected environment when navigating between tabs with the same service connection. Configurable for a tab of type `SERVICE`. 

<!-------------------- Update CUSTOM NAV -------------------->
### Update custom navigation

`PUT /navigation/:id`

```shell 
curl --request PUT \
  --url http://portal.coxedge.com/api/v2/navigation/e80adf4d-5401-4cff-b393-93a7f10f4d71 \
  --header 'Content-Type: application/json' \
  --header 'Mc-Api-Key: your_api_key' \
  --data '{
	"id": "e80adf4d-5401-4cff-b393-93a7f10f4d71",
	"reseller": {
		"id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
	},
	"enabled": false,
	"tabs": []
}'
```

> The above command returns JSON structured like this:
 
```json
{
  "data": {
    "reseller": {
      "id": "c869e848-6fb3-4850-af3d-42c5666f2c78"
    },
    "tabs": [],
    "alwaysShowOrgPicker": false,
    "id": "e80adf4d-5401-4cff-b393-93a7f10f4d71",
    "enabled": false
  }
}
```

Update a custom navigation.

Required | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The id of the custom navigation. Cannot be changed.
`reseller.id`<br/>*UUID* | The organization id that the custom field belongs to. If not provided defaults to caller's organization.

Optional | &nbsp;
---------- | -----------
`enabled`<br/>*boolean* | Whether not custom navigation is enabled on the reseller. Defaults to false.
`alwaysShowOrgPicker`<br/>*boolean* | Whether or not to always show the organization picker in the sidebar, even when the user has access to only a single organization. Defaults to false.
`tabs`<br/>*Array[Object]* | List of tabs, in the order they should be displayed in a the menu. Replaces all tabs currently set on the object.
`tabs.type`<br/>*Object* | *Required* in tab object. Valid values are `SERVICE`, `SYSTEM` and `COMING_SOON`. 
`tabs.name`<br/>*Object* | *Required* in tab object. Mapped object containing the tab name in different languages. Need to specify all languages for target reseller's branding.
`tabs.tooltip`<br/>*Object* | Mapped object containing the tab's tooltip name in different languages. Need to specify all languages for target reseller's branding.
`tabs.tag`<br/>*Object* | Mapped object containing the tab's tag name in different languages. Need to specify all languages for target reseller's branding.
`tabs.icon`<br/>*String* | A string representing a css icon class.
`tabs.serviceConnection`<br/>*UUID* | *Required* if type `SERVICE`. The service connection id for a tab of type `SERVICE`.
`tabs.workspace`<br/>*String* | *Required* if type `SERVICE`. The workspace name for a tab of type `SERVICE`. 
`tabs.key`<br/>*String* |  *Required* if type `SYSTEM`. The view key for a tab of type `SYSTEM`. 
`tabs.skipEnvironmentList`<br/>*boolean* | Skip the environment list if there is a single environment associated with the service tab. Configurable for a tab of type `SERVICE`.
`tabs.showSubTabs`<br/>*boolean* | Whether or not to show the subtabs, as defined by the plugin, underneath the menu tab. Configurable for a tab of type `SERVICE`.
`tabs.retainEnvironment`<br/>*boolean* | Retain the selected environment when navigating between tabs with the same service connection. Configurable for a tab of type `SERVICE`. 

<!-------------------- Delete CUSTOM NAV -------------------->

### Delete custom navigation

`DELETE /navigation/:id`

```shell 
curl --request DELETE \
  --url http://portal.coxedge.com/api/v2/navigation/e80adf4d-5401-4cff-b393-93a7f10f4d71 \
  --header 'Mc-Api-Key: you_api_key'
```

> The above command returns JSON structured like this:

```json
{
  "taskId": "96bb7528-dc19-48b5-b713-9e55c7664aaf",
  "taskStatus": "SUCCESS"
}
```

Delete's a custom navigation configuration.
