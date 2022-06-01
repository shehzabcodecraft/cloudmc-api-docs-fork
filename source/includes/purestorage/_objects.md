### Objects

View and manage your objects within a bucket.

<!-------------------- LIST OBJECTS -------------------->

#### List Objects

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects?bucketId=us-east-1/bucket-root-brdje"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "name": "text.rtf",
      "id": "us-east-1/bucket-root-brdje/text.rtf",
      "size": 14403501,
      "fullPath": "text.rtf",
      "storageClass": "STANDARD",
      "lastModified": "Fri May 06 09:09:15 EDT 2022",
      "displaySize": {
        "value": "13.7",
        "unitKey": "units.filesizes.MB"
      },
      "contentType": "application/rtf",
      "eTag": "4bdf0a5e8c871d520f835b2fc519f263",
      "bucketName": "bucket-root-brdje",
      "region": "us-east-1",
      "containingFolder": "",
      "isFolder": false,
      "isVirtual": false
    },
    {
      "name": "photos",
      "id": "us-east-1/bucket-root-brdje/photos/",
      "fullPath": "photos/",
      "contentType": "application/directory",
      "eTag": "",
      "bucketName": "bucket-root-brdje",
      "region": "us-east-1",
      "containingFolder": "",
      "isFolder": true,
      "isVirtual": true
    }
  ],
  "metadata": {
    "recordCount": 3
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects?bucketId=`:regionName/:bucketName`</code>

Retrieve a list of objects inside a given bucket.

| Attributes                      | &nbsp;                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`<br/>_string_             | The name of the object.                                                                                                                                                                                                                                                                                                                                           |
| `id`<br/>_string_               | The ID of the object, which is of the form `:regionName/:bucketName/:objectName`.                                                                                                                                                                                                                                                                                 |
| `size`<br/>_integer_            | The size of the object in bytes.                                                                                                                                                                                                                                                                                                                                  |
| `fullPath`<br/>_string_         | The actual key of the object inside the bucket, which is represented as a full path.                                                                                                                                                                                                                                                                              |
| `storageClass`<br/>_string_     | The type of storage class on the object.                                                                                                                                                                                                                                                                                                                          |
| `lastModified`<br/>_string_     | The date the object was last updated.                                                                                                                                                                                                                                                                                                                             |
| `displaySize`<br/>_string_      | The size of the object represented as an object in either KB, MB, or GB.                                                                                                                                                                                                                                                                                          |
| `contentType`<br/>_string_      | The type of file.                                                                                                                                                                                                                                                                                                                                                 |
| `eTag`<br/>_string_             | The eTag of the object generated by S3 during initial upload.                                                                                                                                                                                                                                                                                                     |
| `bucketName`<br/>_string_       | The name of the bucket the object exists within.                                                                                                                                                                                                                                                                                                                  |
| `region`<br/>_string_           | The name of the region the object exists within.                                                                                                                                                                                                                                                                                                                  |
| `containingFolder`<br/>_string_ | The folder containing the object. An empty string is returned if the object is not contained within a folder in the bucket.                                                                                                                                                                                                                                       |
| `isFolder`<br/>_boolean_        | Boolean denoting whether the object acts as a folder. This is always true when the `fullPath` attribute ends with a '/' character.                                                                                                                                                                                                                                |
| `isVirtual`<br/>_boolean_       | Boolean value denoting whether the folder is virtual. If true there exists no object named `:folderName/`, and the folder exists only as a part of a complete object path (`:folderName/:objectName`). If false, there exists a key in the bucket named ‘{folderName}/’. If the query parameter `nested = true`, the request will not return any virtual folders. |

| Required Query Parameters | &nbsp;                                                      |
| ------------------------- | ----------------------------------------------------------- |
| `bucketId`<br/>_string_   | The ID of the bucket of the form `:regionName/:bucketName`. |

| Optional Query Paramaters | &nbsp;                                                                                                                                                                                        |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `prefix`<br/>_string_     | The path of the objects to search in. If prefix is left blank, it will search for objects in the root. If `nested = true` and prefix is left blank, it will obtain all objects in the bucket. |
| `nested`<br/>_boolean_    | Whether to include nested objects or just include objects in the root of the prefix. If `nested = true`, the request will not return any virtual folders. Defaults to false.                  |

<!-------------------- GET OBJECT -------------------->

#### Retrieve an Object

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/us-east-1/bucket-root-brdje/photos/miami.png"
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "name": "miami.png",
    "id": "us-east-1/bucket-root-brdje/photos/miami.png",
    "size": 35186,
    "fullPath": "photos/miami.png",
    "storageClass": "STANDARD",
    "lastModified": "Mon Mar 21 14:15:05 EDT 2022",
    "displaySize": {
      "value": "34.4",
      "unitKey": "units.filesizes.KB"
    },
    "contentType": "image/png",
    "eTag": "a8b886246bccda023fbb348731c1bd05",
    "isFolder": false,
    "bucketName": "bucket-root-brdje",
    "region": "us-east-1",
    "isVirtual": false
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/:regionName/:bucketName/:pathToObject</code>

Retrieve a list of objects inside a given folder inside a given bucket.

| Attributes                  | &nbsp;                                                                                                                                                                                                                                                                                                                                                            |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_string_           | The ID of the object, which is of the form `:regionName/:bucketName/:objectName`.                                                                                                                                                                                                                                                                                 |
| `name`<br/>_string_         | The name of the object.                                                                                                                                                                                                                                                                                                                                           |
| `fullPath`<br/>_string_     | The actual key of the object inside the bucket, which is represented as a full path.                                                                                                                                                                                                                                                                              |
| `size`<br/>_integer_        | The size of the object in bytes.                                                                                                                                                                                                                                                                                                                                  |
| `storageClass`<br/>_string_ | The type of storage class on the object.                                                                                                                                                                                                                                                                                                                          |
| `lastModified`<br/>_string_ | The date the object was last updated.                                                                                                                                                                                                                                                                                                                             |
| `displaySize`<br/>_string_  | The size of the object represented as an object in either KB, MB, or GB.                                                                                                                                                                                                                                                                                          |
| `contentType`<br/>_string_  | The type of file.                                                                                                                                                                                                                                                                                                                                                 |
| `eTag`<br/>_string_         | The eTag of the object generated by S3 during initial upload.                                                                                                                                                                                                                                                                                                     |
| `isFolder`<br/>_boolean_    | Boolean value denoting whether the object acts as a folder. This is always true when the `fullPath` attribute ends with a '/' character.                                                                                                                                                                                                                          |
| `bucketName`<br/>_string_   | The name of the bucket the object exists within.                                                                                                                                                                                                                                                                                                                  |
| `region`<br/>_string_       | The name of the region the object exists within.                                                                                                                                                                                                                                                                                                                  |
| `isVirtual`<br/>_boolean_   | Boolean value denoting whether the folder is virtual. If true there exists no object named `:folderName/`, and the folder exists only as a part of a complete object path (`:folderName/:objectName`). If false, there exists a key in the bucket named ‘{folderName}/’. If the query parameter `nested = true`, the request will not return any virtual folders. |

<!-------------------- Upload Object -------------------->

#### Upload Object

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/operation/upload" \
   --form operation=upload \
   --form entityType=objects \
   --form serviceConnectionId=connection_id \
   --form environmentId=environment_id \
   --form filename=file_size \
   --form bucketName=bucket_name \
   --form regionName=region_name \
   --form file=path_to_file
```

> Request body examples as Multipart Form:

```json
operation: upload
entityType: objects
serviceConnectionId: connection_id
environmentId: environment_id
filename: file_size
bucketName: bucket_name
regionName: region_name
file: path_to_file
```

> The above command returns a JSON structured like this:

```json
{
  "files": [
    {
      "name": "filename.png",
      "size": 93240,
      "status": "success"
    }
  ]
}
```

<code>POST /api/v2/services/operations/upload</code>

Upload a file to a bucket.

| Required                           | &nbsp;                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------------- |
| `operation`<br/>_string_           | The type of operation to execute, in this case `upload`.                              |
| `entityType`<br/>_string_          | The entityType, in this case `objects`.                                               |
| `serviceConnectionId`<br/>_string_ | The ID tied to the related service connection.                                        |
| `environmentId`<br/>_string_       | The ID tied to the related environment.                                               |
| `bucketName`<br/>_string_          | The name of the bucket to upload the file to.                                         |
| `regionName`<br/>_string_          | The name of the region to upload the file to.                                         |
| `:fileName`<br/>_long_             | Key should be the name of the file and value should be the size of the file in bytes. |
| `file`<br/>_string_                | The path to the file. This **must** be the last parameter in the form.                |

| Attributes            | &nbsp;                                         |
| --------------------- | ---------------------------------------------- |
| `name`<br/>_string_   | The name of the file uploaded.                 |
| `size`<br/>_integer_  | The size of the file uploaded.                 |
| `status`<br/>_string_ | String indicating the status of the operation. |

<!-------------------- DOWNLOAD AN OBJECT -------------------->

#### Download Object

```shell
curl --request GET \
  -H "MC-Api-Key: your_api_key" \
  "https://portal.coxedge.com/api/v2/services/operations/:service_connection_id/download?bucketName=akc-buck&regionName=us-east-1&id=us-east-1/akc-buck/api123.png&entityType=objects&operation=download&environmentId=97430433-875c-4ba5-8c57-90a051a52729"
```

<code>GET rest/services/operations/:service_connection_id/download?id=:regionName/:bucketName/:objectPath&entityType=objects&operation=download&environmentId:environmentId</code>

Download an object from a bucket.

> The above command returns the binary of the file downloaded.

| Required Query Parameters    | &nbsp;                                                                                        |
| ---------------------------- | --------------------------------------------------------------------------------------------- |
| `id`<br/>_string_            | The ID of the object to download, which is of the form ":regionName/:bucketName/:objectName". |
| `entityType`<br/>_string_    | The type of entity to download. In this case `objects`.                                       |
| `environmentId`<br/>_string_ | The ID of environment which owns the object.                                                  |

<!-------------------- DELETE AN OBJECT -------------------->

#### Delete Object

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/:regionName/:bucketName/:pathToObject/?operation=delete"
```

> Request body examples:

```json
{
  "id": "ap-south-1/bucket-root-dwyak/images/"
}
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
  "taskStatus": "PENDING"
}
```

<code>DELETE /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/:regionName/:bucketName/:fullPath</code>

Delete an object from a bucket.

| Attributes                 | &nbsp;                                                |
| -------------------------- | ----------------------------------------------------- |
| `taskId` <br/>_string_     | The [task ID](#tasks) related to the object deletion. |
| `taskStatus` <br/>_string_ | The status of the operation.                          |

<!-------------------- RENAME AN OBJECT -------------------->

#### Rename Object

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/:regionName/:bucketName/:pathToObject/?operation=rename"
```

