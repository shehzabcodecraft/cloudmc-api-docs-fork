### Buckets

View and manage your buckets.

<!-------------------- GET buckets -------------------->

#### Get Buckets

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://cloudmc_endpoint/rest/services/aws/test-env/buckets"
```
> Request body example for a bucket:

```json
{
  "access": "private",
  "name": "bucketOne",
  "region": "us-east-1",
},
```

> The above command returns a JSON structured like this:

```json
{
    "data": [
        {
            "id": "us-east-1/bucketOne",
            "name": "bucketOne",
            "region": "us-east-1",
            "created": "Tue Mar 01 16:13:29 EST 2022",
            "url": "https://bucketOne.s3.amazonaws.com/"
        },
        {
            "id": "ap-south-1/bucketTwo",
            "name": "bucketTwo",
            "region": "ap-south-1",
            "created": "Fri Mar 04 16:20:29 EST 2022",
            "url": "https://bucketTwo.s3.amazonaws.com/"
        }
    ],
    "metadata": {
        "recordCount": 2
    }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/buckets</code>

Retrieve a list of all buckets from Amazon S3.

| Attributes                        | &nbsp;                                                                                                                                                                                                                   |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `id`<br/>*string*                 | The ID of the bucket, which is of the form ":regionName/:bucketName".                                                                                                                                                                                                  |
| `name`<br/>*string*               | The name of the bucket.                                                                                                                                                                                                |
| `region`<br/>*string*     | The region the bucket exists in.                                                                                                                                                     |
| `created`<br/>*string*            | The date the bucket was created.                                                                                                                                                                         |
| `url`<br/>*string*       | The full endpoint url used to make api calls on the bucket.                                                                                                                                                                                      

<!-------------------- CREATE A BUCKET -------------------->

#### Create Bucket

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://cloudmc_endpoint/rest/services/aws/test-env/buckets/"
```
> The above command returns a JSON structured like this:

```json
{
    "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
    "taskStatus": "SUCCESS"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/buckets/</code>

| Attributes                 | &nbsp;                                        |
|----------------------------|-----------------------------------------------|
| `taskId` <br/>*string*     | The task id related to the bucket creation. |
| `taskStatus` <br/>*string* | The status of the operation.                  |


<!-------------------- DELETE A BUCKET -------------------->

#### Delete Bucket

```shell
curl -X DELETE \
   -H "MC-Api-Key: your_api_key" \
   "https://cloudmc_endpoint/rest/services/aws/test-env/buckets/us-east-1/bucketOne"
```
> The above command returns a JSON structured like this:

```json
{
    "taskId": "30121175-926a-4fd2-991b-ff303ffdf905",
    "taskStatus": "PENDING"
}
```

<code>DELETE /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/buckets/:regionName/:bucketName</code>

| Attributes                 | &nbsp;                                        |
|----------------------------|-----------------------------------------------|
| `taskId` <br/>*string*     | The task id related to the bucket deletion. |
| `taskStatus` <br/>*string* | The status of the operation.                  |


