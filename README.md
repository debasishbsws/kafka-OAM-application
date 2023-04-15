# Kafka-OAM-Application

> Apache Kafka is a distributed, open-source streaming platform that is used for building real-time data streaming applications.

## References

* [https://kafka.apache.org](https://kafka.apache.org/)

After deploy the application, get the endpoint executing:

## How to deploy

```bash
playground catalog deploy napptive/kafka:1.0

STATUS     INFO
SUCCESS    application deployed
```

```bash
playground apps  info kafka
NAME          STATUS
kafka    APP_RUNNING

COMPONENT    STATUS    SCOPES    TRAITS
kafka       OK                  kafka-ingress

COMPONENT    INGRESSES
kafka        kafka -<usernane>.apps.playground.napptive.dev
```

```bash
playground apps open kafka 
```

To configure kafka  installation, log into admin interface using main installation URL with `/adminpanel/` appended to it:

```bash
user: superadmin
password: 
```

