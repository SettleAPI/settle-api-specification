# Settle SDK for Node.js Client Functions

> For instructions on installation and generic use of the **Settle SDK for Node.js**, see the [Reference Documentation](./ZG9jOjM0ODQwMjA2-overview).

## Authentication

### Create new API Key

```js
merchant.apiKeys.create({
  "id": "string",
  "label": "string",
  "key_type": "secret",
  "roles": "null",
  "netmask": "string",
  "secret": "stringst",
  "pubkey": "string"
})
```

[Reference Documentation for `merchant.apiKeys.create`](./b3A6MTUzOTU0MDk-merchant-api-keys-create)


### List all API Keys

```js
merchant.apiKeys.list()
```
[Reference Documentation for `merchant.apiKeys.list`](./b3A6MTUzOTU0MDg-merchant-api-keys-list)

### Get API Key

```js
merchant.apiKeys.get('api_user_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "api_user_id": {
      "type": "string",
      "description": "API Key ID created by either Settle or Merchant."
    }
  },
  "required": ["api_user_id"]
}
```
[Reference Documentation for `merchant.apiKeys.get`](./b3A6MTUzOTU0NDQ-merchant-api-keys-get)


### Update API Key

```js
merchant.apiKeys.update('api_user_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "api_user_id": {
      "type": "string",
      "description": "API Key ID created by either Settle or Merchant."
    }
  },
  "required": ["api_user_id"]
}
```
[Reference Documentation for `merchant.apiKeys.update`](./b3A6MTUzOTU0NDI-merchant-api-keys-update)

### Delete API Key

```js
merchant.apiKeys.delete('api_user_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "api_user_id": {
      "type": "string",
      "description": "API Key ID created by either Settle or Merchant."
    }
  },
  "required": ["api_user_id"]
}
```
[Reference Documentation for `merchant.apiKeys.delete`](./b3A6MTUzOTU0NDM-merchant-api-keys-delete)

## Balance

### Get Merchant Balance

```js
merchant.balance.get('merchant_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "merchant_id": {
      "type": "string",
      "description": "Merchant id assigned by Settle."
    }
  },
  "required": ["merchant_id"]
}
```
[Reference Documentation for `merchant.balance.get`](./b3A6MTUzOTU0NDE-merchant-balance-get)

## Payments

### Create New Payment Request

```js
merchant.payment.request.create({
  "action": "AUTH",
  "allow_credit": true,
  "amount": 0,
  "currency": "string",
  "customer": "string",
  "line_items": {
    "product_id": "string",
    "quantity": "string",
    "item_cost": 0,
    "total": 0
  },
  "pos_id": "string",
  "pos_tid": "string",
})
```
[Reference Documentation for `merchant.payment.request.create`](./b3A6ODY4MjgyNA-merchant-payment-request-create)

### List all Payment Requests

```js
merchant.payment.request.list()
```
[Reference Documentation for `merchant.payment.request.list`](./b3A6MTUzOTU0MTE-merchant-payment-request-list)


### Get Payment Request

```js
merchant.payment.request.get('tid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.request.get`](./b3A6MTUzOTU0MTQ-merchant-payment-request-get)

### Update Payment Request

```js
merchant.payment.request.update('tid', {
  "action": "string",
  "amount": 0,
  "currency": "string",
})
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.request.update`](./b3A6OTM1MjI5OA-merchant-payment-request-update)


<!-- ### Capture Payment

```js
merchant.payment.capture('tid', {
  "action": "CAPTURE",
})
    .then(success => {
        // do something with 'success'
    }, failure => {
        console.log(failure);
    });
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.capture`](./b3A6OTM1MjI5OA-merchant-payment-request-update) -->

### Capture Payment

```js
merchant.payment.capture('tid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.capture`](./b3A6OTM1MjI5OA-merchant-payment-request-update)

### Get Payment Request Outcome

```js
merchant.payment.request.outcome.get('tid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.request.outcome.get`](./b3A6ODY5MDgzNQ-merchant-payment-request-outcome-get)


<!-- ### Refund Captured Payment (full)

```js
merchant.payment.refund.full('tid', {
  "action": "REFUND",
})
    .then(success => {
        // do something with 'success'
    }, failure => {
        console.log(failure);
    });
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  }
}
```
[Reference Documentation for `merchant.payment.refund.full`](./b3A6OTM1MjI5OA-merchant-payment-request-update) -->

