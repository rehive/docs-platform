# Transactions

Rehive offers 2 standard transaction types: debit and credit. Debit transactiosn deduct from a user's account and credit transaction add to a user's account. There is also an additional "transfer" endpoint that can be used in order to automtically trigger a debit followed by a credit on the specified accounts.

## List Transactions

> User transactions request

```shell
curl https://api.rehive.com/3/transactions/
  -X GET
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
```

```javascript
var filters = {
    tx_type: "credit",
    currency:'ZAR'
};

rehive.transactions.get({filters: filters}).then(function(res){
    ...
},function(err){
    ...
})
```

```python
# Filters are not required
filters = {
    "tx_type": "credit",
    "currency": "ZAR"
}

rehive.transactions.get(
    filters=filters
)
```

> User transactions response

```shell
 {
    "status": "success",
    "data": {
        "count": 1,
        "next": null,
        "previous": null,
        "results": [
            {
                "id": "00000000-0000-0000-0000-000000000000",
                "collection": "00000000-0000-0000-0000-000000000000",
                "parent": null,
                "partner": null,
                "inferred": false,
                "tx_type": "credit",
                "subtype": null,
                "note": "",
                "metadata": {},
                "status": "Pending",
                "reference": "",
                "amount": 500,
                "balance": 0,
                "account": "0000000000",
                "label": "Credit",
                "company": "rehive",
                "total_amount":100,
                "currency": {
                    "description": "Rand",
                    "code": "ZAR",
                    "symbol": "R",
                    "unit": "rand",
                    "divisibility": 2
                },
                "created": 1496135465218,
                "updated": 1496135465287
            }
        ]
    }
}
```

```javascript
 {
    "count": 2,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "collection": "00000000-0000-0000-0000-000000000000",
            "parent": null,
            "partner": null,
            "inferred": false,
            "tx_type": "credit",
            "subtype": null,
            "note": "",
            "metadata": {},
            "status": "Pending",
            "reference": "",
            "amount": 500,
            "balance": 0,
            "account": "0000000000",
            "label": "Credit",
            "company": "rehive",
            "total_amount":100,
            "currency": {
                "description": "Rand",
                "code": "ZAR",
                "symbol": "R",
                "unit": "rand",
                "divisibility": 2
            },
            "created": 1496135465218,
            "updated": 1496135465287
        }
    ]
 }
```

```python
 [
    {
        "id": "00000000-0000-0000-0000-000000000000",
        "collection": "00000000-0000-0000-0000-000000000000",
        "parent": null,
        "partner": null,
        "inferred": false,
        "tx_type": "credit",
        "subtype": null,
        "note": "",
        "metadata": {},
        "status": "Pending",
        "reference": "",
        "amount": 500,
        "balance": 0,
        "account": "0000000000",
        "label": "Credit",
        "company": "rehive",
        "total_amount":100,
        "currency": {
            "description": "Rand",
            "code": "ZAR",
            "symbol": "R",
            "unit": "rand",
            "divisibility": 2
        },
        "created": 1496135465218,
        "updated": 1496135465287
    }
]
```

Get a a user's transaction list.

#### Filtering

Field | Type
--- | ---
`id` | string
`tx_type` | boolean
`subtype` | string
`status` | string
`account` | string
`partner` | string
`partner__isnull` | boolean
`collection` | string
`created` | millsecond timestamp
`updated` | millsecond timestamp
`metadata` | any

#### Endpoint

`https://api.rehive.com/3/transactions/`

## Total Transactions

> User total transactions request

```shell
curl https://api.rehive.com/3/transactions/totals/
  -X GET
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
```

```javascript

rehive.transactions.totals.get().then(function(res){
    ...
},function(err){
    ...
})
```

```python
rehive.transactions.get_totals()
```

> User total transactions response

```shell
{
    "status": "success",
    "data": {
        "amount": 500,
        "total_amount": 500,
        "fees": 0,
        "count": 1,
        "currency": "ZAR"
    }
}
```

```javascript
{
    "amount": 1000,
    "total_amount": 500,
    "count": 2,
    "currency": "ZAR",
    "fees": 0
}
```

```python
{
    "amount": 500,
    "total_amount": 500,
    "fees": 0,
    "count": 1,
    "currency": "ZAR"
}
```

Get a user's total transaction details. This summarizes transaction fields like:
amount, total_amount and fees. It also retrieves a total count of all transactions.

#### Filtering

See Transaction List filtering above.

#### Endpoint

`https://api.rehive.com/3/transactions/totals/`

## Create Credit

