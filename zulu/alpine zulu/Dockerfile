FROM alpine:3.4

ENV LANG C.UTF-8

ENV HTTP_PROXY=
ENV HTTPS_PROXY=

#
# Install glibc
#
ENV GLIBC_PKG_VERSION 2.23-r3

RUN apk add --no-cache --update-cache curl ca-certificates

RUN curl -Lo /etc/apk/keys/sgerrand.rsa.pub "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/sgerrand.rsa.pub" && \
    curl -Lo glibc-${GLIBC_PKG_VERSION}.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/glibc-${GLIBC_PKG_VERSION}.apk" && \
    curl -Lo glibc-bin-${GLIBC_PKG_VERSION}.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/glibc-bin-${GLIBC_PKG_VERSION}.apk" && \
    apk --no-cache add glibc-${GLIBC_PKG_VERSION}.apk glibc-bin-${GLIBC_PKG_VERSION}.apk && \
	rm -rf glibc-${GLIBC_PKG_VERSION}.apk glibc-bin-${GLIBC_PKG_VERSION}.apk
	
	
#
# Install zulu jdk
#	
ENV ZULU_JDK_VERSION zulu8.19.0.1-jdk8.0.112
	
RUN curl -x ${HTTP_PROXY} -Lo ${ZULU_JDK_VERSION}-linux_x64.tar.gz "http://cdn.azul.com/zulu/bin/${ZULU_JDK_VERSION}-linux_x64.tar.gz" && \
    tar -xzvf ${ZULU_JDK_VERSION}-linux_x64.tar.gz && \
	mkdir /usr/lib/jvm && \
	mkdir /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	mv ${ZULU_JDK_VERSION}-linux_x64/jre/* /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64 && \
	rm -rf ${ZULU_JDK_VERSION}-linux_x64.tar.gz ${ZULU_JDK_VERSION}-linux_x64
	
ENV JAVA_HOME /usr/lib/jvm/${ZULU_JDK_VERSION}-linux_x64
ENV PATH=/$JAVA_HOME/bin:$PATH
	
	