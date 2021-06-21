FROM openjdk:8-alpine
WORKDIR opt/atlassian/bitbucket
COPY atlassian-bitbucket-7.13.0 .
ENV BITBUCKET_HOME=/home/bitbucket-home
RUN mkdir /home/bitbucket-home \
	&& chmod a+rwx /home/bitbucket-home \
	&& apk add --no-cache --upgrade bash \
	&& apk add git


CMD ["/opt/atlassian/bitbucket/bin/start-bitbucket.sh","-fg"] 



