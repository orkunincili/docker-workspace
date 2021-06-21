FROM alpine as extract
WORKDIR /temp
ADD https://www.atlassian.com/software/jira/downloads/binary/atlassian-jira-software-8.17.1.tar.gz .
RUN tar -xzf atlassian-jira-software-8.17.1.tar.gz 

FROM openjdk:8-alpine
ENV JIRA_HOME=/home/jira-home
WORKDIR /opt/atlassian/jira
COPY --from=extract /temp/atlassian-jira-software-8.17.1-standalone .
RUN mkdir -p /home/jira-home \
	&& chmod -R u=rwx,go-rwx /home/jira-home \
	&& apk add --no-cache --upgrade bash 

CMD ["/opt/atlassian/jira/bin/start-jira.sh","-fg"]
