## Applied Pricing Discounts

The discount allows the assignment of a percentage discount or credit to an applied pricing.

<!-------------------- LIST APPLIED PRICING DISCOUNTS -------------------->

### List applied pricing discounts

`GET /applied_pricings/:applied_pricing_id/discounts?type=:type`

Retrieve the list of discounts associated with an applied pricing.

```shell
# Retrieve applied pricing discount list
curl "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts?type=PERCENTAGE" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "applyToNewCustomersOnly": true,
      "discountedProducts": {},
      "durationDays": 60,
      "type": "PERCENTAGE",
      "packageDiscount": 20.0,
      "discountScope": "ALL_PRODUCTS",
      "isDeactivated": true,
      "discountedCategories": {},
      "name": {
        "en": "Summer Discount",
        "fr": "Réduction Estival"
      },
      "id": "18db7bc6-8be1-48bb-bab1-77a7d696fa3b",
      "appliedPricing": {
        "id": "efd32752-c6f2-45cf-b494-cc6be8a45845"
      },
      "startDate": "2021-07-20T15:57:16.132Z",
      "status": "CURRENT"
    }
  ]
}
```

| Optional Query Parameters | &nbsp;                                                                 |
| ------------------------- | ---------------------------------------------------------------------- |
| `type`<br/>_enum_         | The type of the discount. It could be either "PERCENTAGE" or "CREDIT". |

| Attributes                                         | &nbsp;                                                                                                                                                                             |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                                    | The UUID of the discount.                                                                                                                                                          |
| `discountedProducts`<br/>_Map[UUID, BigDecimal]_   | A mapping of the desired priced product IDs and discounts. All pricing products specified will have the discount value applied to them.                                            |
| `durationDays`<br/>_integer_                       | Duration of the discount once it has been applied to a customer. If not provided the discount will last indefinitely, or until credit values are reached.                          |
| `type`<br/>_enum_                                  | The type of the discount. It could be either "PERCENTAGE" or "CREDIT".                                                                                                             |
| `packageDiscount`<br/>_BigDecimal_                 | The discount value that will be applied to all products within the applied pricing.                                                                                                |
| `discountScope`<br/>_enum_                         | The scope of the discount. It could be either "ALL_PRODUCTS", "CATEGORIES" or "PRODUCTS".                                                                                          |
| `isDeactivated`<br/>_boolean_                      | Whether or not the discount is deactivated. Defaults to false.                                                                                                                     |
| `discountedCategories`<br/>_Map[UUID, BigDecimal]_ | A mapping between category IDs and discount values. All pricing products within a category will have the discount value applied to them.                                           |
| `name`<br/>_Map[String, String]_                   | The name translations of the discount.                                                                                                                                             |
| `appliedPricing`<br/>_Object_                      | The applied pricing being discounted.                                                                                                                                              |
| `appliedPricing.id`<br/>_UUID_                     | The UUID of the applied pricing.                                                                                                                                                   |
| `applyToNewCustomersOnly`<br/>_boolean_            | If true, the discount will only be applied to organizations created after the discount start date.                                                                                 |
| `startDate`<br/>_date_                             | The start date of the discount.                                                                                                                                                    |
| `cutoffDate`<br/>_date_                            | The date on which the discount will no longer be offered to customers who have not already received it. If not provided, the discount will always be offered after the start date. |
| `status`<br/>_enum_                                | The status of the discount. Possible values are: UPCOMING, CURRENT, ENDED.                                                                                                         |

<!-------------------- GET APPLIED PRICING DISCOUNT -------------------->

### Get applied pricing discount

`GET /applied_pricings/:applied_pricing_id/discounts/:id`

Retrieve a discount's details.

```shell
# Retrieve applied pricing discount list
curl "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts/18db7bc6-8be1-48bb-bab1-77a7d696fa3b" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "data": [
    {
      "applyToNewCustomersOnly": true,
      "discountedProducts": {},
      "durationDays": 60,
      "type": "PERCENTAGE",
      "packageDiscount": 20.0,
      "discountScope": "ALL_PRODUCTS",
      "isDeactivated": true,
      "discountedCategories": {},
      "name": {
        "en": "Summer Discount",
        "fr": "Réduction Estival"
      },
      "id": "18db7bc6-8be1-48bb-bab1-77a7d696fa3b",
      "appliedPricing": {
        "id": "efd32752-c6f2-45cf-b494-cc6be8a45845"
      },
      "startDate": "2021-07-20T15:57:16.132Z",
      "status": "CURRENT"
    }
  ]
}
```

