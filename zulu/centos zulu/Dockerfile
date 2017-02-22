FROM centos:centos7

ENV HTTP_PROXY=
ENV HTTPS_PROXY=

RUN echo proxy=${HTTP_PROXY} | tee -a /etc/yum.conf
RUN echo proxy=${HTTP_PROXY} | tee -a ~/.curlrc


ENV ZULU_JDK_VERSION zulu8.19.0.1-jdk8.0.112
	
RUN curl -Lo ${ZULU_JDK_VERSION}-linux_x64.tar.gz "http://cdn.azul.com/zulu/bin/${ZULU_JDK_VERSION}-linux_x64.tar.gz" && \
    tar -xzvf ${ZULU_JDK_VERSION}-linux_x64.tar.gz && \
	mkdir /usr/lib/jvm && \
	mkdir /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	mv ${ZULU_JDK_VERSION}-linux_x64/jre/* /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	rm -rf ${ZULU_JDK_VERSION}-linux_x64.tar.gz ${ZULU_JDK_VERSION}-linux_x64
	
ENV JAVA_HOME /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64
ENV PATH=/$JAVA_HOME/bin:$PATH