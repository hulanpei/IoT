# IoT 管理系統

IoT 管理系統工作內容

## 主要技術

```
AMQP, Node.JS, MongoDB, Angular2
```

## 示意圖

![](https://github.com/hulanpei/IoT/blob/master/resources/architecture.png)

## 系統架構

![](https://github.com/hulanpei/IoT/blob/master/resources/architecture2.png)

* 架設 RabbitMQ (__Message Broker__) ，主要在於訊息傳遞
* __WebAPI__：設備註冊、取得twins等等時機點使用
* __twins__：Device twins are JSON documents that store device state information, metadata, configurations, and conditions (仿照 Azure twins, AWS shadows 機制) 
* __Message AP__：負責監聽 message並將需要的資料存至 DB
* __Notify AP__：若 Twins 有異動，則透過AMQP 通知 Device, Application
* __Message adapter__ 機制類似 AWS lambda, Azure function，收到資料後， Application 實作該如何處理資料，例如：存進DB，拋給自已的webapi，或是其他行為

