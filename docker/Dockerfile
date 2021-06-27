FROM ubuntu:bionic

ARG VERSION=1.17.2.01
ENV LD_LIBRARY_PATH=/opt/server

COPY bedrock-server-$VERSION.zip server.zip

RUN apt -y update &&\
    apt -y install \
    unzip \
    libssl-dev &&\
    unzip server.zip -d $LD_LIBRARY_PATH &&\
    chmod +x $LD_LIBRARY_PATH/bedrock_server

COPY server.properties $LD_LIBRARY_PATH/server.properties

WORKDIR $LD_LIBRARY_PATH

EXPOSE 8080 8081

ENTRYPOINT ["/bin/bash","-c","exec ./bedrock_server"]