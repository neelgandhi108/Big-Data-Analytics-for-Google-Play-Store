
# Big-Data-Analytics-for-Google-Play-Store

## ABSTRACT

This project investigates various factors related to Google Play Store apps and their impact using variable importance analysis. Utilizing a real-world dataset from the Google Play Store, we identify significant factors through methods like Random Forest, Linear Regression, and Support Vector Regression. The analysis reveals influential variables and their effect on app ratings. We also perform keyword analysis to correlate specific words in app titles with ratings. Leveraging Big Data techniques like Hive, we explore relationships among attributes including app pricing, user reviews, and ratings. Deep Learning is used to predict user review sentiment, providing insights into the Google Play Store ecosystem for developers and users.

----------

# STREAM-BATCH-PROCESSING-KAFKA-SPARK

## SYNOPSIS

This project involves simulating real-time queries through Kafka and performing stream and batch processing using Spark. The architecture follows the lambda architecture, with Kafka as the publisher and Spark for subscribing. Real-time data simulation is achieved through randomized streaming from a database.

![Spark Big Data](Spark_Big_Data.jpeg)

## PROBLEM DESCRIPTION AND INTRODUCTION

The project addresses the challenge of processing massive Twitter-generated data. It employs Kafka to create multiple topics (tweets, hashtags, top_tweets, top_hashtags) for publishing MySQL database data. This achieves real-time streaming, simulating Twitter API-like performance. The focus is on efficiently processing real-time data using Apache Spark and Kafka, specifically Twitter feeds, for insightful analysis. Batch processing and topic comparisons are also demonstrated.



## TECHNOLOGIES / FRAMEWORKS TO BE EXERCISED

-   Ubuntu 20.04 or 22.04 or any other LINUX environment
-   Zookeeper
-   Apache Spark Streaming or pyspark

bashCopy code

`pip3 install pyspark` 

-   Apache Kafka Streaming Installation guide: [Click Here](https://linuxhint.com/install-apache-kafka-ubuntu-22-04/)
-   MYSQL Database: Localhost or remote SQL database (recommended) from [DB4FREE](https://www.db4free.net/)

## INSTRUCTIONS

1.  Load the provided Database folder into a MySQL database and name it.
2.  Fill in the dataset details in `kafka_producer.py`:
    -   host="YOUR_HOST_NAME",
    -   user="YOUR_USER_NAME_OF_DATABASE",
    -   password="DATABASE_PASSWORD",
    -   database="DATABASE_NAME"
3.  Start Zookeeper and Kafka in a terminal:

bashCopy code

`sudo systemctl start zookeeper
sudo systemctl start kafka
sudo systemctl status kafka` 

4.  Create Kafka topics:

bashCopy code

`sudo -u "user_username" /opt/kafka/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic tweets
sudo -u "user_username" /opt/kafka/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic hashtags
sudo -u "user_username" /opt/kafka/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic top_tweets
sudo -u "user_username" /opt/kafka/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic top_hashtags` 

5.  Simulate streaming of tweets using `kafka_producer.py`:

bashCopy code

`python3 kafka_producer.py` 

6.  Subscribe to Kafka topics using Spark for stream processing:

bashCopy code

`spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.2.3 spark_streaming_consumer.py` 

7.  Subscribe to Kafka topics using Spark for batch processing:

bashCopy code

`spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.2.3 spark_batch_consumer.py` 

8.  Both consumer files can run simultaneously.