## SSH Keys

Create and manage your SSH keys.

<!-------------------- LIST SSH Keys -------------------->

### Get SSH Keys

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/ssh-key"
```

> The above commands return a JSON structured like this:

```json
{
  "data": [
    {
      "id": "746",
      "publicKey": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCKuP1Oj6yjxeBOjuYZ3Sib1gP2RGUkGePRYUFfqWRKe+NsThV2dCw4kVY8YFPDYX6UQYHEH2K13m5k48cHJfN/1rdVwTR5jcjanzV3ye7VY72nExalCJXExQUM5EDR3ztf9IMfHzT+r7MaMLEvbhkC6gUlqBfm2olhgo+R03zOpzgQSH7k3bui8piVSOnriqiFApG3p/3pc/v90XUfIvfmUOWZRwlSSGCf82KJlhf0yHBzLkK2rPVzW2M+SkzplnhlbcP/u2T0sJBKwYsDBRvVWisFkyIYgIS/ZNPF5awDRfiukc+RfaD/HMWfTJyTdF3lu3VyvSFL7WnGi0aOzdr7",
      "name": "example"
    },
    {
      "id": "761",
      "publicKey": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCKuP1Oj6yjxeBOjuYZ3Sib1gP2RGUkGePRYUFfqWRKe+NsThV2dCw4kVY8YFPDYX6UQYHEH2K13m5k48cHJfN/1rdVwTR5jcjanzV3ye7VY72nExalCJXExQUM5EDR3ztf9IMfHzT+r7MaMLEvbhkC6gUlqBfm2olhgo+R03zOpzgQSH7k3bui8piVSOnriqiFApG3p/3pc/v90XUfIvfmUOWZRwlSSGCf82KJlhf0yHBzLkK2rPVzW2M+SkzplnhlbcP/u2T0sJBKwYsDBRvVWisFkyIYgIS/ZNPF5awDRfiukc+RfaD/HMWfTJyTdF3lu3VyvSFL7WnGi0aOzdr7",
      "name": "example"
    }
  ],
  "metadata": {
    "recordCount": 2
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/ssh-key</code>

Get SSH keys in a given [environment](#administration-environments).

### Retrieve SSH Key

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/ssh-key/746"
```

> The above commands return a JSON structured like this:

```json
{
  "data": {
    "id": "746",
    "publicKey": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCKuP1Oj6yjxeBOjuYZ3Sib1gP2RGUkGePRYUFfqWRKe+NsThV2dCw4kVY8YFPDYX6UQYHEH2K13m5k48cHJfN/1rdVwTR5jcjanzV3ye7VY72nExalCJXExQUM5EDR3ztf9IMfHzT+r7MaMLEvbhkC6gUlqBfm2olhgo+R03zOpzgQSH7k3bui8piVSOnriqiFApG3p/3pc/v90XUfIvfmUOWZRwlSSGCf82KJlhf0yHBzLkK2rPVzW2M+SkzplnhlbcP/u2T0sJBKwYsDBRvVWisFkyIYgIS/ZNPF5awDRfiukc+RfaD/HMWfTJyTdF3lu3VyvSFL7WnGi0aOzdr7",
    "name": "example"
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/ssh-key/:id</code>

Retrieve SSH key in a given [environment](#administration-environments).

### Create SSH Key

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/ssh-key"
```

> Request body example:

```json
{
  "name": "example",
  "publicKey": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCKuP1Oj6yjxeBOjuYZ3Sib1gP2RGUkGePRYUFfqWRKe+NsThV2dCw4kVY8YFPDYX6UQYHEH2K13m5k48cHJfN/1rdVwTR5jcjanzV3ye7VY72nExalCJXExQUM5EDR3ztf9IMfHzT+r7MaMLEvbhkC6gUlqBfm2olhgo+R03zOpzgQSH7k3bui8piVSOnriqiFApG3p/3pc/v90XUfIvfmUOWZRwlSSGCf82KJlhf0yHBzLkK2rPVzW2M+SkzplnhlbcP/u2T0sJBKwYsDBRvVWisFkyIYgIS/ZNPF5awDRfiukc+RfaD/HMWfTJyTdF3lu3VyvSFL7WnGi0aOzdr7"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "61f3cbac-946e-4ee0-a786-b8b5051c6ffb",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/ssh-key</code>

Create SSH key in a given [environment](#administration-environments).

| Attributes                | &nbsp;         |
| ------------------------- | -------------- |
| `name`<br/>_string_       | SSH key name   |
| `publicKey` <br/>_string_ | SSH public key |

### Delete SSH Key

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/ssh-key/761?operation=delete"
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "61f3cbac-946e-4ee0-a786-b8b5051c6ffb",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/ssh-key/:id?operation=delete</code>

Delete SSH key in a given [environment](#administration-environments).
