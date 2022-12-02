## Devices

Allows you to purchase, deploy, and manage your Bare Metal machines and network resources

Deploy and manage your Bare Metal devices.

<!-------------------- LIST Bare Metal Devices -------------------->

### List Devices

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/devices"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "id": "23303",
      "servicePlan": "149874",
      "name": "tester02.coxedge.com",
      "deviceType": "Dedicated Server 1U",
      "primaryIp": "91.191.214.66",
      "status": "active",
      "monitorsTotal": 0,
      "monitorsUp": 0,
      "ipmiAddress": "10.6.91.160",
      "powerStatus": "ON",
      "tags": [],
      "hostname": "tester02.coxedge.com",
      "location": {
        "facility": "DAL1",
        "facility_title": "Dallas 1"
      }
    },
    {
      "id": "13547",
      "servicePlan": "149588",
      "name": "testcc01.coxedge.com",
      "deviceType": "Dedicated Server 1U",
      "primaryIp": "66.165.229.26",
      "status": "active",
      "monitorsTotal": 0,
      "monitorsUp": 0,
      "ipmiAddress": "10.4.66.21",
      "powerStatus": "ON",
      "tags": ["ultra-wp"],
      "hostname": "testcc01.coxedge.com",
      "location": {
        "facility": "LAX2",
        "facility_title": "Los Angeles 2"
      }
    }
  ],
  "metadata": {
    "recordCount": 2
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/devices</code>

Retrieve a list of all devices in a given [environment](#administration-environments).

| Attributes                             | &nbsp;                                                                                       |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| `id`<br/>_string_                      | The unique ID of the device.                                                                 |
| `servicePlan`<br/>_string_             | The unique ID of the service associated with this device.                                    |
| `name`<br/>_string_                    | User given custom name.                                                                      |
| `deviceType` <br/>_string_             | Generic description of device. Usually type and rack unit size.                              |
| `primaryIp` <br/>_string_              | The first assigned public IP for accessing this device.                                      |
| `status` <br/>_string_                 | active/inactive                                                                              |
| `monitorsTotal`<br>_int_               | Total # device monitors.                                                                     |
| `monitorsUp`<br/>_int_                 | Number of passing device monitors.                                                           |
| `ipmiAddress` <br/>_string_            | IP address for IPMI connection. Requires you to whitelist your current IP or be on IPMI VPN. |
| `powerStatus` <br/>_string_            | ON/OFF                                                                                       |
| `tags`<br/>_Array[string]_             | List of all user set device tags.                                                            |
| `hostname` <br/>_string_               | A FQDN for the device. For example: example.hivelocity.net.                                  |
| `location.facility` <br/>_string_      | A facility code. For example NYC1.                                                           |
| `location.facility_title`<br/>_string_ | A facility name.                                                                             |

<!-------------------- RETRIEVE A DEVICE -------------------->

### Retrieve a device

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/devices/13547"
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "id": "23303",
    "servicePlan": "149874",
    "name": "tester02.coxedge.com",
    "deviceType": "Dedicated Server 1U",
    "primaryIp": "91.191.214.66",
    "status": "active",
    "monitorsTotal": 0,
    "monitorsUp": 0,
    "monitors": "0/0 (UP)",
    "ipmiAddress": "10.6.91.160",
    "powerStatus": "ON",
    "tags": [],
    "hostname": "tester02.coxedge.com",
    "location": {
      "facility": "DAL1"
    },
    "deviceDetail": {
      "processor": "2 x 2.2GHz 10-Core 4210 Xeon Silver",
      "primaryHardDrive": "960GB SSD",
      "memory": "64 GB",
      "operatingSystem": "Ubuntu 18.x",
      "bandwidth": "100 TB on 1Gbps port",
      "internalNetwork": "1 Gbps",
      "ddos": "Filtering Edge of Network System (FENS)",
      "raidSetUp": "Software RAID 1",
      "nextRenew": "Dec 1 2022",
      "deviceIPDetail": {
        "primaryIp": "91.191.214.64/29",
        "description": "Primary Assignment",
        "gatewayIp": "91.191.214.65",
        "subnetMask": "255.255.255.248",
        "usableIps": [
          "91.191.214.66",
          "91.191.214.67",
          "91.191.214.68",
          "91.191.214.69",
          "91.191.214.70"
        ]
      }
    },
    "deviceInitialPassword": {
      "lockerUrl": "https://locker.hivelocity.net/155f282feba1ccd450ae9f9dd7ddb394c8fc90dd/decrypt/",
      "password": "!rfl7qQ3p&Rc7A15vAyI",
      "passwordReturnsUntil": 4,
      "passwordExpires": "4",
      "port": 22,
      "user": "ubuntu"
    },
    "deviceIPs": {
      "subnet": "91.191.214.64/29",
      "netmask": "255.255.255.248",
      "usableIps": [
        "91.191.214.65",
        "91.191.214.66",
        "91.191.214.67",
        "91.191.214.68",
        "91.191.214.69",
        "91.191.214.70"
      ]
    }
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/devices/:id</code>

Retrieve a device in a given [environment](#administration-environments).

| Attributes                                                   | &nbsp;                                                                                                                                   |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_string_                                            | The unique ID of the device.                                                                                                             |
| `servicePlan`<br/>_string_                                   | The unique ID of the service associated with this device.                                                                                |
| `name`<br/>_string_                                          | User given custom name.                                                                                                                  |
| `deviceType` <br/>_string_                                   | Generic description of device. Usually type and rack unit size.                                                                          |
| `primaryIp` <br/>_string_                                    | The first assigned public IP for accessing this device.                                                                                  |
| `status` <br/>_string_                                       | active/inactive                                                                                                                          |
| `monitorsTotal`<br>_int_                                     | Total # device monitors.                                                                                                                 |
| `monitorsUp`<br/>_int_                                       | Number of passing device monitors.                                                                                                       |
| `monitors`<br/>_string_                                      | monitors.                                                                                                                                |
| `ipmiAddress` <br/>_string_                                  | IP address for IPMI connection. Requires you to whitelist your current IP or be on IPMI VPN.                                             |
| `powerStatus` <br/>_string_                                  | ON/OFF                                                                                                                                   |
| `tags`<br/>_Array[string]_                                   | List of all user set device tags.                                                                                                        |
| `hostname` <br/>_string_                                     | A FQDN for the device. For example: example.hivelocity.net.                                                                              |
| `location.facility` <br/>_string_                            | A facility code. For example NYC1.                                                                                                       |
| `deviceDetail.processor` <br/>_string_                       |                                                                                                                                          |
| `deviceDetail.memory` <br/>_string_                          |                                                                                                                                          |
| `deviceDetail.operatingSystem` <br/>_string_                 |                                                                                                                                          |
| `deviceDetail.bandwidth` <br/>_string_                       |                                                                                                                                          |
| `deviceDetail.internalNetwork` <br/>_string_                 |                                                                                                                                          |
| `deviceDetail.ddos` <br/>_string_                            |                                                                                                                                          |
| `deviceDetail.raidSetUp` <br/>_string_                       |                                                                                                                                          |
| `deviceDetail.nextRenew` <br/>_string_                       |                                                                                                                                          |
| `deviceDetail.deviceIPDetail.primaryIp` <br/>_string_        |                                                                                                                                          |
| `deviceDetail.deviceIPDetail.description` <br/>_string_      |                                                                                                                                          |
| `deviceDetail.deviceIPDetail.gatewayIp` <br/>_string_        |                                                                                                                                          |
| `deviceDetail.deviceIPDetail.subnetMask` <br/>_string_       |                                                                                                                                          |
| `deviceDetail.deviceIPDetail.usableIps` <br/>_Array[string]_ |                                                                                                                                          |
| `deviceInitialPassword.lockerUrl` <br/>_int_                 | Link to encrypted locker containing password for initial ssh access. Locker contents be expired from api 7 days after initial provision. |
| `deviceInitialPassword.password` <br/>_int_                  | Password for initial ssh access. Will expire from api 7 days after initial provision.                                                    |
| `deviceInitialPassword.passwordReturnsUntil` <br/>_int_      | Date password will expire from API.                                                                                                      |
| `deviceInitialPassword.passwordExpires` <br/>_string_        | Number of days password remains / Expired                                                                                                |
| `deviceInitialPassword.port` <br/>_int_                      | Port for initial ssh access.                                                                                                             |
| `deviceInitialPassword.user` <br/>_int_                      | User for initial ssh access.                                                                                                             |
| `deviceIPs.subnet` <br/>_string_                             |                                                                                                                                          |
| `deviceIPs.netmask` <br/>_string_                            |                                                                                                                                          |
| `deviceIPs.usableIps` <br/>_Array[string]_                   | A broadcast & gateway is reserved in each subnet. To use all IPs route this assignment to an IP in another assignment.                   |

|

<!-------------------- CREATE A DEVICE -------------------->

### Create a device

```shell
curl -X POST \
    -H "MC-Api-Key: your_api_key" \
    -d "request_body" \
    "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-create-request"
```

> Request body example for a device:

```json
{
  "quantity": 1,
  "locationName": "DAL1",
  "hasUserData": true,
  "hasSshData": false,
  "productOptionId": 143006,
  "productId": "582",
  "osName": "Ubuntu 18.x",
  "server": [
    {
      "hostname": "example.coxedge.com"
    }
  ],
  "sshKey": "",
  "sshKeyName": "",
  "sshKeyId": "746"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-create-request</code>

Create a new device in a given [environment](#administration-environments).

| Required                       | &nbsp;                                                                                                               |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| `quantity` <br/>_int_          | Number of device creating.                                                                                           |
| `locationName`<br/>_string_    | A facility code. For example NYC1.                                                                                   |
| `hasUserData`<br/>_boolean_    | True if we passing user data.                                                                                        |
| `hasSshData`<br/>_boolean_     | True if we passing SSH key.                                                                                          |
| `productOptionId`<br/>_int_    | The unique ID of the desired product option.                                                                         |
| `productId`<br/>_string_       | The unique ID of the desired product to provision.                                                                   |
| `osName`<br/>_string_          | The name of the Operating System to provision on this device. Must match name of an operating system product option. |
| `server`<br/>_Array[object]_   | List of servers.                                                                                                     |
| `server.hostname`<br/>_string_ | A FQDN for the device. For example: example.coxedge.com                                                              |

| Optional                   | &nbsp;                         |
| -------------------------- | ------------------------------ |
| `sshKey`<br/>_string_      | SSH key value.                 |
| `sshKeyName` <br/>_string_ | Name for newly adding SSH key. |
| `sshKeyId`<br/>_string_    | The unique ID of the SSH key.  |

<!-------------------- DELETE A DEVICE -------------------->

### Delete a device

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/devices/11296?operation=delete"
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "ef70cafa-0544-4709-a66a-c68595ee105a",
  "taskStatus": "SUCCESS"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/devices/:id?operation=delete</code>

Delete a device in a given [environment](#administration-environments).

| Attributes                 | &nbsp;                                        |
| -------------------------- | --------------------------------------------- |
| `taskId` <br/>_string_     | The task id related to the workload deletion. |
| `taskStatus` <br/>_string_ | The status of the operation.                  |

### Edit device hostname

```shell
curl -X PATCH \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-setting/13547"
```

> Request body example:

```json
{
  "hostname": "example.coxedge.com"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>PATCH /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-setting/:id</code>

Edit device hostname in a given [environment](#administration-environments).

| Required                | &nbsp;           |
| ----------------------- | ---------------- |
| `hostname`<br/>_string_ | Device hostname. |

### Edit device name

```shell
curl -X PATCH \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-setting/13547"
```

> Request body example:

```json
{
  "name": "example device name"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>PATCH /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-setting/:id</code>

Edit device name in a given [environment](#administration-environments).

| Required            | &nbsp;       |
| ------------------- | ------------ |
| `name`<br/>_string_ | Device name. |

### Edit device tag

```shell
curl -X PATCH \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-setting/13547"
```

> Request body example:

```json
{
  "tags": ["test-tag-1", "test-tag-1"]
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>PATCH /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-setting/:id</code>

Edit device tag in a given [environment](#administration-environments).

| Required                   | &nbsp;                 |
| -------------------------- | ---------------------- |
| `tags`<br/>_Array[string]_ | User specified values. |

### Device power on

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/devices/13547?operation=device-on"
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/devices/:id?operation=device-on</code>

Edit device power on in a given [environment](#administration-environments).

### Device power off

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/devices/13547?operation=device-off"
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/devices/:id?operation=device-off</code>

Edit device power off in a given [environment](#administration-environments).

### Get device charts

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-charts?id=13547"
```

> The above commands return a JSON structured like this:

```json
{
  "data": [
    {
      "id": "13547",
      "filter": "DAY",
      "graphImage": "",
      "interfaces": "eth0",
      "switchId": "13526"
    },
    {
      "filter": "WEEK",
      "graphImage": "",
      "interfaces": "eth0",
      "switchId": "13526"
    },
    {
      "filter": "MONTH",
      "graphImage": "",
      "interfaces": "eth0",
      "switchId": "13526"
    }
  ],
  "metadata": {
    "recordCount": 3
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-charts?id=:id</code>

Get device charts in a given [environment](#administration-environments).

| Query Params      | &nbsp;                  |
| ----------------- | ----------------------- |
| `id`<br/>_string_ | The unique ID of device |

### Get device custom charts

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-charts/13547?operation=custom"
```

> Request body example:

```json
{
  "endDate": "1668407548",
  "startDate": "1668184639"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-charts/id?operation=custom</code>

Get device custom charts in a given [environment](#administration-environments).

| Required                  | &nbsp;                                              |
| ------------------------- | --------------------------------------------------- |
| `endDate`<br/>_string_    | Start Time of Custom Time Period. (Unix Epoch Time) |
| `startDate` <br/>_string_ | End Time of Custom Time Period (Unix Epoch Time)    |

### Get device sensors

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-sensors-list?id=13547"
```

> The above commands return a JSON structured like this:

```json
{
  "data": [
    {
      "id": "13547",
      "ipmiField": "Manufacture Name",
      "ipmiValue": "Supermicro (10876)"
    },
    {
      "ipmiField": "IPMI Version",
      "ipmiValue": "2.0"
    },
    {
      "ipmiField": "Firmware Revision",
      "ipmiValue": "1.22"
    },
    {
      "ipmiField": "IPMI IP Address",
      "ipmiValue": "10.4.66.21"
    },
    {
      "ipmiField": "Device Tags",
      "ipmiValue": "[ultra-wp]"
    },
    {
      "ipmiField": "Username",
      "ipmiValue": "hv_WGBSO"
    },
    {
      "ipmiField": "Password",
      "ipmiValue": "K7Ta10E1gFk"
    },
    {
      "ipmiField": "Sensors",
      "ipmiValue": "[{\"group\":\"Temperature\",\"name\":\"CPU Temp\",\"reading\":\"25.0\"},{\"group\":\"Temperature\",\"name\":\"PCH Temp\",\"reading\":\"30.0\"},{\"group\":\"Temperature\",\"name\":\"System Temp\",\"reading\":\"24.0\"},{\"group\":\"Temperature\",\"name\":\"Peripheral Temp\",\"reading\":\"29.0\"},{\"group\":\"Temperature\",\"name\":\"VcpuVRM Temp\",\"reading\":\"27.0\"},{\"group\":\"Temperature\",\"name\":\"M2NVMeSSD Temp1\",\"reading\":\"null\"},{\"group\":\"Temperature\",\"name\":\"M2NVMeSSD Temp2\",\"reading\":\"null\"},{\"group\":\"Temperature\",\"name\":\"DIMMA1 Temp\",\"reading\":\"null\"},{\"group\":\"Temperature\",\"name\":\"DIMMA2 Temp\",\"reading\":\"null\"},{\"group\":\"Temperature\",\"name\":\"DIMMB1 Temp\",\"reading\":\"null\"},{\"group\":\"Temperature\",\"name\":\"DIMMB2 Temp\",\"reading\":\"23.0\"},{\"group\":\"Fan\",\"name\":\"FAN1\",\"reading\":\"null\"},{\"group\":\"Fan\",\"name\":\"FAN2\",\"reading\":\"1400.0\"},{\"group\":\"Fan\",\"name\":\"FAN3\",\"reading\":\"null\"},{\"group\":\"Fan\",\"name\":\"FAN4\",\"reading\":\"null\"},{\"group\":\"Fan\",\"name\":\"FANA\",\"reading\":\"null\"},{\"group\":\"Fan\",\"name\":\"FANB\",\"reading\":\"null\"},{\"group\":\"Voltage\",\"name\":\"12V\",\"reading\":\"12.19\"},{\"group\":\"Voltage\",\"name\":\"5VCC\",\"reading\":\"4.94\"},{\"group\":\"Voltage\",\"name\":\"3.3VCC\",\"reading\":\"3.32\"},{\"group\":\"Battery\",\"name\":\"VBAT\",\"reading\":\"null\"},{\"group\":\"Voltage\",\"name\":\"Vcpu\",\"reading\":\"0.02\"},{\"group\":\"Voltage\",\"name\":\"Vdimm\",\"reading\":\"1.2\"},{\"group\":\"Voltage\",\"name\":\"VCC_SA\",\"reading\":\"1.05\"},{\"group\":\"Voltage\",\"name\":\"5VSB\",\"reading\":\"4.96\"},{\"group\":\"Voltage\",\"name\":\"3.3VSB\",\"reading\":\"3.3\"},{\"group\":\"Voltage\",\"name\":\"VCC_IO\",\"reading\":\"0.95\"},{\"group\":\"Voltage\",\"name\":\"1.8V_PCH\",\"reading\":\"1.78\"},{\"group\":\"Voltage\",\"name\":\"1.2V_BMC\",\"reading\":\"1.2\"},{\"group\":\"Voltage\",\"name\":\"1.05V_PCH\",\"reading\":\"1.05\"},{\"group\":\"Physical Security\",\"name\":\"Chassis Intru\",\"reading\":\"null\"}]"
    }
  ],
  "metadata": {
    "recordCount": 8
  }
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-sensors-list?id=:id</code>

Get device custom charts in a given [environment](#administration-environments).

| Query Params      | &nbsp;                  |
| ----------------- | ----------------------- |
| `id`<br/>_string_ | The unique ID of device |

### Connect to IPMI

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-sensors-list/13547?operation=connect"
```

> Request body example:

```json
{
  "customIP": "192.168.1.44"
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-sensors-list/:id?operation=connect</code>

Connect device to IPMI in a given [environment](#administration-environments).

| Required                | &nbsp;     |
| ----------------------- | ---------- |
| `customIP`<br/>_string_ | IP address |

### Clear IPMI allowed list

```shell
curl -X POST \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-sensors-list/13547?operation=clear"
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-sensors-list/:id?operation=clear</code>

Clear IPMI alowed list of device in a given [environment](#administration-environments).

### Get Device IPs

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/baremetal/baremetal-test-env/device-ips-list?id=13547"
```

> The above commands return a JSON structured like this:

```json
{
  "data": [
    {
      "ipName": "Usable IP",
      "value": "66.165.229.25"
    },
    {
      "ipName": "Usable IP",
      "value": "66.165.229.26"
    },
    {
      "ipName": "Usable IP",
      "value": "66.165.229.27"
    },
    {
      "ipName": "Usable IP",
      "value": "66.165.229.28"
    },
    {
      "ipName": "Usable IP",
      "value": "66.165.229.29"
    },
    {
      "ipName": "Usable IP",
      "value": "66.165.229.30"
    }
  ],
  "metadata": {
    "recordCount": 6
  }
}
```

<code>POST /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/device-ips-list?id=:id</code>

Get device IPs in a given [environment](#administration-environments).

| Query Params      | &nbsp;                  |
| ----------------- | ----------------------- |
| `id`<br/>_string_ | The unique ID of device |
