# Piggy Metrics (Kubernetes) - Service discovery

[![CircleCI](https://circleci.com/gh/afermon/PiggyMetrics-registry-service.svg?style=svg)](https://circleci.com/gh/afermon/PiggyMetrics-registry-service)  [![GitHub license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/afermon/PiggyMetrics-registry-service/blob/master/LICENCE)

Another commonly known architecture pattern is Service discovery. It allows automatic detection of network locations for service instances, which could have dynamically assigned addresses because of auto-scaling, failures and upgrades.

The key part of Service discovery is Registry. I use Netflix Eureka in this project. Eureka is a good example of the client-side discovery pattern, when client is responsible for determining locations of available service instances (using Registry server) and load balancing requests across them.

With Spring Boot, you can easily build Eureka Registry with `spring-cloud-starter-eureka-server` dependency, `@EnableEurekaServer` annotation and simple configuration properties.

Client support enabled with `@EnableDiscoveryClient` annotation an `bootstrap.yml` with application name:
``` yml
spring:
  application:
    name: notification-service
```

Now, on application startup, it will register with Eureka Server and provide meta-data, such as host and port, health indicator URL, home page etc. Eureka receives heartbeat messages from each instance belonging to a service. If the heartbeat fails over a configurable timetable, the instance will be removed from the registry.

Also, Eureka provides a simple interface, where you can track running services and a number of available instances: `http://localhost:8761`

For more information please refer to the main repository [afermon/PiggyMetrics-Kubernetes](https://github.com/afermon/PiggyMetrics-Kubernetes)

## Credits

* Forked from [sqshq/PiggyMetrics](https://github.com/sqshq/PiggyMetrics)