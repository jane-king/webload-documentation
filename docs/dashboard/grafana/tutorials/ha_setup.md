# How to setup Grafana for high availability

> Alerting does not support high availability yet.

Setting up Grafana for high availability is fairly simple. It comes down to two things:

  * Use a shared database for multiple grafana instances.
  * Consider how user sessions are stored.

## Configure multiple servers to use the same database

First you need to do is to setup mysql or postgres on another server and configure Grafana to use that database.
You can find the configuration for doing that in the [[database]](../installation/configuration.md#database) section in the grafana config.
Grafana will now persist all long term data in the database. 
It also worth considering how to setup the database for high availability but thats outside the scope of this guide.

## User sessions

The second thing to consider is how to deal with user sessions and how to balance the load between servers. 
By default Grafana stores user sessions on disk which works fine if you use `sticky sessions` in your load balancer. 
Grafana also supports storing the session data in the database, redis or memcache which makes it possible to use round robin in your load balancer. 
If you use mysql/postgres for session storage you first need a table to store the session data in. More details about that in [[sessions]](../installation/configuration.md#session) 

For Grafana itself it doesn't really matter if you store your sessions on disk or database/redis/memcache.
But we suggest that you store the session in redis/memcache since it makes it easier to add/remote instances from the group. 

## Alerting

Currently alerting does not support high availability. But this is something that we will be working on in the future. 


