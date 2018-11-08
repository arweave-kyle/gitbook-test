# HTTP API

### Network

{% api-method method="get" host="http://arweave.net:1984" path="/infooo" %}
{% api-method-summary %}
Network Info
{% endapi-method-summary %}

{% api-method-description %}
Get the current network information.
{% endapi-method-description %}

{% api-method-spec %}

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
Get the list of peers that the node. Nodes can only respond with peers they currently know about so this will not be an exhaustive list of nodes in the network.
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

## Test

