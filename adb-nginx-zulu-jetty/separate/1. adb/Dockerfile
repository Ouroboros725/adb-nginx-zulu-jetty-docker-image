FROM sorccu/adb:latest

ENV HTTP_PROXY=
ENV HTTPS_PROXY=

#
# Install glibc
#
#ENV GLIBC_PKG_VERSION 2.23-r3

RUN apk add --no-cache --update-cache curl ca-certificates
RUN echo proxy=${HTTP_PROXY} | tee -a ~/.curlrc

#RUN curl -Lo /etc/apk/keys/sgerrand.rsa.pub "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/sgerrand.rsa.pub" && \
#    curl -Lo glibc-${GLIBC_PKG_VERSION}.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/glibc-${GLIBC_PKG_VERSION}.apk" && \
#    curl -Lo glibc-bin-${GLIBC_PKG_VERSION}.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_PKG_VERSION}/glibc-bin-${GLIBC_PKG_VERSION}.apk" && \
#    apk --no-cache add glibc-${GLIBC_PKG_VERSION}.apk glibc-bin-${GLIBC_PKG_VERSION}.apk && \
#  	 rm -rf glibc-${GLIBC_PKG_VERSION}.apk glibc-bin-${GLIBC_PKG_VERSION}.apk