| Attributes                                         | &nbsp;                                                                                                                                                                             |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`<br/>_UUID_                                    | The UUID of the discount.                                                                                                                                                          |
| `discountedProducts`<br/>_Map[UUID, BigDecimal]_   | A mapping of the desired priced product IDs and discounts. All pricing products specified will have the discount value applied to them.                                            |
| `durationDays`<br/>_integer_                       | Duration of the discount once it has been applied to a customer. If not provided the discount will last indefinitely, or until credit values are reached.                          |
| `type`<br/>_enum_                                  | The type of the discount. It could be either "PERCENTAGE" or "CREDIT".                                                                                                             |
| `packageDiscount`<br/>_BigDecimal_                 | The discount value that will be applied to all products within the applied pricing.                                                                                                |
| `discountScope`<br/>_enum_                         | The scope of the discount. It could be either "ALL_PRODUCTS", "CATEGORIES" or "PRODUCTS".                                                                                          |
| `isDeactivated`<br/>_boolean_                      | Whether or not the discount is deactivated. Defaults to false.                                                                                                                     |
| `discountedCategories`<br/>_Map[UUID, BigDecimal]_ | A mapping between category IDs and discount values. All pricing products within a category will have the discount value applied to them.                                           |
| `name`<br/>_Map[String, String]_                   | The name translations of the discount.                                                                                                                                             |
| `appliedPricing`<br/>_Object_                      | The applied pricing being discounted.                                                                                                                                              |
| `appliedPricing.id`<br/>_UUID_                     | The UUID of the applied pricing.                                                                                                                                                   |
| `applyToNewCustomersOnly`<br/>_boolean_            | If true, the discount will only be applied to organizations created after the discount start date.                                                                                 |
| `startDate`<br/>_date_                             | The start date of the discount.                                                                                                                                                    |
| `cutoffDate`<br/>_date_                            | The date on which the discount will no longer be offered to customers who have not already received it. If not provided, the discount will always be offered after the start date. |
| `status`<br/>_enum_                                | The status of the discount. Possible values are: UPCOMING, CURRENT, ENDED.                                                                                                         |

<!-------------------- CREATE APPLIED PRICING DISCOUNT -------------------->

### Create applied pricing discount

`POST /applied_pricings/:applied_pricing_id/discounts`

Create a new discount

```shell
# Creates a new applied pricing discount
curl -X POST "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts" \
   -H "MC-Api-Key: your_api_key"
