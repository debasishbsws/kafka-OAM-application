# Apache-Kafka

> Apache Kafka is a distributed streaming platform used for building real-time data pipelines and streaming apps. It is horizontally scalable, fault-tolerant, wicked fast.
        
## How to Use

After deploy the application, the bootstrap server is available at kafka `<ClusterIP>:9092`  
To get the ClusterIP you can use the command `kubectl get svc` and look for the service named `kafka`  

## How to Deploy and edit configuration

To deploy the application, you can use the playgroung CLI command:
```bash
playground catalog deploy debasishbiswas/apache-kafka:3.4.0
```

It will deploy the application with the default configuration where we will have 3 Brokers.  

You can configure by changing `env` variables in the `properties` file.  

- `DEFAULT_REPLICATION_FACTOR` - The cluster-wide default replication factor. Always should be >= 1 and less than the number of brokers.  
- `DEFAULT_MIN_INSYNC_REPLICAS` - The cluster-wise default in-sync replicas size.  
- `SHARE_DIR` - used to set log.dirs; The directories in which the Kafka data is stored.  
- `CLUSTER_ID` - The unique identifier for the Kafka cluster.  

> Note: The volume mount EmptyDir is not recommended in production environments.

## References
[Apache Kafka](https://kafka.apache.org/)

[IBM - KRaft mode Kafka on Kubernetes](https://github.com/IBM/kraft-mode-kafka-on-kubernetes)

[Updated Image - GitHub](https://github.com/debasishbsws/kafka-OAM-application)

[Test the application](https://github.com/debasishbsws/kafka-OAM-application/blob/master/testing.md)
