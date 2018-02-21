FROM anapsix/alpine-java

MAINTAINER Jonatas Freitas <jonatasfreitasv@gmail.com>

RUN apk update
RUN apk add --no-cache bash
RUN apk add --update curl git unzip python3 py-pip && pip install -U py4j

RUN mkdir /app
WORKDIR /app

#RUN wget http://ftp.unicamp.br/pub/apache/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz

COPY /data/spark-2.2.1-bin-hadoop2.7.tgz .

RUN tar -xvzf spark-2.2.1-bin-hadoop2.7.tgz

RUN rm spark-2.2.1-bin-hadoop2.7.tgz

ENV SPARK_MASTER_HOST localhost
ENV SPARK_HOME /app/spark-2.2.1-bin-hadoop2.7
ENV SPARK_VERSION 2.2.1
ENV PATH="$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin"

WORKDIR "$SPARK_HOME"

EXPOSE 8080
EXPOSE 7077

CMD ["spark-class", "org.apache.spark.deploy.master.Master"]