# HTTP API

## Transactions

{% api-method method="get" host="http://arweave.net:1984" path="/tx/:id" %}
{% api-method-summary %}
Get Transaction by ID
{% endapi-method-summary %}

{% api-method-description %}
Get a transaction by its ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Transaction ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "id": "BNttzDav3jHVnNiV7nYbQv-GY0HQ-4XXsdkE5K9ylHQ",
  "last_tx": "jUcuEDZQy2fC6T3fHnGfYsw0D0Zl4NfuaXfwBOLiQtA",
  "owner": "posmE...psEok",
  "tags": [],
  "target": "",
  "quantity": "0",
  "data": "PGh0b...RtbD4",
  "reward": "124145681682",
  "signature": "HZRG_...jRGB-M"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %}
The transaction is pending.
{% endapi-method-response-example-description %}

```
Pending
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The provided transaction ID is not valid.
{% endapi-method-response-example-description %}

```
Invalid hash.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
A transaction with the given ID could not be found.
{% endapi-method-response-example-description %}

```
Not Found.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://arweave.net:1984" path="/tx/:id/:field" %}
{% api-method-summary %}
Get Transaction Field
{% endapi-method-summary %}

{% api-method-description %}
Get a single field from a transaction.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Transaction ID
{% endapi-method-parameter %}

{% api-method-parameter name="field" type="string" required=true %}
Field name. Acceptable values: id, last\_tx, owner, tags, target, quantity, data, reward, signature
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The field value as plain text
{% endapi-method-response-example-description %}

```
jUcuEDZQy2fC6T3fHnGfYsw0D0Zl4NfuaXfwBOLiQtA
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %}
The transaction is pending.
{% endapi-method-response-example-description %}

```
Pending
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The provided transaction ID is not valid or the field name is not valid.
{% endapi-method-response-example-description %}

```
Invalid hash.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
A transaction with the given ID could not be found.
{% endapi-method-response-example-description %}

```
Not Found.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://arweave.net:1984" path="/tx/:id/data.:extension" %}
{% api-method-summary %}
Get Transaction data
{% endapi-method-summary %}

{% api-method-description %}
Get the base64 decoded data from a transaction.  
  
A `Content-Type` tag can be submitted with a transaction, and the value of this tag will be used in the `Content-Type` header on this response. For example if a PDF file is posted in a transaction with the following tag  
  
`[  
  {"Name": "Content-Type"},  
  {"Value" : "application/pdf"}  
]`  
  
then the response will be served as a PDF.  
  
The `Content-Type` will default to `text/html` so this endpoint will return a browser renderable response by default.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
Transaction ID
{% endapi-method-parameter %}

{% api-method-parameter name="extension" type="string" required=false %}
Any extension can be specified depending on the clients use case. Web pages can be requested with `data.html` .
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```markup
<html lang="en-GB" class="b-pw-1280 no-touch orb-js id-svg bbcdotcom ads-enabled bbcdotcom-init bbcdotcom-responsive bbcdotcom-async bbcdotcom-ads-enabled orb-more-loaded  bbcdotcom-group-5" id="responsive-news">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=1">
...
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %}
The transaction is pending.
{% endapi-method-response-example-description %}

```
Pending
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The provided transaction ID is not valid or the field name is not valid.
{% endapi-method-response-example-description %}

```
Invalid hash.
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
A transaction with the given ID could not be found.
{% endapi-method-response-example-description %}

```
Not Found.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="http://arweave.net:1984" path="/tx" %}
{% api-method-summary %}
Submit a Transaction
{% endapi-method-summary %}

{% api-method-description %}
Submit a new transaction to the network.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="signature" type="string" required=true %}
The transaction signature, base64 URL encoded.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Network

{% api-method method="get" host="http://arweave.net:1984" path="/info" %}
{% api-method-summary %}
Network Info
{% endapi-method-summary %}

{% api-method-description %}
Get the current network information.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Accept" type="string" required=false %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "network": "arweave.N.1",
  "version": 3,
  "release": 16,
  "height": 78309,
  "current": "o8ahQ55Omd7Fdi4UgGP82bD2-TZ66JYY33NzGyvpLL3_V3wCmsq8NJmnkJl1p_ew",
  "blocks": 97375,
  "peers": 64,
  "queue_length": 0,
  "node_state_latency": 18
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



{% api-method method="get" host="http://arweave.net" path="/peers" %}
{% api-method-summary %}
Peer list
{% endapi-method-summary %}

{% api-method-description %}
Get the list of peers that the node. Nodes can only respond with peers they currently know about, so this will not be an exhaustive list of nodes on the network.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  "127.0.0.1:1984",
  "0.0.0.0:1984"
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

