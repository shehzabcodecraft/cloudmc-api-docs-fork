## Users

A user account allows users to authenticate to an [organization](#administration-organizations) and to have access to the resources in it. You can restrict user access to the system and environments by assigning them specific [roles](#administration-roles). Additionally, every user is given an API key which is needed to use our APIs. All operations done by users are persisted and can be accessed through the activity log.

<!-------------------- LIST USERS -------------------->

### List users

`GET /users`

```shell
# Retrieve visible users

curl "https://portal.coxedge.com/api/v2/users" \
   -H "MC-Api-Key: your_api_key"
```
> The above command returns a JSON structured like this:

```json
{
  "data":[{
    "id": "e83540c7-75a0-4715-96dc-c10a364e0390",
    "userName": "habsgoalie123",
    "firstName": "Carey",
    "lastName": "Price",
    "email": "gohabsgo@cloud.mc",
    "creationDate": "2017-08-15T12:00:00.000Z",
    "status": "ACTIVE",
    "locale": "en",
    "organization": {
      "id": "8e3393ce-ee63-4f32-9e0f-7b0200fa655a",
      "name": "Canadiens"
    },
    "serviceConnections": [
      {
        "id": "5d841eb6-5913-4244-b001-917228e7aa64",
        "name": "Microsoft Azure"
      },
      {
        "id": "61e5dc38-441b-4c7d-8ac4-087ebaab23da",
        "name": "swifttest"
      }
    ],
    "lastLogin": "2022-05-20T15:56:27.000Z",
    "lastFailedLogin": "2022-04-16T18:50:21.000Z",
    "loginCount": 76,
    "failedLoginCount": 10,
    "isBusinessContact": false,
    "isTechnicalContact": false,
    "tfaEnabled": false,
    "deleted": false,
    "receivesEmailNotifications": false,
    "canResendUserCreationEmail": true,
    "backupCodesRemaining": 0,
    "primaryRoleBinding": {
      "id": "013b40ca-9837-4233-b28e-09f5828958e5",
      "role": {
        "isSystem": true,
        "name": "guest",
        "id": "ad6b03cc-b9f3-48ae-9406-2ad168afbe01",
        "isFixed": true
      }
    }
  }]
}
```

Retrieve information about users you have access to. If you want access to other users in your [organization or sub-organizations](#administration-organizations), you will need to be assigned the `Users read` permission. Without this permission, you will only see your own user in the list.

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The id of the user.
`creationDate`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) that the user was created.
`email`<br/>*string* | The email of the user.
`firstName`<br/>*string* | The first name of the user.
`lastName`<br/>*string* | The last name of the user.
`organization`<br/>*[Organization](#administration-organization)* | The organization to which the user belongs.
`primaryRoleBinding`<br/>*RoleBinding* | The primary role assigned to this user. This role will always be a fixed role.
`serviceConnections`<br/>*Array[[ServiceConnection](#administration-service-connections)]* | The service connection of the user<br/>*includes*: `id`, `name`, `serviceCode`, `type`, and `state`
`status`<br/>*string* | The current status of the user.
`userName`<br/>*string* | The username of the user
`timezone`<br/>*string* | The timezone of the user.
`locale`<br/>*string* | The language set for the user.
`lastLogin`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) of the last login by the user.
`lastFailedLogin`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) of the last failed login by the user.
`loginCount`<br/>*integer* | The count of successful logins for that user.
`failedLoginCount`<br/>*integer* | The count of failed logins attempted by the user.
`isBusinessContact`<br/>*boolean* | Indicates whether the user is a business contact.
`isTechnicalContact`<br/>*boolean* | Indicates whether the user is a technical contact.
`receivesEmailNotifications`<br/>*boolean* | Indicates whether the user email notifications.
`canResendUserCreationEmail`<br/>*boolean* | Indicates whether the user creation email can be sent to the user.
`backupCodesRemaining`<br/>*integer* | The number of backup codes remaining for the user.

<!-------------------- GET USER -------------------->

### Retrieve a user

`GET /users/:id`

```shell
# Retrieve visible user
curl "https://portal.coxedge.com/api/v2/users/fdf60a19-980d-4380-acab-914485111305" \
   -H "MC-Api-Key: your_api_key"
```
> The above command returns a JSON structured like this:

```json
{
  "data":{
    "id": "fdf60a19-980d-4380-acab-914485111305",
    "userName": "frodo",
    "firstName": "Frodo",
    "lastName": "Baggins",
    "email": "frodo@cloud.mc",
    "creationDate": "2017-08-15T12:00:00.000Z",
    "status": "ACTIVE",
    "locale": "en",
    "organization": {
      "id": "c64dcd1d-9123-45e5-ad00-5d635c49176b",
      "name": "The Shire"
    },
    "serviceConnections": [
      {
        "serviceCode": "cs-acs-dev2",
        "name": "cs-acs-dev2",
        "id": "7430e95f-6029-444f-9677-9d2d54007138",
        "state": "PROVISIONED",
        "type": "cloudstack"
      },
      {
        "serviceCode": "cs-acs-dev1",
        "name": "cs-acs-dev1",
        "id": "9000c02b-cb33-4e4e-8d7b-f834f48e8fb9",
        "state": "ERROR_PROVISIONING",
        "type": "cloudstack"
      }
    ],
     "lastLogin": "2022-05-20T15:56:27.000Z",
    "lastFailedLogin": "2022-04-16T18:50:21.000Z",
    "loginCount": 76,
    "failedLoginCount": 10,
    "isBusinessContact": false,
    "isTechnicalContact": false,
    "tfaEnabled": false,
    "deleted": false,
    "receivesEmailNotifications": false,
    "canResendUserCreationEmail": true,
    "backupCodesRemaining": 0,
    "primaryRoleBinding": {
      "id": "013b40ca-9837-4233-b28e-09f5828958e5",
      "role": {
        "isSystem": true,
        "name": "guest",
        "id": "ad6b03cc-b9f3-48ae-9406-2ad168afbe01",
        "isFixed": true
      }
    }
  }
}
```

Retrieve information about a specific user. If you want access to other users in your [organization or sub-organizations](#administration-organizations), you will need to be assigned the `Users Read` permission.

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The id of the user.
`creationDate`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) that the user was created.
`email`<br/>*string* | The email of the user.
`firstName`<br/>*string* | The first name of the user.
`lastName`<br/>*string* | The last name of the user.
`organization`<br/>*[Organization](#administration-organization)* | The organization to which the user belongs.
`primaryRoleBinding`<br/>*RoleBinding* | The primary role assigned to this user. This role will always be a fixed role.
`serviceConnections`<br/>*Array[[ServiceConnection](#administration-service-connections)]* | The service connection of the user<br/>*includes*: `id`, `name`, `serviceCode`, `type`, and `state`
`status`<br/>*string* | The current status of the user.
`userName`<br/>*string* | The username of the user
`timezone`<br/>*string* | The timezone of the user.
`locale`<br/>*string* | The language set for the user.
`lastLogin`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) of the last login by the user.
`lastFailedLogin`<br/>*string* | The date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) of the last failed login by the user.
`loginCount`<br/>*integer* | The count of successful logins for that user.
`failedLoginCount`<br/>*integer* | The count of failed logins attempted by the user.
`isBusinessContact`<br/>*boolean* | Indicates whether the user is a business contact.
`isTechnicalContact`<br/>*boolean* | Indicates whether the user is a technical contact.
`receivesEmailNotifications`<br/>*boolean* | Indicates whether the user email notifications.
`canResendUserCreationEmail`<br/>*boolean* | Indicates whether the user creation email can be sent to the user.
`backupCodesRemaining`<br/>*integer* | The number of backup codes remaining for the user.
`identityProviderUsers`<br/>*Array* | A list of objects containing the ids of users associated with the identity provider, and their subject ids.


<!-------------------- CREATE USER -------------------->

### Create user

`POST /users`

```shell
# Create a user

curl -X POST "https://portal.coxedge.com/api/v2/users" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request-body"
```
> Request body example:

```json
{
  "userName": "vader42",
  "firstName": "Anakin",
  "lastName": "Skywalker",
  "email": "vader42@cloud.mc",
  "primaryRoleBinding": {
    "role": {
      "id": "4a1a44f3-ea74-4952-b9ef-ff3163c329d9",
    },
  },
  "organization": {
    "id": "645cf4ce-3699-40c5-a1a8-0b3e945f49ee"
  },
}
```

Create a user in a specific organization.

Users are created asynchronously on the underlying service(s) and progress is reflected in the state of the user's service connection(s).

You will need the `Create a new user` permission to execute this operation.

Required | &nbsp;
-------- | -----------
`userName`<br/>*string* | Username of the new user. Should be unique across the organization.
`firstName`<br/>*string* | First name of the user.
`lastName`<br/>*string* | Last name of the user.
`email`<br/>*string* | Email of the user. Should be unique across the organization.
`primaryRoleBinding.role.id`<br/>*UUID* | The id of the primary role to assign to this user

Optional | &nbsp;
-------- | -----------
`organization`</br>*[Organization](#administration-organization)* | Organization in which the user will be created. *Defaults to your organization*.<br/>*required:* `id`

Response | &nbsp;
---------- | -----------
`taskId`<br/>*UUID* | The id of the task
`taskStatus`<br/>*string* | The status of the task
`data`<br/>*[user](#administration-users)* | The information about the created user

```shell
# Response body example
```
The responses' `data` field contains the created [user](#administration-users) with its `id`.

```json
{
  "taskId": "633a85e5-447b-41db-a9a2-da986325955c",
  "taskStatus": "PENDING",
  "data": {
    "id": "c1ad55a9-0301-4925-bedc-106d31a73047",
    "userName": "bkenobi",
    "email": "bkenobi@gmail.com",
    "firstName": "Ben",
    "lastName": "Kenobi",
    "canResendUserCreationEmail": true,
    "deleted": false,
    "failedLoginCount": 0,
    "isBusinessContact": false,
    "isTechnicalContact": false,
    "locale": "en",
    "loginCount": 0,
    "receivesEmailNotifications": false,
    "serviceConnections": [],
    "status": "ACTIVE",
    "tfaEnabled": false,
    "organization": {
      "id": "bdb2d571-2878-462c-8162-9a034d5ab602",
      "name": "System"
    },
    "primaryRoleBinding": {
      "id": "013b40ca-9837-4233-b28e-09f5828958e5",
      "role": {
        "isSystem": true,
        "name": "guest",
        "id": "ad6b03cc-b9f3-48ae-9406-2ad168afbe01",
        "isFixed": true
      }
    }
  }
}
```

<!-------------------- UPDATE USER -------------------->

### Update user

`PUT /users/:id`

```shell
# Update a user
curl -X PUT "https://portal.coxedge.com/api/v2/users/fdf60a19-980d-4380-acab-914485111305" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json" \
   -d "request-body"
```
> Request body example:

```json
{
  "userName": "spidey1",
  "firstName": "Peter",
  "lastName": "Parker",
  "email": "spidey1@cloud.mc",
  "primaryRoleBinding": {
    "role": {
      "id": "4a1a44f3-ea74-4952-b9ef-ff3163c329d9",
    },
  },
}
```

Update a specific user. You will need the `Users update` permission to execute this operation.

Optional | &nbsp;
-------- | -----------
`userName`<br/>*string* | The new username of the user. Should be unique across the organization.
`firstName`<br/>*string* | The new first name of the user
`lastName`<br/>*string* | The new last name of the user
`primaryRoleBinding.role.id`<br/>*UUID* | The id of the primary role to assign to this user
`email`<br/>*string* | The new email of the user. Should be unique across the organization.

##### Returns

The responses' `data` field contains the updated [user](#administration-users).

<!-------------------- DELETE USER -------------------->

### Delete user

`DELETE /users/:id`

Users are deleted asynchronously on the underlying services.

The user model's status will be set to `DISABLED` prior to attempting the delete operation. This will prevent the user from login in or making API calls.

The user model will be deleted only when the user is removed from all environments AND from all underlying services.

If removing a user from an environment fails, no attempt will be made to delete the user model. This does not affect other attempts at removing the user from a different environment or deleting the user from a different service.

If deleting a user fails, subsequent delete attempts will be considered as a "force delete". A force delete entails reattempting to delete the user as explained above and then deleting the user model regardless of the response from the underlying services.

Delete a specific user. You will need the `Delete an existing user` permission to execute this operation.

```shell
# Delete a user
curl "https://portal.coxedge.com/api/v2/users/dd01c908-371c-4ec5-9fd7-80b1bfac8975" \
   -X DELETE -H "MC-Api-Key: your_api_key"
```

Response                  | &nbsp;
--------------------------|-----------------------
`taskId`<br/>*UUID*       | The id of the task
`taskStatus`<br/>*string* | The status of the task

```shell
# Response body example
```

```json
{
  "taskId": "cd921b44-ca9f-4f6b-b184-f952e5ab010a",
  "taskStatus": "PENDING"
}
```

<!-------------------- UNLOCK USER -------------------->


### Unlock user

`POST /users/:id/unlock`


```shell
# Unlock a user that was locked from the system

curl "https://portal.coxedge.com/api/v2/users/dd01c908-371c-4ec5-9fd7-80b1bfac8975/unlock" \
   -X POST -H "MC-Api-Key: your_api_key"

```

A user with 10 consecutive unsuccessful logins will be automatically locked by our system. This API can be used to unlock a user in this situation. You will need the `Unlock user` permission to execute this operation.

### Additional roles

With additional roles, you can allow users access to other organizations. You can specify a scope which targets one or many organizations with a specific role. See [roles](#administration-roles) for more information on roles.

#### Scoping

There are different types of scope that you can use depending on your use case. This scope must be provided when assigning an additional role to a user. You can only give a scope/role combination to another user if you have a higher or equivalent additional role.

Scope | Description | Required fields
---------- | ----------- | -----------
ORG_BASE | Applies the role on a specific organization | `organization.id`
ORG_TREE | Applies the role on a specific organization and its sub-organzations | `organization.id`
ORG_SUBS | Applies the role the sub-organzations of a specific organization | `organization.id`
ORG_TOPLEVEL | Applies the role on all top-level organizations | &nbsp;
TAGS_ANYMATCH | Applies the role on all organizations that are tagged with at least one the specified tags | `tags`

#### Get additional roles of user

`GET /users/:id/additional_roles`

```shell
# Get additional role of user
curl -X GET "https://portal.coxedge.com/api/v2/users/:id/additional_roles" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json"

# Response body example
```
```json
{
"data": [
    {
        "id": "ed18cdd0-0fa0-464d-a993-e689d39dfe2e",
        "creationDate": "2019-06-06T15:01:22.000Z",
        "scopeQualifier": "ORG_BASE",
        "primary": false,
        "role": {
            "id": "cc71a40b-d90b-40db-b724-08d71f5179b5",
            "name": "user",
            "isSystem": true,
            "isFixed": true
        },
        "organization": {
            "name": "Test",
            "id": "6861c664-0a83-4e91-bd8c-3a6083e81a13",
            "entryPoint": "test"
        },
        "user": {
            "id": "6ebc54bb-c3fe-4434-b412-09ac4f798680",
            "firstName": "franz",
            "lastName": "franz",
            "userName": "franz",
            "email": "fgarcia@cloudops.com"
        }
    }]
}
```

Attributes | &nbsp;
---------- | -----------
`id`<br/>*UUID* | The id of the additional role
`creationDate`<br/>*string* | The date the additional role was added/updated on the user
`scopeQualifier`<br/>*string* | The scope of this additional role (ORG_BASE, TAGS_ANYMATCH, GLOBAL, etc..). Please refer to the table above.
`tags`<br/>*[string]* | Organization tags to match for TAGS_ANYMATCH scoping
`role`<br/>*[Role](#administration-roles)* | The role to apply on the target scope
`organization`<br/>*[Organization](#administration-organizations)* | The organization of the additional role. Only present on scopes that target a specific organization.<br/>*includes*: `id`, `name`, `entryPoint`
`user`<br/>*[User](#administration-users)* | The user that the additional role is applied on<br/>*includes*: `id`, `username`, `firstName`, `lastName`, `email`
`primary`<br/>*boolean* | Indicates whether the role is primary.


#### Assign additional role to user

`POST /users/:id/additional_roles`

```shell
# Assign an additional role to user
curl -X POST "https://portal.coxedge.com/api/v2/users/:id/additional_roles" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json"
   -d "[request_body]"

# Request body example
```
```json
{
    "scopeQualifier": "ORG_BASE",
    "role": {
        "id": "cc71a40b-d90b-40db-b724-08d71f5179b5",
    },
    "organization": {
        "id": "6861c664-0a83-4e91-bd8c-3a6083e81a13",
    },
}
```

Required | &nbsp;
---------- | -----------
`scopeQualifier`<br/>*string* | The scope of this additional role (ORG_BASE, TAGS_ANYMATCH, GLOBAL, etc..)
`role.id`<br/>*UUID* | The id of the role to apply on the target scope. Operator cannot be used as additional role.
`organization.id`<br/>*UUID* | The id of the target organization of the scope. Only required when using a scope qualifier that targets an organization.
`tags`<br/>*UUID* | The organization tags of the scope. Only required when using the TAGS_ANYMATCH scope.

You will need to have `Users: Manage` permission to execute this operation.

#### Remove additional role from user
`DELETE /users/:user_id/additional_roles/:id`

```shell
# Remove an additional role from user
curl -X DELETE "https://portal.coxedge.com/api/v2/users/:user_id/additional_roles/:id" \
   -H "MC-Api-Key: your_api_key" \
   -H "Content-Type: application/json"

```

You will need to have `Users: Manage` permission to execute this operation.