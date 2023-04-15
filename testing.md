> To test the environment, we are going to produce an event to a Kafka topic and then consume it.

# Producing an event
Let's publish a simple event to a topic and consume it.

Before you interact with the container, let's find the IP addresses. where the sever is running.

```bash
kubectl describe service kafka
```
output will be simmiliar to this:
```bash
Selector:          app=kafka
Type:              ClusterIP
IP Family Policy:  SingleStack
IP Families:       IPv4
IP:                10.100.56.146
IPs:               10.100.56.146
Port:              port-9092  9092/TCP
TargetPort:        9092/TCP
Endpoints:         192.168.176.112:9092,192.168.214.246:9092,192.168.251.144:9092
Port:              port-9093  9093/TCP
TargetPort:        9093/TCP
Endpoints:         192.168.176.112:9093,192.168.214.246:9093,192.168.251.144:9093
Session Affinity:  None
Events:            <none>
```
The IP `10.100.56.146` is the IP address of the brokers. We will use this IP address to connect to the Kafka cluster.

Now, let's create a pod that you can use as a Kafka client:
```bash
kubectl run kafka-client --rm -ti --image bitnami/kafka:3.1.0 -- bash
```
then inside the container terminal, let's create a topic using the example console producer script `kafka-console-producer.sh`:
```bash
kafka-console-producer.sh \
  --topic test \
  --request-required-acks all \
  --bootstrap-server 10.100.56.146:9092
```
When the `>` prompt becomes visible, you can produce a "hello world" event:
```bash
> hello world
```
the event has been produced to the topic `test`.

# Consume the events on the "test" topic

In the same terminal session, terminate the script with `ctrl+C` or `cmd+C` and run the `kafka-console-consumer.sh` script:
```bash
kafka-console-consumer.sh \
  --topic test \
  --from-beginning \
  --bootstrap-server 10.100.56.146:9092
```
You should see the event you produced earlier:
```bash
hello world
```
The consumer continues to poll the broker for more events on the test topic and process them as they happen.