Rename an object in a bucket.

> Request body examples:

```json
{
  "name": "newFilePath.png"
}
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
  "taskStatus": "PENDING"
}
```

<code>POST /services/operation/rename <a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/:regionName/:bucketName/:fullPath?&operation=rename</code>

| Required             | &nbsp;                      |
| -------------------- | --------------------------- |
| `name` <br/>_string_ | The new name of the object. |

| Attributes                 | &nbsp;                                                |
| -------------------------- | ----------------------------------------------------- |
| `taskId` <br/>_string_     | The [task ID](#tasks) related to the object renaming. |
| `taskStatus` <br/>_string_ | The status of the operation.                          |

<!-------------------- ADD FOLDER -------------------->

#### Add Folder

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/?bucketName=bucketOne&regionName=regionOne&operation=add_folder"
```

Add a folder to a bucket.

> Request body examples:

```json
{
  "name": "newFolderName"
}
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
  "taskStatus": "PENDING"
}
```

<code>POST /services/operation/rename <a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/?bucketName=:bucketName&regionName=:regionName&operation=add_folder</code>

| Required             | &nbsp;                                                                       |
| -------------------- | ---------------------------------------------------------------------------- |
| `name` <br/>_string_ | The name of the folder. Can contain '/' characters to create nested folders. |

| Attributes                 | &nbsp;                                                |
| -------------------------- | ----------------------------------------------------- |
| `taskId` <br/>_string_     | The [task ID](#tasks) related to the folder creation. |
| `taskStatus` <br/>_string_ | The status of the operation.                          |

| Required Query Parameters  | &nbsp;                                          |
| -------------------------- | ----------------------------------------------- |
| `bucketName` <br/>_string_ | The name of the bucket to create the folder in. |
| `regionName` <br/>_string_ | The name of the region the bucket exists in.    |

| Optional Query Parameters | &nbsp;                                                                                                   |
| ------------------------- | -------------------------------------------------------------------------------------------------------- |
| `prefix` <br/>_string_    | The folder path to create the folder in. If omitted, a folder will be created in the root of the bucket. |

<!-------------------- RENAME FOLDER -------------------->

#### Rename Folder

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/:regionName/:bucketName/:pathToObject?&operation=rename_folder"
```

