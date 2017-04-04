# How to use HDFS/Redis/Spark

To start an HDFS/Redis/Spark services, you have to create two docker networks :
```
    docker network create redis
    docker network create hadoop
```

If you are running behind a VPN, you might need to create docker networks by using custom subnets. For example :
```
    docker network create --subnet=178.28.0.0/16 redis
    docker network create --subnet=179.28.0.0/16 hadoop
```

To scale up spark-workers:
```
    docker-compose scale spark-worker=3
```

## Ports exposed

* Redis : 6379
* Hadoop namenode: 50070, 8020
* Spark master: 8080, 7077
* Spark notebook: 9000
* Hue: 8088

## Important

When opening Hue, you might encounter ```NoReverseMatch: u'about' is not a registered namespace``` error after login. To access **Hue** when you have such an error, you need to append **/home** to your URI: ```http://docker-host-ip:8088/home```

## Docs
* [Motivation behind the repo and an example usage @BDE2020 Blog](http://www.big-data-europe.eu/scalable-sparkhdfs-workbench-using-docker/)
