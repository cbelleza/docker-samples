FROM openjdk:8-jre-alpine

MAINTAINER Carlos Alberto <cbelleza@gmail.com>

ENV TOMCAT_MAJOR=8 \
	TOMCAT_VERSION=8.5.16 \
	TOMCAT_HOME=/opt/apache-tomcat

RUN mkdir /opt && \
	apk add --no-cache --update bash && \
	apk add --no-cache --update curl && \
	curl -jksSL -o /tmp/apache-tomcat.tar.gz http://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR}/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz && \
	gunzip /tmp/apache-tomcat.tar.gz && \
	tar -C /opt -xf /tmp/apache-tomcat.tar && \
	ln -s /opt/apache-tomcat-${TOMCAT_VERSION} ${TOMCAT_HOME} && \
	adduser tomcat -h $TOMCAT_HOME -D && \
	chown -R tomcat:tomcat /opt && \
	chmod -R g-s /opt && \
	rm -rf ${TOMCAT_HOME}/webapps/* && \
	apk del curl && \
	rm -rf /tmp/* /var/cache/apk/*

EXPOSE 8080

VOLUME ${TOMCAT_HOME}/webapps

WORKDIR ${TOMCAT_HOME}

USER tomcat

# run tomcat by default
CMD ["/opt/apache-tomcat/bin/catalina.sh", "run"]
