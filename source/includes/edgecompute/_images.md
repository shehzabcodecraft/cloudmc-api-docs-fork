## Images

StackPath Edge Computing makes use of images to deploy virtual machines within a workload. The image can be from StackPath default images or
a custom one. Only non-deprecated images are returned by default.

Deploy and manage your images.


<!-------------------- LIST IMAGES -------------------->

### List images

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/images"
```
> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "stackId": "a8050b2b-39eb-4929-bce5-1af42055903e",
      "id": "a8050b2b-39eb-4929-bce5-1af42055903e/centos7/v20201110",
      "slug": "stackpath-edge",
      "family": "centos7",
      "tag": "v20201110",
      "createdAt": "2020-11-10T20:33:32.609434Z",
      "description": "Image using centos7",
      "reference": "stackpath-edge/centos7:v20201110",
      "status": "READY"
    },
    {
      "stackId": "a8050b2b-39eb-4929-bce5-1af42055903e",
      "id": "a8050b2b-39eb-4929-bce5-1af42055903e/ubuntu/v20201110",
      "slug": "stackpath-edge",
      "family": "ubuntu",
      "tag": "v20201110",
      "createdAt": "2020-11-10T20:34:11.328575Z",
      "description": "Image using ubuntu",
      "reference": "stackpath-edge/ubuntu:v20201110",
      "status": "READY"
    }
  ],
  "metadata": {
    "recordCount": 2
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/images</code>

Retrieve a list of all images in a given [environment](#administration-environments).

Optional | &nbsp;
------ | -----------
`imageType`<br/>*string* | This query parameter can either be set to **default** to return the default StackPath images or **custom** to return the created custom images. Anything else will return all images.

Attributes | &nbsp;
------- | -----------
`id`<br/>*string* | An image's unique identifier. It is the combination of stackId/family/tag.
`stackId`<br/>*string* | The ID of the stack that an image belongs to.
`family`<br/>*string* | The family of the image.
`tag`<br/>*string* | The tag of the image.
`slug`<br/>*string* | A workload's programmatic name. Workload slugs are used to build its instances names.
`status`<br/>*string* | The status of the workload. It can be either READY, PENDING, PROCESSING, FAILED or IMAGE_STATUS_UNKNOWN.
`createdAt`<br/>*string* | Creation timestamp of the image.
`description`<br/>*string* | The description of the image.
`reference`<br/>*string* | The reference of the image.

<!-------------------- RETRIEVE AN IMAGE -------------------->

### Retrieve an image

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/images/a8050b2b-39eb-4929-bce5-1af42055903e/ubuntu/v20201110"
```
> The above command returns a JSON structured like this:

```json
{
  "data": {
    "stackId": "a8050b2b-39eb-4929-bce5-1af42055903e",
    "id": "a8050b2b-39eb-4929-bce5-1af42055903e/ubuntu/v20201110",
    "slug": "stackpath-edge",
    "family": "ubuntu",
    "tag": "v20201110",
    "createdAt": "2020-11-10T20:34:11.328575Z",
    "description": "test 2",
    "reference": "stackpath-edge/ubuntu:v20201110",
    "status": "READY"
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/images/:id</code>

Retrieve an image in a given [environment](#administration-environments).

Attributes | &nbsp;
------- | -----------
`id`<br/>*string* | An image's unique identifier. It is the combination of stackId/family/tag.
`stackId`<br/>*string* | The ID of the stack that an image belongs to.
`family`<br/>*string* | The family of the image.
`tag`<br/>*string* | The tag of the image.
`slug`<br/>*string* | A workload's programmatic name. Workload slugs are used to build its instances names.
`status`<br/>*string* | The status of the workload. It can be either READY, PENDING, PROCESSING, FAILED or IMAGE_STATUS_UNKNOWN.
`createdAt`<br/>*string* | Creation timestamp of the image.
`description`<br/>*string* | The description of the image.
`reference`<br/>*string* | The reference of the image.


<!-------------------- CREATE AN IMAGE -------------------->

#### Create a custom image

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/images"
```
> Request body example for creating a custom image:

```json
{
  "family": "Ubuntu",
  "tag": "v2021-01-01",
  "workloadId": "c23652ed-0f15-47cf-a9b8-63e1e3aacb3c",
  "instanceName": "w-john-ahd-wi-john-jsr-phx-0",
  "description": "Ubuntu OS v4"
}
```
> The above commands return a JSON structured like this:

```json
{
  "taskId": "1f64aefb-f980-400b-bc2d-5300376fa55e",
  "taskStatus": "PENDING"
}
```
<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/images</code>

Required| &nbsp;
------------------------| -----------
`family`<br/>*string* | The family name of the custom image.Family must consist of lower case alphanumeric characters or '-' and must begin and end with an alphanumeric character.
`tag`<br/>*string* | The tag of the image. A tag must be valid ASCII and may contain lowercase and uppercase letters, digits, underscores, periods and dashes. A tag must not start with a period or a dash and must contain a maximum of 128 characters.
`workloadId`<br/>*string* | The workloadId of the source workload the image will be created from. Only workloads of type VM are allowed
`instanceName`<br/>*string* | The name of one of the instance the create the image from. The name of the instance needs to be a valid instance of the workloadId provided.

Optional| &nbsp;
----------------------- | -----------
`description`<br/>*string* | The description of the custom image.


<!-------------------- DELETE AN IMAGE -------------------->

#### Delete a custom image
```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/images/1b932678-1038-4ab4-9fa4-c4c06e696e20"
```
> The above command returns a JSON structured like this:

```json
{
  "taskId": "ef70cafa-0544-4709-a66a-c68595ee105a",
  "taskStatus": "SUCCESS"
}
```

<code>DELETE /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/images/:id</code>

Delete an image in a given [environment](#administration-environments).

Attributes | &nbsp;
------- | -----------
`taskId` <br/>*string* | The task id related to the image deletion.
`taskStatus` <br/>*string* | The status of the operation.