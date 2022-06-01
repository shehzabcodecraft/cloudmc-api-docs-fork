## Branding

Manage branding.

<!-------------------- LIST BRANDINGS -------------------->

### List brandings

`GET /brandings`

```shell
# Retrieve branding
curl "https://portal.coxedge.com/api/v2/brandings" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "671f113c-dbbb-4478-be9c-90765b3259e5",
      "factory": false,
      "defaultLanguage": "en",
      "organization": {
        "id": "23910576-d29f-4c14-b663-31d728ff49a5"
      },
      "activeLanguages": "en,fr,es",
      "defaultTimezone": "America/Montreal",
      "applicationName": "Cox Edge application",
      "artifacts": [
        {
          "createdAt": "2020-09-14T11:42:52.000Z",
          "name": "android-chrome-144x144.png",
          "id": "642c73cf-d675-4b6f-826b-72d1a240542e",
          "mimeType": "image/png",
          "type": "FAVICON",
          "content": "iVBOR...kJggg==",
          "updatedAt": "2020-09-14T11:42:52.000Z"
        }
      ]
    }
  ]
}
```

List the branding configured for the organization.

| Query Params                 | &nbsp;                                                                                                               |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `organization_id`<br/>_UUID_ | Return only the branding for the provided organization id. If not provided, will default to the user's organization. |

| Attributes                            | &nbsp;                                                                                                    |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                       | The id of the branding.                                                                                   |
| `organization.id`<br/>_UUID_          | The organization id that the branding is linked to.                                                       |
| `defaultLanguage`<br/>_string_        | The default language.                                                                                     |
| `activeLanguages`<br/>_Array[string]_ | List of the possible languages.                                                                           |
| `defaultTimezone`<br/>_string_        | The default timezone.                                                                                     |
| `applicationName`<br/>_string_        | The application name displayed to the user.                                                               |
| `factory`<br/>_boolean_               | If the branding is the factory branding.                                                                  |
| `artifacts`<br/>_Array[Object]_       | The list of artifacts linked to the branding. This includes the custom css, colours css, logos, favicons. |
| `artifacts.id`<br/>_UUID_             | The artifact id.                                                                                          |
| `artifacts.name`<br/>_string_         | The artifact name.                                                                                        |
| `artifacts.mimeType`<br/>_string_     | The mime type of the artifact.                                                                            |
| `artifacts.type`<br/>_string_         | The artifact type. The possibles values are: LOGO, LOGO_SQUARE, FAVICON, CUSTOM_CSS, COLORS.              |
| `artifacts.content`<br/>_string_      | The artifact content.                                                                                     |
| `artifacts.createdAt`<br/>_string_    | The artifact creation date.                                                                               |
| `artifacts.updatedAt`<br/>_string_    | The artifact update date.                                                                                 |

<!-------------------- GET BRANDING -------------------->

### Retrieve branding

`GET /brandings/:id`

```shell
# Retrieve knowledge base
curl "https://portal.coxedge.com/api/v2/brandings/671f113c-dbbb-4478-be9c-90765b3259e5" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "671f113c-dbbb-4478-be9c-90765b3259e5",
    "factory": false,
    "defaultLanguage": "en",
    "organization": {
      "id": "23910576-d29f-4c14-b663-31d728ff49a5"
    },
    "activeLanguages": "en,fr,es",
    "defaultTimezone": "America/Montreal",
    "applicationName": "Cox Edge application",
    "artifacts": [
      {
        "createdAt": "2020-09-14T11:42:52.000Z",
        "name": "android-chrome-144x144.png",
        "id": "642c73cf-d675-4b6f-826b-72d1a240542e",
        "mimeType": "image/png",
        "type": "FAVICON",
        "content": "iVBOR...kJggg==",
        "updatedAt": "2020-09-14T11:42:52.000Z"
      }
    ]
  }
}
```

Retrieve the branding associated to the id.

| Attributes                            | &nbsp;                                                                                                    |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                       | The id of the branding.                                                                                   |
| `organization.id`<br/>_UUID_          | The organization id that the branding is linked to.                                                       |
| `defaultLanguage`<br/>_string_        | The default language.                                                                                     |
| `activeLanguages`<br/>_Array[string]_ | List of the possible languages.                                                                           |
| `defaultTimezone`<br/>_string_        | The default timezone.                                                                                     |
| `applicationName`<br/>_string_        | The application name displayed to the user.                                                               |
| `factory`<br/>_boolean_               | If the branding is the factory branding.                                                                  |
| `artifacts`<br/>_Array[Object]_       | The list of artifacts linked to the branding. This includes the custom css, colours css, logos, favicons. |
| `artifacts.id`<br/>_UUID_             | The artifact id.                                                                                          |
| `artifacts.name`<br/>_string_         | The artifact name.                                                                                        |
| `artifacts.mimeType`<br/>_string_     | The mime type of the artifact.                                                                            |
| `artifacts.type`<br/>_string_         | The artifact type. The possibles values are: LOGO, LOGO_SQUARE, FAVICON, CUSTOM_CSS, COLORS.              |
| `artifacts.content`<br/>_string_      | The artifact content.                                                                                     |
| `artifacts.createdAt`<br/>_string_    | The artifact creation date.                                                                               |
| `artifacts.updatedAt`<br/>_string_    | The artifact update date.                                                                                 |