```

> Request body example:

```json
{
  "name": {
    "en": "Summer Discount",
    "fr": "Réduction Estival"
  },
  "startDate": "2021-07-23T00:00:00.000Z",
  "type": "PERCENTAGE",
  "durationDays": 60,
  "discountedProducts": {},
  "discountedCategories": {
    "8cf73cc0-b86e-49b4-a102-6102894f7955": 2,
    "00358632-5c9a-4164-a9a9-df271a9c06a9": 22
  },
  "discountScope": "CATEGORIES",
  "cutoffDate": "2021-07-24T00:00:00.000Z",
  "applyToNewCustomersOnly": false
}
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "applyToNewCustomersOnly": false,
    "discountedProducts": {},
    "durationDays": 60,
    "type": "PERCENTAGE",
    "discountScope": "CATEGORIES",
    "discountedCategories": {
      "8cf73cc0-b86e-49b4-a102-6102894f7955": 2,
      "00358632-5c9a-4164-a9a9-df271a9c06a9": 22
    },
    "name": {
      "en": "Summer Discount",
      "fr": "Réduction Estival"
    },
    "id": "18db7bc6-8be1-48bb-bab1-77a7d696fa3b",
    "appliedPricing": {
      "id": "efd32752-c6f2-45cf-b494-cc6be8a45845"
    },
    "startDate": "2021-07-23T00:00:00.000Z",
    "cutoffDate": "2021-07-24T00:00:00.000Z"
  }
}
```

| Required                                           | &nbsp;                                                                                                                                                                                                                                                                                                |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`<br/>_Map[String, String]_                   | The name translations of the discount.                                                                                                                                                                                                                                                                |
| `type`<br/>_enum_                                  | The type of the discount. It can be either "PERCENTAGE" or "CREDIT".                                                                                                                                                                                                                                  |
| `startDate`<br/>_date_                             | The start date of the discount.                                                                                                                                                                                                                                                                       |
| `applyToNewCustomersOnly`<br/>_boolean_            | If true, the discount will only be applied to organizations created after the discount start date.                                                                                                                                                                                                    |
| `discountScope`<br/>_enum_                         | The scope of the discount. It can be either "ALL_PRODUCTS", "CATEGORIES" or "PRODUCTS".                                                                                                                                                                                                               |
| `packageDiscount`<br/>_BigDecimal_                 | The discount value that will be applied to all products within the applied pricing. Only required if the scope is "ALL_PRODUCTS". The value must be between (0,100] for a percentage discount and greater than 0 for a credit.                                                                        |
| `discountedCategories`<br/>_Map[UUID, BigDecimal]_ | A mapping between category IDs and discount values. All pricing products within a category will have the discount value applied to them. Required to be non-empty if scope is "CATEGORIES". All discount values must be between (0,100] for a percentage discount and greater than 0 for a credit.    |
| `discountedProducts`<br/>_Map[UUID, BigDecimal]_   | A mapping of the desired priced product IDs and discount values. All pricing products specified will have the discount value applied to them. Required to be non-empty if scope is "PRODUCTS". All discount values must be between (0,100] for a percentage discount and greater than 0 for a credit. |

| Optional                     | &nbsp;                                                                                                                                                                             |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cutoffDate`<br/>_date_      | The date on which the discount will no longer be offered to customers who have not already received it. If not provided, the discount will always be offered after the start date. |
| `durationDays`<br/>_integer_ | Duration of the discount once it has been applied to a customer. If not provided the discount will last indefinitely, or until credit values are reached.                          |

<!-------------------- EDIT APPLIED PRICING DISCOUNT -------------------->

### Edit applied pricing discount

`PUT /applied_pricings/:applied_pricing_id/discounts/:id`

Edit an existing discount that hasn't ended. Only the name and cutoff date can be edited for current discount. All fields can be edited for upcoming discounts.

```shell
# Edit an existing discount
curl -X PUT "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts/18db7bc6-8be1-48bb-bab1-77a7d696fa3b" \
   -H "MC-Api-Key: your_api_key"