> User credit request

```shell
curl https://api.rehive.com/3/transactions/credit/
  -X POST
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
  -d '{"amount": 500, "currency": "ZAR"}'
```

```javascript
rehive.transactions.createCredit(
{
    amount: 500,
    currency: "ZAR"
}).then(function(res){
    ...
},function(err){
    ...
})
```

```python
rehive.transactions.create_credit(
    amount=500,
    currency="ZAR"
)
```

> User credit response

```shell
{
    "status": "success",
    "data": {
        "id": "00000000-0000-0000-0000-000000000000",
        "collection": "00000000-0000-0000-0000-000000000000",
        "parent": null,
        "partner": null,
        "inferred": false,
        "tx_type": "credit",
        "subtype": null,
        "note": "",
        "metadata": {},
        "status": "Pending",
        "reference": null,
        "amount": 500,
        "total_amount": 500,
        "balance": 0,
        "account": "0000000000",
        "label": "Credit",
        "company": "rehive",
        "currency": {
            "description": "Rand",
            "code": "ZAR",
            "symbol": "R",
            "unit": "rand",
            "divisibility": 2
        },
        "messages": [],
        "created": 1476691969394,
        "updated": 1496135465287
    }
}
```

```javascript
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "inferred": false,
    "tx_type": "credit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": null,
    "amount": 500,
    "total_amount": 500,
    "balance": 0,
    "account": "0000000000",
    "label": "Credit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

```python
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "inferred": false,
    "tx_type": "credit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": null,
    "amount": 500,
    "total_amount": 500,
    "balance": 0,
    "account": "0000000000",
    "label": "Credit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

Create a credit transaction.

#### Endpoint

`https://api.rehive.com/3/transactions/credit/`

#### Required Fields

Field | Description | Default
--- | --- | ---
`amount` | amount | null
`currency` | currency code | null

#### Optional Fields

Field | Description | Default
--- | --- | ---
`reference` | optional credit reference | blank
`subtype` | a custom defined subtype | null
`account` | account reference code | null
`note` | user's note or message | blank
`metadata` | custom metadata | {}

<aside class="notice">
Bear in mind that the <code>amount</code> should always be in the lowest currency unit available (ie, cents).
</aside>

<aside class="notice">
A <code>subtype</code> can be created in the admin dashboard (or via the API). A blank/null<code>subtype</code> can be sent without errors but if a subtype is sent in the request it must match an existing <code>subtype</code> and it's related <code>tx_type</code> in Rehive.
</aside>

## Create Debit

> User debit request

```shell
curl https://api.rehive.com/3/transactions/debit/
  -X POST
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
  -d '{"amount": 500, "currency": "ZAR"}'
```

```javascript
rehive.transactions.createDebit(
{
    amount: 500,
    currency: "ZAR"
}).then(function(res){
    ...
},function(err){
    ...
})
```

```python
rehive.transactions.create_debit(
    amount=500,
    currency="ZAR"
)
```

> User debit response

```shell
{
    "status": "success",
    "data": {
        "id": "00000000-0000-0000-0000-000000000000",
        "collection": "00000000-0000-0000-0000-000000000000",
        "parent": null,
        "partner": null,
        "inferred": false,
        "tx_type": "debit",
        "subtype": null,
        "note": "",
        "metadata": {},
        "status": "Pending",
        "reference": null,
        "amount": -500,
        "total_amount": -500,
        "balance": 0,
        "account": "0000000000",
        "label": "Debit",
        "company": "rehive",
        "currency": {
            "description": "Rand",
            "code": "ZAR",
            "symbol": "R",
            "unit": "rand",
            "divisibility": 2
        },
        "messages": [],
        "created": 1476691969394,
        "updated": 1496135465287
    }
}
```

```javascript
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "inferred": false,
    "tx_type": "debit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": null,
    "amount": -500,
    "total_amount": -500,
    "balance": 0,
    "account": "0000000000",
    "label": "Debit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

```python
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "inferred": false,
    "tx_type": "debit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": null,
    "amount": -500,
    "total_amount": -500,
    "balance": 0,
    "account": "0000000000",
    "label": "Debit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

Create a debit transaction.

#### Endpoint

`https://api.rehive.com/3/transactions/debit/`

#### Required Fields

Field | Description | Default
--- | --- | ---
`amount` | amount | null
`currency` | currency code | null

#### Optional Fields

Field | Description | Default
--- | --- | ---
`reference` | optional debit reference | blank
`subtype` | a custom defined subtype | null
`account` | account reference code | null
`note` | user's note or message | blank
`metadata` | custom metadata | {}

