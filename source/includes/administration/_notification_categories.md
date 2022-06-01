## Notification Categories

Manage notification categories.

<!-------------------- LIST NOTIFICATION CATEGORIES -------------------->

### List notification categories

`GET /content/categories`

```shell
# Retrieve notification categories
curl "https://portal.coxedge.com/api/v2/api/v2/content/categories?language=:language&organization_id=:organizationId" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "organizationId": "3e824205-f507-4ffe-9891-a8addf3cf0e9",
      "createdAt": "2020-10-29T14:06:50.000Z",
      "translations": [
        {
          "language": "en",
          "id": "1cea5fe9-3bfa-4eea-a9aa-8e8aa8f85346",
          "text": "Test-notif-reseller",
          "type": "title",
          "version": 1
        },
        {
          "language": "fr",
          "id": "d4044366-2bf9-4c1f-9da5-e2e47b719714",
          "text": "test-notif-reseller",
          "type": "title",
          "version": 1
        }
      ],
      "icon": "fa fa-envelope",
      "id": "dc921a2a-16c2-4bc3-8ed6-bcb571bae241",
      "version": 1,
      "updatedAt": "2020-10-29T14:06:50.000Z"
    }
  ]
}
```

List the notification categories configured for the organization.

| Optional Query Parameters    | &nbsp;                                                                                                                                       |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `organization_id`<br/>_UUID_ | The id of the organization we wish to display notification categories for. If not provided, the current user's organization id will be used. |
| `language`<br/>_UUID_        | Language of the notification categories. Expected values are "en" (English), "fr" (French) or "es" (Spanish).                                |

| Attributes                           | &nbsp;                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                      | The id of the notification category.                                                        |
| `organizationId`<br/>_UUID_          | The organization id of the notification category.                                           |
| `createdAt`<br/>_string_             | The date on which the notification category was created.                                    |
| `updatedAt`<br/>_string_             | The date on which the notification category was updated.                                    |
| `icon`<br/>_string_                  | The icon used when displaying the notification category.                                    |
| `version`<br/>_integer_              | The notification category's version.                                                        |
| `translations`<br/>_Array[Object]_   | The translations of the notification category content.                                      |
| `translations.language`<br/>_string_ | The language of the translation.                                                            |
| `translations.text`<br/>_string_     | The content of the notification.                                                            |
| `translations.type`<br/>_string_     | The content that we are translating. For a notification category, this can only be "title". |
| `translations.id`<br/>_UUID_         | The translation's id.                                                                       |
| `translations.version`<br/>_integer_ | The translation's version.                                                                  |

<!-------------------- GET NOTIFICATION CATEGORY -------------------->

### Retrieve notification category

`GET /content/categories/:id`

```shell
# Retrieve notification category
curl "https://portal.coxedge.com/api/v2/api/v2/content/categories/:id?language=:language" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "organizationId": "3e824205-f507-4ffe-9891-a8addf3cf0e9",
    "createdAt": "2020-10-29T14:06:50.000Z",
    "translations": [
      {
        "language": "en",
        "id": "1cea5fe9-3bfa-4eea-a9aa-8e8aa8f85346",
        "text": "Test-notif-reseller",
        "type": "title",
        "version": 1
      },
      {
        "language": "fr",
        "id": "d4044366-2bf9-4c1f-9da5-e2e47b719714",
        "text": "test-notif-reseller",
        "type": "title",
        "version": 1
      }
    ],
    "icon": "fa fa-envelope",
    "id": "dc921a2a-16c2-4bc3-8ed6-bcb571bae241",
    "version": 1,
    "updatedAt": "2020-10-29T14:06:50.000Z"
  }
}
```

Get a specific notification category.

| Optional Query Parameters | &nbsp;                                                                                                        |
| ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `language`<br/>_UUID_     | Language of the notification categories. Expected values are "en" (English), "fr" (French) or "es" (Spanish). |

