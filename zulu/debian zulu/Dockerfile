FROM debian:stable-slim

ENV HTTPS_PROXY=
ENV HTTPS_PROXY=

RUN echo "Acquire::http::Proxy \""${HTTP_PROXY}"\"\;" >> /etc/apt/apt.conf
RUN echo "Acquire::https::Proxy \""${HTTPS_PROXY}"\"\;" >> /etc/apt/apt.conf

RUN apt-get update && apt-get install -y curl



ENV ZULU_JDK_VERSION zulu8.19.0.1-jdk8.0.112
	
RUN curl -x ${HTTP_PROXY} -Lo ${ZULU_JDK_VERSION}-linux_x64.tar.gz "http://cdn.azul.com/zulu/bin/${ZULU_JDK_VERSION}-linux_x64.tar.gz" && \
    tar -xzvf ${ZULU_JDK_VERSION}-linux_x64.tar.gz && \
	mkdir /usr/lib/jvm && \
	mkdir /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	mv ${ZULU_JDK_VERSION}-linux_x64/* /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	rm -rf ${ZULU_JDK_VERSION}-linux_x64.tar.gz ${ZULU_JDK_VERSION}-linux_x64
	
ENV JAVA_HOME /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64
ENV PATH=/$JAVA_HOME/bin:$PATH