### Refund Captured Payment (full)

```js
merchant.payment.refund.full('tid', 'message')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    },
    "message": {
      "type": "string",
      "description": "Text that is shown to user upon a refund. This can contain linebreaks and the text has to fit on smartphones screens."
    }
  },
  "required": ["tid"]
}
```
[Reference Documentation for `merchant.payment.refund.full`](./b3A6OTM1MjI5OA-merchant-payment-request-update)


<!-- ### Refund Captured Payment (partial)

```js
merchant.payment.refund.partial('tid', {
  "action": "REFUND",
  "refund_id": "string",
  "currency": "string",
  "amount": number,
  "additional_amount": number
})
    .then(success => {
        // do something with 'success'
    }, failure => {
        console.log(failure);
    });
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  }
}
```
[Reference Documentation for `merchant.payment.refund.partial`](./b3A6OTM1MjI5OA-merchant-payment-request-update) -->

### Refund Captured Payment (partial)

```js
merchant.payment.refund.partial('tid', 'cur', 'amo', 'adamo', 'message')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    },
    "cur": {
      "type": "string",
      "description": "In schemas where a Currency field occurs it's value determines the currency used for the Money fields in the same schema. If the schema has a nested structure, the Currency field only affects the Money fields at the same nesting level. The currency field takes a string of 3 chars representing a currency code according to the [ISO 4217 standard](https://www.iso.org/iso-4217-currency-codes.html)"
    },
    "amo": {
      "type": "string",
      "description": "Type that represents a monetary amount as an integer. In schemas where one or more [Money](./c2NoOjUwMDYw-money) fields appears there will always be a [Currency](./c2NoOjQwNjM0Ng-currency) field present, that determines the currency of the Money fields."
    },
    "adamo": {
      "type": "string",
      "description": "Type that represents a monetary amount as an integer. In schemas where one or more [Money](./c2NoOjUwMDYw-money) fields appears there will always be a [Currency](./c2NoOjQwNjM0Ng-currency) field present, that determines the currency of the Money fields."
    },
    "message": {
      "type": "string",
      "description": "Text that is shown to user upon a refund. This can contain linebreaks and the text has to fit on smartphones screens."
    }
  },
  "required": ["tid", "cur", "amo", "adamo"]
}
```
[Reference Documentation for `merchant.payment.refund.partial`](./b3A6OTM1MjI5OA-merchant-payment-request-update)

### Send New Payment

```js
merchant.payment.send.create({
  "payer": "string",
  "payee": "null",
  "idempotency_id": "string",
  "currency": "string",
  "amount": 0,
})
```
[Reference Documentation for `merchant.payment.send.create`](./b3A6MTUzOTU0Mzc-merchant-payment-send-create)


### Get Sent Payment Outcome

```js
merchant.payment.send.outcome.get('tid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "tid": {
      "type": "string",
      "description": "Transaction ID assigned by Settle."
    }
  }
}
```
[Reference Documentation for `merchant.payment.send.outcome.get`](./b3A6MTUzOTU0Mzg-merchant-payment-send-outcome-get)

## POS

### Create New POS Resource

```js
merchant.pos.create({
  "name": "string",
  "type": "webshop",
  "location": [59.912270, 10.735820, 1],
  "id": "string"
})
```
[Reference Documentation for `merchant.pos.create`](./b3A6MTUzOTU0MTU-merchant-pos-create)


### List all POS Resources

```js
merchant.pos.list()
```
[Reference Documentation for `merchant.pos.list`](./b3A6MTUzOTU0MTY-merchant-pos-list)


### Get POS Resource

```js
merchant.pos.get('pos_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "pos_id": {
      "type": "string",
      "description": "POS id as chosen on registration."
    }
  },
  "required": ["pos_id"]
}
```
[Reference Documentation for `merchant.pos.get`](./b3A6MTUzOTU0MTk-merchant-pos-get)


### Update POS Resource

```js
merchant.pos.update('pos_id', {
  "name": "string",
  "type": "webshop",
})
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "pos_id": {
      "type": "string",
      "description": "POS id as chosen on registration."
    }
  },
  "required": ["pos_id"]
}
```
[Reference Documentation for `merchant.pos.update`](./b3A6MTUzOTU0MTc-merchant-pos-update)

### Delete POS Resource

