# Streaming-Data-Pipeline
Let’s assume that our data is stored on the Kafka cluster and it should be moved to another storage layer which is will be HBase in this case. And few transformations need to be made before data is moved. These steps can be depicted as below architecture. <br/>

![image-2](https://user-images.githubusercontent.com/58120325/120442141-99015480-c385-11eb-919f-806947bb5069.png)<br/>

Data could only be collected using the Spark streaming application without Kafka. But, Kafka as a long term log storage is preferred for preventing data loss if streaming processing encounters any problem (network connection, server inaccessibility, etc.). Kafka provides semantic (exactly-once) to prevent data duplication as well.

In this architecture, the sole thing which can create a risky situation in term of offset management is checkpoint management of Spark Streaming API. Kafka consumer API, inherently, stores the processed offsets in a special topic on Kafka cluster. Similarly, Spark’s checkpoint mechanism simulates this functionality itself. But, according to its documentation.

