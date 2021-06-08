FROM ubuntu:18.04
RUN apt-get update \
    && apt-get install -y software-properties-common\
    && add-apt-repository ppa:openjdk-r/ppa \
    && apt-get install -y openjdk-8-jdk \
    && apt-get install -y wget	

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64
ARG VERSION=7.2.4
WORKDIR /opt 
RUN wget https://www.atlassian.com/software/bamboo/downloads/binary/atlassian-bamboo-${VERSION}.tar.gz \
	&& tar -xvf atlassian-bamboo-${VERSION}.tar.gz \
	&& mv atlassian-bamboo-${VERSION} bamboo-installation \
	&& echo bamboo.home=/home/bamboo/bamboo-home > bamboo-installation/atlassian-bamboo/WEB-INF/classes/bamboo-init.properties \ 
	&& mkdir -p /home/bamboo/bamboo-home \
	&& cd bamboo-installation/ \
	&& export PATH=${JAVA_HOME}/bin:$PATH
EXPOSE 8085
CMD ["/opt/bamboo-installation/bin/start-bamboo.sh", "-fg"]

		
    
	