```

> Request body example:

```json
{
  "name": {
    "en": "End of summer Discount",
    "fr": "Réduction estival fin d'été"
  },
  "durationDays": 60,
  "discountedProducts": {},
  "discountedCategories": {
    "8cf73cc0-b86e-49b4-a102-6102894f7955": 2,
    "00358632-5c9a-4164-a9a9-df271a9c06a9": 22
  },
  "discountScope": "CATEGORIES",
  "cutoffDate": "2021-08-24T00:00:00.000Z",
  "applyToNewCustomersOnly": false
}
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "applyToNewCustomersOnly": false,
    "discountedProducts": {},
    "durationDays": 60,
    "type": "PERCENTAGE",
    "discountScope": "CATEGORIES",
    "discountedCategories": {
      "8cf73cc0-b86e-49b4-a102-6102894f7955": 2,
      "00358632-5c9a-4164-a9a9-df271a9c06a9": 22
    },
    "name": {
      "en": "End of summer Discount",
      "fr": "Réduction estival fin d'été"
    },
    "id": "18db7bc6-8be1-48bb-bab1-77a7d696fa3b",
    "appliedPricing": {
      "id": "efd32752-c6f2-45cf-b494-cc6be8a45845"
    },
    "startDate": "2021-07-23T00:00:00.000Z",
    "cutoffDate": "2021-08-24T00:00:00.000Z",
    "status": "UPCOMING"
  }
}
```

| Optional                                           | &nbsp;                                                                                                                                                                                                                                                                                                |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`<br/>_Map[String, String]_                   | The name translations of the discount.                                                                                                                                                                                                                                                                |
| `startDate`<br/>_date_                             | The start date of the discount.                                                                                                                                                                                                                                                                       |
| `applyToNewCustomersOnly`<br/>_boolean_            | If true, the discount will only be applied to organizations created after the discount start date.                                                                                                                                                                                                    |
| `discountScope`<br/>_enum_                         | The scope of the discount. It can be either "ALL_PRODUCTS", "CATEGORIES" or "PRODUCTS".                                                                                                                                                                                                               |
| `packageDiscount`<br/>_BigDecimal_                 | The discount value that will be applied to all products within the applied pricing. Only required if the scope is "ALL_PRODUCTS". The value must be between (0,100] for a percentage discount and greater than 0 for a credit.                                                                        |
| `discountedCategories`<br/>_Map[UUID, BigDecimal]_ | A mapping between category IDs and discount values. All pricing products within a category will have the discount value applied to them. Required to be non-empty if scope is "CATEGORIES". All discount values must be between (0,100] for a percentage discount and greater than 0 for a credit.    |
| `discountedProducts`<br/>_Map[UUID, BigDecimal]_   | A mapping of the desired priced product IDs and discount values. All pricing products specified will have the discount value applied to them. Required to be non-empty if scope is "PRODUCTS". All discount values must be between (0,100] for a percentage discount and greater than 0 for a credit. |
| `cutoffDate`<br/>_date_                            | The date on which the discount will no longer be offered to customers who have not already received it. If not provided, the discount will always be offered after the start date.                                                                                                                    |
| `durationDays`<br/>_integer_                       | Duration of the discount once it has been applied to a customer. If not provided the discount will last indefinitely, or until credit values are reached.                                                                                                                                             |

<!-------------------- DELETE APPLIED PRICING DISCOUNT -------------------->

### Delete applied pricing discount

`DELETE /applied_pricings/:applied_pricing_id/discounts/:id`

Delete a discount. This operation can only be performed on discounts that have status UPCOMING.

```shell
curl -X DELETE "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts/18db7bc6-8be1-48bb-bab1-77a7d696fa3b" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "taskId": "85df8dfb-b904-42dc-bb76-4824e6b50c83",
  "taskStatus": "SUCCESS"
}
```

<!-------------------- DEACTIVATE APPLIED PRICING DISCOUNT -------------------->

### Deactivate applied pricing discount

`PUT /applied_pricings/:applied_pricing_id/discounts/:id/deactivate`

Deactivate a discount. This operation can only be performed on discounts that have status CURRENT or ENDED.
Deactivated is a final state, cannot be reactivated.

```shell
curl -X PUT "https://portal.coxedge.com/api/v2/applied_pricings/efd32752-c6f2-45cf-b494-cc6be8a45845/discounts/18db7bc6-8be1-48bb-bab1-77a7d696fa3b/deactivate" \
   -H "MC-Api-Key: your_api_key"
```

> The above command returns a JSON structured like this:

```json
{
  "data": {
    "applyToNewCustomersOnly": false,
    "discountedProducts": {},
    "durationDays": 60,
    "type": "PERCENTAGE",
    "discountScope": "CATEGORIES",
    "isDeactivated": true,
    "discountedCategories": {
      "8cf73cc0-b86e-49b4-a102-6102894f7955": 2,
      "00358632-5c9a-4164-a9a9-df271a9c06a9": 22
    },
    "name": {
      "en": "End of summer Discount",
      "fr": "Réduction estival fin d'été"
    },
    "id": "18db7bc6-8be1-48bb-bab1-77a7d696fa3b",
    "appliedPricing": {
      "id": "efd32752-c6f2-45cf-b494-cc6be8a45845"
    },
    "startDate": "2020-07-23T00:00:00.000Z",
    "cutoffDate": "2020-08-24T00:00:00.000Z",
    "status": "ENDED"
  }
}
```