Renames a folder in a bucket. This operation renames all objects inside the folder to use the new folder name and their full path. To accomplish this, all objects must first be copied with a new key, then deleted. This operation can take an extended amount of time depending on the amount and size of objects inside the folder.

> Request body examples:

```json
{
  "name": "newFolderName"
}
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/:regionName/:bucketName/:folderFullPath?&operation=rename_folder</code>

| Required             | &nbsp;                                                                           |
| -------------------- | -------------------------------------------------------------------------------- |
| `name` <br/>_string_ | The new name of the folder. Can contain '/' characters to create nested folders. |

| Attributes                 | &nbsp;                                                |
| -------------------------- | ----------------------------------------------------- |
| `taskId` <br/>_string_     | The [task ID](#tasks) related to the folder renaming. |
| `taskStatus` <br/>_string_ | The status of the operation.                          |

<!-------------------- GENERATE URL -------------------->

#### Generate URL

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/purestorage/test-env/objects/:regionName/:bucketName/:pathToObject?&operation=generate_url"
```

Generates a presigned URL. Must specify a limit in the request which denotes the amount of time (in minutes) until the URL expires. Minimum is 1 minute and maximum is 10080 minutes.

> Request body examples:

```json
{
  "limit": "60"
}
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
  "taskStatus": "SUCCESS"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/objects/:regionName/:bucketName/:objectFullPath?&operation=generate_url</code>

| Required               | &nbsp;                                               |
| ---------------------- | ---------------------------------------------------- |
| `limit` <br/>_integer_ | The length (in minutes) the link will be active for. |

| Attributes                 | &nbsp;                                               |
| -------------------------- | ---------------------------------------------------- |
| `taskId` <br/>_string_     | The [task ID](#tasks) related to the URL generation. |
| `taskStatus` <br/>_string_ | The status of the operation.                         |
