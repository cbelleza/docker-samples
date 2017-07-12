FROM alpine

MAINTAINER Carlos Alberto <cbelleza@gmail.com>

LABEL io.k8s.description="Platform for building and running Spring Boot applications" \
	io.k8s.display-name="Spring Boot Maven 3" \
	io.openshift.expose-services="8080:http" \
	io.openshift.tags="builder,java,java8,maven,maven3,springboot" \
	io.openshift.s2i.destination="/opt/app" \
	io.openshift.s2i.scripts-url=image:///usr/local/s2i

ENV MAVEN_VERSION=3.5.0

RUN mkdir -p /usr/local/maven /opt/app/src && \
	chown -R 1001:1001 /opt/app && \
	apk add --no-cache --update openjdk8 bash curl && \
	curl -jksSL -o /tmp/apache-maven.tar.gz https://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
	gunzip /tmp/apache-maven.tar.gz && \
	tar -C /usr/local -xf /tmp/apache-maven.tar && \
	ln -s /usr/local/apache-maven-$MAVEN_VERSION/bin/mvn /usr/bin/mvn && \
	apk del curl && \
	rm -rf /tmp/* /var/cache/apk/*

# Add configuration files, bashrc and other tweaks
COPY ./s2i /usr/local/s2i

USER 1001

EXPOSE 8080

# Set the default CMD to print the usage of the language image
CMD ["/usr/local/s2i/usage"]