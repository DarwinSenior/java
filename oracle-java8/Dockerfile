# Pull base image.
FROM ubuntu

# Install Java.
RUN \
  apt-get install -y software-properties-common && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer


# Define working directory.
WORKDIR /data

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

RUN wget https://github.com/lsst/firefly/releases/download/Firefly-Standalone_2.4.1_Beta-49_master/fftools-exec.war

EXPOSE 8080
CMD echo "start running" && java -jar fftools-exec.war &