```js
merchant.pos.delete('pos_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "pos_id": {
      "type": "string",
      "description": "POS id as chosen on registration."
    }
  },
  "required": ["pos_id"]
}
```
[Reference Documentation for `merchant.pos.delete`](./b3A6MTUzOTU0MTg-merchant-pos-delete)

## Settlements

### Get Merchant Settlement

```js
merchant.settlement.get('settlement_id')
```

#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "settlement_id": {
      "type": "string",
      "description": "The ID of the settlement to retrieve."
    }
  },
  "required": ["settlement_id"]
}
```
[Reference Documentation for `merchant.settlement.get`](./b3A6MTUzOTU0MjQ-merchant-settlement-get)

## Shortlinks

### Create New Shortlink

```js
merchant.shortlink.create()
```

[Reference Documentation for `merchant.shortlink.create`](./b3A6MTUzOTU0Mjk-merchant-shortlink-create)



### List All ShortLinks

```js
merchant.shortlink.list()
```
[Reference Documentation for `merchant.shortlink.list`](./b3A6MTUzOTU0Mjg-merchant-shortlink-list)


### Get ShortLink

```js
merchant.shortlink.get('shortlink_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "shortlink_id": {
      "type": "string",
      "description": "ShortLink ID assigned by Settle."
    }
  },
  "required": ["shortlink_id"]
}
```
[Reference Documentation for `merchant.shortlink.get`](./b3A6MTUzOTU0MzA-merchant-shortlink-get)


### Update ShortLink

```js
merchant.shortlink.update('shortlink_id', 'callback_uri')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "shortlink_id": {
      "type": "string",
      "description": "ShortLink ID assigned by Settle."
    },
    "callback_uri": {
      "type": "string",
      "description": "URI called by Settle when user scans shortlink."
    }
  },
  "required": ["shortlink_id"]
}
```
[Reference Documentation for `merchant.shortlink.update`](./b3A6MTUzOTU0MzE-merchant-shortlink-update)


### Delete ShortLink

```js
merchant.shortlink.delete('shortlink_id')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "shortlink_id": {
      "type": "string",
      "description": "ShortLink ID assigned by Settle."
    }
  },
  "required": ["shortlink_id"]
}
```
[Reference Documentation for `merchant.shortlink.delete`](./b3A6MTUzOTU0MzI-merchant-shortlink-delete)

## Status Codes

### List All Status Codes

```js
merchant.statusCodes.list()
```
[Reference Documentation for `merchant.statusCodes.list`](./b3A6MTUzOTU0MzU-merchant-status-codes-list)

### Get Status Code

```js
merchant.statusCodes.get('status_code')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "status_code": {
      "type": "string",
      "description": "Status Code provided by Settle."
    }
  },
  "required": ["status_code"]
}
```
[Reference Documentation for `merchant.statusCodes.get`](./b3A6MTUzOTU0MzY-merchant-status-codes-get)


## Permission Requests

### Create New Permissions Request

```js
merchant.permissions.request.create({
  "customer": "4798765432",
  "scope": ["openid", "email"],
  "failure_return_uri": "https://example.com/failure",
  "success_return_uri": "https://example.com/success",
  "legal_terms_url": "string"
})
```
[Reference Documentation for `merchant.permissions.request.create`](./b3A6Mjk5NjUxNTk-merchant-permissions-request-create)


### Get Permissions Request

```js
merchant.permissions.request.get('rid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "rid": {
      "type": "string",
      "description": "Permission Request ID assigned by Settle"
    }
  },
  "required": ["rid"]
}
```
[Reference Documentation for `merchant.permissions.request.get`](./b3A6Mjk5NjUxNjA-merchant-permissions-request-get)


### Get Permissions Request Outcome

```js
merchant.permissions.request.outcome.get('rid')
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "rid": {
      "type": "string",
      "description": "Permission Request ID assigned by Settle"
    }
  },
  "required": ["rid"]
}
```
[Reference Documentation for `merchant.permissions.request.outcome.get`](./b3A6MzE5MjkxOTE-merchant-permissions-request-outcome-get)






<!-- ### XXXXX

```js
xxxxx()
    .then(success => {
        // do something with 'success'
    }, failure => {
        console.log(failure);
    });
```
#### Parameters
```json json_schema
{
  "type": "object",
  "properties": {
    "xxxx": {
      "type": "string",
      "description": "xxxxxxx"
    }
  }
}
```
[Reference Documentation for `xxxxx`](.xxxxxx) -->
