# Client

We provide four ways in which you can interact with the server to manage your vantage6 resources:&#x20;

* [User Interface](user-interface.md) (UI)
* [Python client](python-client/)
* [R client](r-client.md)
* [Server API](server-api.md)

The UI and the clients make it much easier to interact with the server than directly interacting with the server API through HTTP requests, especially as data is serialized and encrypted automatically. For most use cases, we recommend to use the UI and/or the Python client.&#x20;

{% hint style="info" %}
The R client is only suitable for creating tasks and retrieve their results. With the Python client it is possible to use the entire API.
{% endhint %}

## Permissions

Note that whenever you interact with the server, you are limited by your permissions. For instance, if you try to create another user but do not have permission to do so, you will receive an error message. All permissions are described by rules, which can be aggregated in roles. Contact your administrator if you find your permissions are inappropriate.

{% hint style="success" %}
There are predefined roles such as 'Researcher' and 'Organization Admin' that are automatically created by the server. These can be assigned to any new user by the administrator that is creating the user.
{% endhint %}



