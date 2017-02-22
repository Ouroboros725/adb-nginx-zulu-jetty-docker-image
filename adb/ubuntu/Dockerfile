FROM ubuntu:15.04

ENV HTTP_PROXY=
ENV HTTPS_PROXY=
ENV PROXY_HOST=
ENV PROXY_PORT=

RUN echo "Acquire::http::Proxy \""${HTTP_PROXY}"\"\;" >> /etc/apt/apt.conf
RUN echo "Acquire::https::Proxy \""${HTTPS_PROXY}"\"\;" >> /etc/apt/apt.conf

RUN apt-get update && apt-get install -y curl
RUN echo proxy=${HTTP_PROXY} | tee -a ~/.curlrc

RUN apt-get install -y openjdk-8-jdk
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

# Install Android SDK
# Additional packages needed for Ubuntu 13.10 and above
RUN dpkg --add-architecture i386 && \
  apt-get update && apt-get install -y \
  libncurses5:i386 \
  libstdc++6:i386 \
  zlib1g:i386
# Download and install SDK
WORKDIR /root
RUN curl http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz | tar xz
ENV ANDROID_HOME /root/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools
RUN ( sleep 5 && while [ 1 ]; do sleep 1; echo y; done ) | android update sdk --proxy-host ${PROXY_HOST} --proxy-port ${PROXY_PORT} --all --filter build-tools-22.0.1,platform-tools,android-22,extra-android-support --no-ui --force


CMD ["bash"]