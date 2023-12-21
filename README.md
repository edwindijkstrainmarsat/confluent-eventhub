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