## Create Transfer

> User transfer request

```shell
curl https://api.rehive.com/3/transactions/transfer/
  -X POST
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
  -d '{"amount": 500,
       "currency": "ZAR",
       "recipient": "susan@rehive.com"}'
```

```javascript
rehive.transactions.createTransfer(
{
    amount: 500,
    recipient: "susan@rehive.com"
}).then(function(res){
    ...
},function(err){
    ...
})
```

```python
rehive.transactions.create_transfer(
    amount=500,
    recipient="susan@rehive.com"
)
```

> User transfer response

```shell
{
    "status": "success",
    "data": {
        "id": "00000000-0000-0000-0000-000000000000",
        "collection": "00000000-0000-0000-0000-000000000000",
        "parent": null,
        "partner": {
            "id": "00000000-0000-0000-0000-000000000000",
            "user": {
                "id": "00000000-0000-0000-0000-000000000000",
                "first_name": "Susan",
                "last_name": "Brown",
                "email": "susan@rehive.com",
                "username": "",
                "mobile": "+27850000000",
                "profile": null,
                "temporary": false
            }
        },
        "inferred": false,
        "tx_type": "debit",
        "subtype": null,
        "note": "",
        "metadata": {},
        "status": "Complete",
        "reference": null,
        "amount": -500,
        "total_amount": -500,
        "balance": 0,
        "account": "0000000000",
        "label": "Debit",
        "company": "rehive",
        "currency": {
            "description": "Rand",
            "code": "ZAR",
            "symbol": "R",
            "unit": "rand",
            "divisibility": 2
        },
        "messages": [],
        "created": 1476691969394,
        "updated": 1496135465287
    }
}
```

```javascript
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": {
        "id": "00000000-0000-0000-0000-000000000000",
        "user": {
            "id": "00000000-0000-0000-0000-000000000000",
            "first_name": "Susan",
            "last_name": "Brown",
            "email": "susan@rehive.com",
            "username": "",
            "mobile": "+27850000000",
            "profile": null,
            "temporary": false
        }
    },
    "tx_type": "debit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Complete",
    "reference": null,
    "amount": -500,
    "total_amount": -500,
    "balance": 0,
    "account": "0000000000",
    "label": "Debit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

```python
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": {
        "id": "00000000-0000-0000-0000-000000000000",
        "user": {
            "id": "00000000-0000-0000-0000-000000000000",
            "first_name": "Susan",
            "last_name": "Brown",
            "email": "susan@rehive.com",
            "username": "",
            "mobile": "+27850000000",
            "profile": null,
            "temporary": false
        }
    },
    "tx_type": "debit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Complete",
    "reference": null,
    "amount": -500,
    "total_amount": -500,
    "balance": 0,
    "account": "0000000000",
    "label": "Debit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

Create a transfer transaction. This will transfer currency from one user/account to another. If the recipient reference does not exist as a user in Rehive and the reference is an email address or mobile number then an invitation message will be sent to the recipient informing them thay have an unclaimed transaction.

<aside class="notice">
The transfer transaction endpoint is a wrapper for standard debit/credit transactions. If a transfer is completed successfuly it will create 2 transactions: one to debit from the sender and one to credit the receiver. The transactions are otherwise indentical to normal debit/credit transactions. You can view sender/receiver details by accessing the `partner` attribute.
</aside>

#### Endpoint

`https://api.rehive.com/3/transactions/transfer/`

#### Required Fields

Field | Description | Default
--- | --- | ---
`amount` | amount | null
`currency` | currency code | null

#### Optional Fields

Field | Description | Default
--- | --- | ---
<ul><li>`recipient`</li>and/or<li>`credit_account`</li></ul> | <ul><li>email, mobile number, or unique id</li><li>account reference code</li></ul> | null
`debit_subtype` | a custom defined subtype | null
`debit_account` | account reference code | null
`debit_note` | user's note or message | blank
`debit_metadata` | custom metadata | {}
`debit_reference` | optional debit reference | string
`credit_subtype` | a custom defined subtype | null
`credit_account` | account reference code | null
`credit_note` | user's note or message | blank
`credit_metadata` | custom metadata | {}
`credit_reference` | optional credit reference | string

## Create Transactions

> User create transactions request

```shell
curl https://api.rehive.com/3/transactions/
  -X POST
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
  -d '{"transactions": [
        {"amount": 500, "currency": "ZAR", "tx_type": "credit"},
        {"amount": 500, "currency": "ZAR", "tx_type": "credit"}]}'
```

