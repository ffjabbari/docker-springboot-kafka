[![Build Status](https://travis-ci.org/claudioaltamura/docker-springboot-kafka.svg?branch=master)](https://travis-ci.org/claudioaltamura/docker-springboot-kafka)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# docker-springboot-kafka
spring boot example with docker and kafka


## Building the example

	./gradlew clean build

or without tests

	./gradle clean bootJar

## Running the example

Run

	java -jar build/libs/docker-springboot-kafka-0.1.0.jar

	
docker exec -it docker-springboot-kafka_kafka_1 sh

docker-compose up -d kafka
Creating network "docker-springboot-kafka_kafka" with the default driver
Creating volume "docker-springboot-kafka_kafka_data" with default driver
Creating docker-springboot-kafka_zookeeper_1 ... done
Creating docker-springboot-kafka_kafka_1     ... done

docker-compose ps

docker inspect docker-springboot-kafka_kafka_1 | grep IP
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
                    "IPAMConfig": null,
                    "IPAddress": "192.168.112.3",
                    "IPPrefixLen": 20,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,

curl http://127.0.0.1:8080/helloworld/manopeter

λ docker exec -it docker-springboot-kafka_kafka_1 bash
                    bash-4.4# 

                    bash-4.4# /opt/kafka/bin/kafka-console-consumer.sh     --bootstrap-server localhost:9092     --topic helloworld  --from-beginning
                    {"timestamp":0,"message":"Hello World!"}

                    bash-4.4# $KAFKA_HOME/bin/kafka-topics.sh --list --zookeeper $KAFKA_ZOOKEEPER_CONNECT
                    __consumer_offsets
                    helloworld

                    bash-4.4# $KAFKA_HOME/bin/kafka-topics.sh --describe --zookeeper $KAFKA_ZOOKEEPER_CONNECT --topic helloworld
                    Topic:helloworld        PartitionCount:1        ReplicationFactor:1     Configs:
                            Topic: helloworld       Partition: 0    Leader: 1001    Replicas: 1001  Isr: 1001
                    bash-4.4#
                    	
	
	