| Attributes                           | &nbsp;                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                      | The id of the notification category.                                                        |
| `organizationId`<br/>_UUID_          | The organization id of the notification category.                                           |
| `createdAt`<br/>_string_             | The date on which the notification category was created.                                    |
| `updatedAt`<br/>_string_             | The date on which the notification category was updated.                                    |
| `icon`<br/>_string_                  | The icon used when displaying the notification category.                                    |
| `version`<br/>_integer_              | The notification category's version.                                                        |
| `translations`<br/>_Array[Object]_   | The translations of the notification category's content.                                    |
| `translations.language`<br/>_string_ | The language of the translation.                                                            |
| `translations.text`<br/>_string_     | The content of the notification.                                                            |
| `translations.type`<br/>_string_     | The content that we are translating. For a notification category, this can only be "title". |
| `translations.id`<br/>_UUID_         | The translation's id.                                                                       |
| `translations.version`<br/>_integer_ | The translation's version.                                                                  |

<!-------------------- CREATE NOTIFICATION CATEGORY -------------------->

### Create notification category

`POST /content/categories/`

```shell
# Create notification category
curl -X POST "https://portal.coxedge.com/api/v2/api/v2/content/categories/" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request-body"
```

> Request body example:

```json
{
  "organizationId": "2cc1b5ba-2cfb-4bf9-9cb9-c67d34ba27b1",
  "icon": "fa fa-envelope",
  "translations": [
    {
      "language": "en",
      "type": "title",
      "text": "trial-ttt"
    },
    {
      "language": "fr",
      "type": "title",
      "text": "trial-tt"
    }
  ]
}
```

Create a notification category.

| Required                             | &nbsp;                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `organizationId`<br/>_UUID_          | The organization id of the notification category.                                           |
| `icon`<br/>_string_                  | The icon used when displaying the notification category.                                    |
| `translations`<br/>_Array[Object]_   | The translations of the notification category's content.                                    |
| `translations.language`<br/>_string_ | The language of the translation.                                                            |
| `translations.text`<br/>_string_     | The content of the notification.                                                            |
| `translations.type`<br/>_string_     | The content that we are translating. For a notification category, this can only be "title". |

<!-------------------- UPDATE NOTIFICATION CATEGORY -------------------->

### Update notification category

`PUT /content/categories/:id`

```shell
# Update notification category
curl -X PUT "https://portal.coxedge.com/api/v2/api/v2/content/categories/:id" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request-body"
```

> Request body example:

```json
{
  "id": "dc921a2a-16c2-4bc3-8ed6-bcb571bae241",
  "organizationId": "3e824205-f507-4ffe-9891-a8addf3cf0e9",
  "icon": "fa fa-envelope",
  "translations": [
    {
      "language": "en",
      "text": "Test-notif-reseller",
      "type": "title"
    },
    {
      "language": "fr",
      "text": "test-notif-reseller",
      "type": "title"
    }
  ]
}
```

Update a notification category.

| Required                             | &nbsp;                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                      | The id of the notification category.                                                        |
| `organizationId`<br/>_UUID_          | The organization id of the notification category.                                           |
| `icon`<br/>_string_                  | The icon used when displaying the notification category.                                    |
| `translations`<br/>_Array[Object]_   | The translations of the notification category's content.                                    |
| `translations.language`<br/>_string_ | The language of the translation.                                                            |
| `translations.text`<br/>_string_     | The content of the notification.                                                            |
| `translations.type`<br/>_string_     | The content that we are translating. For a notification category, this can only be "title". |

| Optional                     | &nbsp;                                                                                                                       |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `translations.id`<br/>_UUID_ | When specified, the existing translation will be modified. If not provided, a new translation will replace the existing one. |

<!-------------------- DELETE NOTIFICATION CATEGORY -------------------->

### Delete notification category

`DELETE /content/categories/:id`

```shell
# Delete a notification category
curl "https://portal.coxedge.com/api/v2/content/categories/:id" \
   -X DELETE -H "MC-Api-Key: your_api_key"

```

Delete a notification category. You must ensure that this category has no associated notification.
