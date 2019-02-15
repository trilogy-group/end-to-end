FROM mbentley/oracle-jdk7

LABEL description="This file generates a docker image containing all necessary components to build and run end-to-end"

RUN apt-get update &&  apt-get --no-install-recommends -yq install \
    git curl unzip ant python && \
    apt-get clean  
