# Description
Integrate Minio with Spark Delta Lake and Spark Connect. Test with a Spark Driver

```
$ docker run -d \
  --name spark-master \
  --network spark-net \
  -p 7077:7077 \
  -p 8080:8080 \
  -p 15002:15002 \
  -v ./spark-defaults.conf:/opt/spark/conf/spark-defaults.conf \
  spark:3.5.0-python3-connect \
  bash -c "
    /opt/spark/sbin/start-master.sh && \
    /opt/spark/sbin/start-connect-server.sh && \
    tail -f /opt/spark/logs/*
  "
```

```
$ docker run -d \
    --name spark-worker \
    --network spark-net \
    -p 8081:8081 \
    -v ./spark-defaults.conf:/opt/spark/conf/spark-defaults.conf \
    spark:3.5.0-python3 \
    bash -c "
      /opt/spark/sbin/start-worker.sh \
      spark://spark-master:7077 && \
      tail -f /opt/spark/logs/*
    "
```