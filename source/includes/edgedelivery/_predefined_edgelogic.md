### Predefined Edge Logic

The predefined Edge Logic let you configure how Cox Edge responds to requests to your website. These predefined Edge Logic only work with domains that resolve to Cox Edge.

<!-------------------- LIST PREDEFINED EDGE LOGIC -------------------->

#### List predefined Edge Logic

```shell
curl -X GET \
   -H "MC-Api-Key: your_api_key" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/predefinededgerules/dcc2771d-a524-4f8c-a666-f699985d6961"
```
> The above command returns a JSON structured like this:

```json
{
  "data": {
    "allowEmptyReferrer": false,
    "forceWwwEnabled": true,
    "id": "c988cc62-24e7-4850-9a81-95f51af0a68e",
    "pseudoStreamingEnabled": true,
    "referrerList": [
      "cloudmc.io",
      "saas.cloudmc.io"
    ],
    "referrerProtectionEnabled": true,
    "robotsTxtEnabled": true,
    "robotsTxtFile": "User-agent: *\nDisallow:",
    "scopeId": "e9e48610-3ba6-471a-96f4-7cf18cb73455",
    "stackId": "1f259d02-db66-4a93-8402-a0725a00a02a",
    
  }
}
```

<code>GET /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/predefinededgerules/<a href="#edgedelivery-sites">:siteId</a></code>

Retrieve the configuration of all predefined Edge Logic in a given [environment](#administration-environments) within a site.

Attributes | &nbsp;
------- | -----------
`allowEmptyReferrer`<br/>*boolean* | Whether or not empty referrer is allowed.
`forceWwwEnabled`<br/>*boolean* | Whether or not redirecting every request to a www subdomain is enabled.
`id`<br/>*UUID* | This ID is same as the siteId to which the predefined Edge Logic belong.
`pseudoStreamingEnabled`<br/>*boolean* | Whether or not seeking random locations within MP4 or FLV files without downloading the entire video is enabled.
`referrerList`<br/>*Array[string]* | The list of domains authorized to access content from the site's root scope. Wildcards can be used to specify multiple websites hosted on the same domain.
`referrerProtectionEnabled`<br/>*boolean* | Whether or not referrer protection is enabled. This rule is used to allow only requests whose referrer header matches a URL that you specified.
`robotsTxtEnabled`<br/>*boolean* | Whether or not custom robot.txt support is enabled. This rule is used to configure which pages or files search engine crawlers can or cannot index from the site.
`robotsTxtFile`<br/>*string* | This field represents the robots.txt file contents. `NOTE:` When you first enable the `robotsTxtEnabled` rule, by default, the robots.txt will populate with a rule to disallow all indexing for CDN content. Any change made with this rule will override the contents of the robots.txt file on origin server.
`scopeId`<br/>*UUID* | The ID of the CDN site's root scope that the predefined rules belongs to.
`stackId`<br/>*UUID* | The ID of the stack that the predefined rules belong to.

<!-------------------- EDIT PREDEFINED EDGE LOGIC  -------------------->

#### Edit a predefined Edge Logic

```shell
curl -X PATCH \
   -H "MC-Api-Key: your_api_key" \
   -d "request_body" \
   "https://portal.coxedge.com/api/v2/services/edge-services/test-area/predefinededgerules/dcc2771d-a524-4f8c-a666-f699985d6961"
```

> Request body example:

```json
{
  "allowEmptyReferrer": true,
  "forceWwwEnabled": true,
  "pseudoStreamingEnabled": true,
  "referrerList": [
    "cloudmc.com",
    "saas.cloudmc.com"
  ],
  "referrerProtectionEnabled": true,
  "robotsTxtEnabled": true,
  "robotsTxtFile": "User-agent: *\nDisallow:",
}
```

> The above commands return a JSON structured like this:

```json
{
  "taskId": "7135ae25-8488-4bc5-a289-285c84a00a84",
  "taskStatus": "PENDING"
}
```
<code>PATCH /services/<a href="#administration-service-connections">:service_code</a>/<a href="#administration-environments">:environment_name</a>/predefinededgerules/<a href="#stackpath-sites">:siteId</a></code>


Optional| &nbsp;
------------------------| -----------
`allowEmptyReferrer`<br/>*boolean* | Whether or not empty referrer is allowed.
`forceWwwEnabled`<br/>*boolean* | Whether or not redirecting every request to a www subdomain is enabled.
`pseudoStreamingEnabled`<br/>*boolean* | Whether or not seeking random locations within MP4 or FLV files without downloading the entire video is enabled.
`referrerList`<br/>*Array[string]* | The list of domains authorized to access content from the site's root scope. Wildcards can be used to specify multiple websites hosted on the same domain.
`referrerProtectionEnabled`<br/>*boolean* | Whether or not referrer protection is enabled. This rule is used to allow only requests whose referrer header matches a URL that you specified.
`robotsTxtEnabled`<br/>*boolean* | Whether or not custom robot.txt support is enabled.
`robotsTxtFile`<br/>*string* | This field represents the robots.txt file contents. `NOTE:` To update the `robotsTxtFile` content, the `robotsTxtEnabled` flag should be included in the request payload.