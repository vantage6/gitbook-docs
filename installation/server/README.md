---
description: A (central) server allows parties to connect and exchange data.
---

# Server

To install the **vantage6-server** make sure you have met the [requirements](../what-to-install/#node-and-server). Then install the latest version:

```
pip install vantage6
```

This command will install the vantage6 command line interface (CLI), from which you can create new servers (see Use [running-the-server](../../usage/running-the-server/ "mention")).

#### Optional components

There are several optional components that you can set up apart from the vantage6-server itself.

You can set up a [user-interface.md](user-interface.md "mention"), which is a web application that will allow your users to communicate more easily with your vantage6 server.

A docker registry can be used to store algorithms but it is also possible to use [Docker hub](https://hub.docker.com/) for this. For instructions on how to install your own Docker registry see [docker-registry.md](docker-registry.md "mention").&#x20;

If you want to enable algorithm containers that are running on different nodes, to directly communicate with one another, you require a VPN server. Refer to [eduvpn.md](eduvpn.md "mention") on how to install the VPN server.

If you have a server with a high workload whose performance you want to improve, you may want to set up a RabbitMQ service which enables horizontal scaling of the Vantage6 server. See[rabbitmq.md](rabbitmq.md "mention")[ ](rabbitmq.md)on how to set this up.
