1. Launce EC2 instance on AWS and generate a key pair image.
2. Store the key-pair into a folder. Now, open the terminal in the same folder and paste the SSH command of the EC2 instance there.
3. To deal with the denied permission error try the following command

```
chmod 400 {key-val} 

```

4. In order to run Apache Kafka you first need to download it on the EC2 instance.

```
wget https://downloads.apache.org/kafka/3.6.1/kafka_2.13-3.6.1.tgz

```
To unzip the folder:

```
tar-xvf {zip folder name} 

```

5. Kafka runs on JVM, so in order to run kafka on ec2 you also need to download java on your instance.

```
sudo yum install java-1.8.0

```

6. Now, we can go ahead and start the kafka zookeeper on our ec2 instance, but before that we will do 2 things, first will be go the ec2 instance console and add the following inbound rule and then run the kakfa on public ip instead of private. Run the following command for the same.

```
sudo nano config/server.properties


```
uncomment the #advertised part and paste the public ipv4 address that is shown on the information of your ec2 instance.
<img width="1378" alt="image" src="https://github.com/shyamal31/Stock-Data-pipeline-using-Apache-Kafka/assets/57554284/65c80a75-408c-44dc-ab05-fbec19ff3d5f">


7. Now, one by one we will start zookeeper and kafka API servers. Use a different terminal to start kafka server once the zookeeper is activated on one terminal.

###Start Zookeeper
```
cd {uncompressed folder}
bin/zookeeper-server-start.sh config/zookeeper.properties

```
###Start Kafka server
Duplicate the session & enter in a new console --
```

export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
cd kafka_2.12-3.3.1
bin/kafka-server-start.sh config/server.properties

```
8. Now, we will create topic, producer and then consumer. (use new terminal for everything and follow all the stpes mentioned before zookeeper start)

### create Topic

```
bin/kafka-topics.sh --create --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092} --replication-factor 1 --partitions 1

```
### Start Producer

```
bin/kafka-console-producer.sh --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092} 


```

### Start Consumer

```
bin/kafka-console-consumer.sh --topic demo_testing2 --bootstrap-server {Put the Public IP of your EC2 Instance:9092}

```

9. Now, inroder to store the data on s3, first create s3 bucket on aws
10. Then create IAM user role: Go to IAM->add user->give admin rights-> download CSV ->download AWS CLI and then set the Key Id and secret key id

11. Crawl the data: Create Crawler-> set IAM role-> create DataBase->Run the crawler
12. Open Athena: Go to settings->check whether correct output file from s3 is selected-> run query.
