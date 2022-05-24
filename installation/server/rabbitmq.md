---
description: Horizontal scaling for servers with high workloads
---

# RabbitMQ

_Please note that RabbitMQ is an **optional** component. It enables the server to handle multiple requests at the same time. This is important if a server has a high workload._

There are several options to host your own RabbitMQ server. You can run [RabbitMQ in Docker](https://hub.docker.com/\_/rabbitmq) or host [RabbitMQ on Azure](https://www.golinuxcloud.com/install-rabbitmq-on-azure/). When you have set up your RabbitMQ service, you can connect the server to it by adding the following to the server configuration:

```
rabbitmq_uri: amqp://<username>:<password@<hostname>:5672/<vhost>
```

Be sure to create the user and vhost that you specify exist! Otherwise, you can add them via the [RabbitMQ management console](https://www.cloudamqp.com/blog/part3-rabbitmq-for-beginners\_the-management-interface.html).

{% hint style="warning" %}
Note that the RabbitMQ currently (vantage6 version 3.2) does not yet work if you start your server via `vserver start`. We are planning to implement support for this in v3.3. Until then, please contact us if you want help setting up a vantage6 server with RabbitMQ.
{% endhint %}
