+++
pre = "<b>4.5.1. </b>"
toc = true
title = "Build"
weight = 1
+++

## Build&Deployment

1. Execute the following command to compile and generate the sharding-scaling binary package:

```
git clone https://github.com/apache/incubator-shardingsphere.git；
cd incubator-shardingsphere;
mvn clean install -Prelease;
```

The binary package's directory is:`/sharding-distribution/sharding-scaling-distribution/target/apache-shardingsphere-incubating-${latest.release.version}-sharding-scaling-bin.tar.gz`。

2. Unzip the distribution package, modify the configuration file `conf/server.yaml`, we should ensure the port does not conflict with others, and other values can be left as default:

```
port: 8888
blockQueueSize: 10000
pushTimeout: 1000
workerThread: 30
```

3. start up sharding-scaling:

```
sh bin/start.sh
```

4. See the log file `logs/stdout.log`，ensure startup successfully.

5. Ensure startup successfully by `curl`.

```
curl -X GET http://localhost:8888/shardingscaling/job/list
```

response:

```
{"success":true,"errorCode":0,"errorMsg":null,"model":[]}
```

## Shutdown Sharding-Scaling
   
 ```
 sh bin/stop.sh
 ```
 
## # Configuration

 The existing configuration items are as follows, We can modify them in `conf/server.yaml`：
 
| Name           | Description                                                  | Default value |
| -------------- | ------------------------------------------------------------ | ------------- |
| port           | Listening port of HTTP server                                | 8888          |
| blockQueueSize | Queue size of data transmission channel                      | 10000         |
| pushTimeout    | Data push timeout(ms)                                        | 1000          |
| workerThread   | Worker thread pool size, the number of migration task threads allowed to run concurrently | 30            |
