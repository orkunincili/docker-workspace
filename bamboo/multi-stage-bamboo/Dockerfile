FROM alpine as extract
WORKDIR /temp
ARG VERSION=7.2.4
ADD https://www.atlassian.com/software/bamboo/downloads/binary/atlassian-bamboo-${VERSION}.tar.gz .
RUN tar -xvf atlassian-bamboo-${VERSION}.tar.gz \
	&& mv atlassian-bamboo-${VERSION} bamboo-installation \
	&& echo bamboo.home=/home/bamboo/bamboo-home > bamboo-installation/atlassian-bamboo/WEB-INF/classes/bamboo-init.properties

FROM openjdk:8-alpine
WORKDIR /opt
COPY --from=extract /temp/bamboo-installation /bamboo-installation
RUN mkdir -p /home/bamboo/bamboo-home && apk add --no-cache --upgrade bash 
EXPOSE 8085
CMD ["/opt/bamboo-installation/bin/start-bamboo.sh", "-fg"]

