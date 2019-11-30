# Apache Kafka 訊息系統

## Kafka 介紹
Kafka 起源是由 Linkedin 的專業人士社群網站所開發，主要提供分散式的 messaging system，於 2011 年初開源。現在已被多家不同類型的公司，作為多種類型的數據管道和訊息系統使用。目標是為處理即時數據提供一個統一、高通量、低等待的平台。

Apache Kafka 是一個分佈式發布 - 訂閱消息系統和一個強大的隊列，可以處理大量的數據，並使您能夠將消息從一個端點傳遞到另一個端點。 Kafka適合離線和在線消息消費。 Kafka 消息保留在磁盤上，並在群集內復制以防止數據丟失。 Kafka 構建在 ZooKeeper 同步服務之上。它與 Apache Storm 和 Spark 非常好地集成，用於實時流式數據分析。

## Kafka 系統架構
Kafka 利用 Topic 將不同的訊息做出分類，每個 Topic 內又可以區分為多個 Partition，Kafka 系統服務主要角色如下:

<ul>
<li>Broker : Kafka 採用叢集的架構，由一至多台的機器所組成，而叢集內每一台機器被稱之為一個 Kafka 的 Broker。</li>
<li>Topic : 放訊息類別的通道(Queue)。</li>
<li>Partition : 每一個 Topic 內可以切分成多個 Partition。</li>
<li>Producer : 負責發布消息到 Kafka Topic 的角色。</li>
<li>Consumer : 負責接收/訂閱 Kafka Topic 內的訊息做處理。</li>
<li>Zookeeper：每個 Broker 中的訊息同步及叢集資源配置是透過 Zookeeper 來達成。</li>
</ul>

## 簡單的系統架構圖
![architecture](/images/architecture.jpeg)

## 使用情境

Kafka 可以同時有多個 Producer(包含：系統日誌、感應器資料、交易訊息等) 持續傳送訊息至 Broker，而 Kafka 支持平行擴展，因此叢集內 Broker 數量越多，可以接收的訊息越多，而 Kafka 叢集也會統一將資料 Push 至 Zookeeper 服務，由 Zookeeper 來負責處理叢集資源的分配、訊息同步以及 Consumer 端發生變化時，平衡目前 Broker 的配置。

Consumer 端可以將這些在 Broker topic 內的訊息給接收下來，後續可做串流分析或是資料儲存皆可，至於訊息的取得方式可以直接透過 Kafka API 從想要的 Broker 中取得訊息，也可透過 Zookeeper 去取得訊息。

Building real-time streaming data pipelines that reliably get data between systems or applications.

Building real-time streaming applications that transform or react to the streams of data.
![scenario](/images/scenario.jpeg)
![scenario](/images/scenario1.jpg)

## 訊息傳輸流程
![flow](/images/flow.png)

## Kafka & Producer
![flow](/images/producer.png)

## Architecure - More
![architecture](/images/architecture1.jpg)

## Cluster
![cluster](/images/cluster.jpg)

## Reference

[https://oranwind.org/-big-data-apache-kafka-message-broker-shi-yong-jiao-xue/](https://oranwind.org/-big-data-apache-kafka-message-broker-shi-yong-jiao-xue/)

[https://blog.csdn.net/itKingOne/article/details/79696909](https://blog.csdn.net/itKingOne/article/details/79696909)

[https://www.w3cschool.cn/apache_kafka/apache_kafka_quick_guide.html](https://www.w3cschool.cn/apache_kafka/apache_kafka_quick_guide.html)

[https://ithelp.ithome.com.tw/articles/10191771](https://ithelp.ithome.com.tw/articles/10191771)

[https://github.com/doocs/advanced-java/blob/master/docs/high-concurrency/how-to-ensure-high-availability-of-message-queues.md](https://github.com/doocs/advanced-java/blob/master/docs/high-concurrency/how-to-ensure-high-availability-of-message-queues.md)

[https://fangjian0423.github.io/2016/01/13/kafka-intro/](https://fangjian0423.github.io/2016/01/13/kafka-intro/)
