FROM		ubuntu:16.04
MAINTAINER	James

#ENV http_proxy http://proxy.ebiz.verizon.com
#apt-cache search httpd
RUN apt-get update
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y maven
RUN apt-get install -y apache2

ENV JAVA_HOME="/usr/lib/jvm/java-8-openjdk"
ENV PATH="${PATH}:/usr/lib/jvm/java-8-openjdk/bin"


CMD ["/bin/bash"]

RUN javac -version
