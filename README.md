# confluent-eventhub


Step by step:

- Create an Event hub namespace (Standard tier)
- Create an unrestricted VM.
- (Optional) Mark the namespace as private and create a private endpoint, so traffic doesn't go over the internet.
- Setup the VM

### setup java and kafka cli:
```shell
sudo apt update
sudo apt install default-jre -y
wget https://downloads.apache.org/kafka/3.6.1/kafka_2.13-3.6.1.tgz
tar -xzf kafka_2.13-3.6.1.tgz
```
To test Azure connectivity with the Kafka CLI, have a look here: https://github.com/Azure/azure-event-hubs-for-kafka/tree/master/quickstart/kafka-cli

### setup docker
```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo usermod -aG docker $USER
```

### log out and log back in

### clone this repo and bring the test env up
```
git clone https://github.com/edwindijkstrainmarsat/confluent-eventhub.git
cd confluent-eventhub
docker compose up -d
```
### setup a data generator
```
curl -X POST -H "Content-Type: application/json" --data @config/connector_pageviews.config http://localhost:8083/connectors
docker-compose exec kafka-connect kafka-console-consumer --topic pageviews --bootstrap-server kafka:29092  --property print.key=true --max-messages 5 --from-beginning
```
### setup mirrormaker from the local kafka to eventhub
curl -X POST -H "Content-Type: application/json" --data @eventhub/connect-mm.json http://localhost:8085/connectors