```javascript
```

```python
```

> User create transactions response

```shell
{
    "status": "success",
    "data": {
        "transactions": [
            {
                "id": "00000000-0000-0000-0000-000000000000",
                "collection": "00000000-0000-0000-0000-000000000000",
                "parent": null,
                "partner": null,
                "tx_type": "credit",
                "subtype": null,
                "note": "",
                "metadata": {},
                "status": "Pending",
                "reference": null,
                "amount": 500,
                "total_amount": 500,
                "balance": 0,
                "account": "0000000000",
                "label": "Credit",
                "company": "rehive",
                "currency": {
                    "description": "Rand",
                    "code": "ZAR",
                    "symbol": "R",
                    "unit": "rand",
                    "divisibility": 2
                },
                "messages": [],
                "created": 1476691969394,
                "updated": 1496135465287
            },
            {
                "id": "00000000-0000-0000-0000-000000000000",
                "collection": "00000000-0000-0000-0000-000000000000",
                "parent": null,
                "partner": null,
                "tx_type": "credit",
                "subtype": null,
                "note": "",
                "metadata": {},
                "status": "Pending",
                "reference": null,
                "amount": 500,
                "total_amount": 500,
                "balance": 0,
                "account": "0000000000",
                "label": "Credit",
                "company": "rehive",
                "currency": {
                    "description": "Rand",
                    "code": "ZAR",
                    "symbol": "R",
                    "unit": "rand",
                    "divisibility": 2
                },
                "messages": [],
                "created": 1476691969394,
                "updated": 1496135465287
            }
        ]
    }
}
```

```javascript
```

```python
```

Create a batch of transactions. This action is atomic and the whole batch will either fail or succeed at the same time. This endpoint can create up to 24 transactions at the same time.

#### Endpoint

`https://api.rehive.com/3/transactions/`

#### Required Fields

Field | Description | Default
--- | --- | ---
`amount` | amount | null
`currency` | currency code | null
`tx_type` | transaction type | null

#### Optional Fields

Field | Description | Default
--- | --- | ---
`reference` | optional credit reference | blank
`subtype` | a custom defined subtype | null
`account` | account reference code | null
`note` | user's note or message | blank
`metadata` | custom metadata | {}


## Retrieve Transaction

> Retrieve transaction request

```shell
curl https://api.rehive.com/3/transactions/{id}/
  -X GET
  -H "Authorization: Token {token}"
  -H "Content-Type: application/json"
```

```javascript
rehive.transactions.get({id: transactionId}).then(function(res){
    ...
},function(err){
    ...
})
```

```python
rehive.transactions.get(
   "{id}"
)
```

> Retrieve transaction response

```shell
{
    "status": "success",
    "data":  {
        "id": "00000000-0000-0000-0000-000000000000",
        "collection": "00000000-0000-0000-0000-000000000000",
        "parent": null,
        "partner": null,
        "tx_type": "credit",
        "subtype": null,
        "note": "",
        "metadata": {},
        "status": "Pending",
        "reference": null,
        "amount": 500,
        "total_amount": 500,
        "balance": 0,
        "account": "0000000000",
        "label": "Credit",
        "company": "rehive",
        "currency": {
            "description": "Rand",
            "code": "ZAR",
            "symbol": "R",
            "unit": "rand",
            "divisibility": 2
        },
        "messages": [],
        "created": 1476691969394,
        "updated": 1496135465287
    }
}
```

```javascript
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "tx_type": "credit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": "",
    "amount": 500,
    "balance": 0,
    "account": "0000000000",
    "label": "Credit",
    "company": "rehive",
    "total_amount":-300,
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1496135465218,
    "updated": 1496135465287
}
```

```python
{
    "id": "00000000-0000-0000-0000-000000000000",
    "collection": "00000000-0000-0000-0000-000000000000",
    "parent": null,
    "partner": null,
    "tx_type": "credit",
    "subtype": null,
    "note": "",
    "metadata": {},
    "status": "Pending",
    "reference": null,
    "amount": 500,
    "total_amount": 500,
    "balance": 0,
    "account": "0000000000",
    "label": "Credit",
    "company": "rehive",
    "currency": {
        "description": "Rand",
        "code": "ZAR",
        "symbol": "R",
        "unit": "rand",
        "divisibility": 2
    },
    "messages": [],
    "created": 1476691969394,
    "updated": 1496135465287
}
```

Get transaction details for a spcific transactions.

#### Endpoint

`https://api.rehive.com/3/transactions/{id}/`

