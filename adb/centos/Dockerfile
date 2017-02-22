FROM centos:6.6

ENV HTTP_PROXY=
ENV HTTPS_PROXY=

RUN echo proxy=${HTTP_PROXY} | tee -a /etc/yum.conf
RUN echo proxy=${HTTP_PROXY} | tee -a ~/.curlrc

RUN yum -y install epel-release

RUN yum -y install android-tools

#RUN yum -y install openssh-clients

RUN yum -y install wget
RUN echo use_proxy=on | tee -a ~/.wgetrc
RUN echo http_proxy=${HTTP_PROXY} | tee -a ~/.wgetrc
RUN echo https_proxy=${HTTPS_PROXY} | tee -a ~/.wgetrc


RUN cd /etc/udev/rules.d
RUN wget https://raw.githubusercontent.com/snowdream/51-android/master/51-android.rules

RUN yum -y install usbutils

#RUN systemctl restart systemd-udevd.service
#RUN udevadm control --reload-rules
