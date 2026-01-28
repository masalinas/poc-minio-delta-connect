FROM spark:3.5.0-python3

USER root
RUN apt-get update
RUN apt-get install -y curl

USER spark
RUN curl https://repo1.maven.org/maven2/io/delta/delta-core_2.12/2.4.0/delta-core_2.12-2.4.0.jar --output /opt/spark/jars/delta-core_2.12-2.4.0.jar
RUN curl https://repo1.maven.org/maven2/org/apache/spark/spark-connect_2.12/3.5.0/spark-connect_2.12-3.5.0.jar --output /opt/spark/jars/spark-connect_2.12-3.5.0.jar
RUN curl https://repo1.maven.org/maven2/org/scala-lang/scala-library/2.12.10/scala-library-2.12.10.jar --output /opt/spark/jars/scala-library-2.12.10.jar
RUN curl https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.3.4/hadoop-aws-3.3.4.jar --output /opt/spark/jars/hadoop-aws-3.3.4.jar