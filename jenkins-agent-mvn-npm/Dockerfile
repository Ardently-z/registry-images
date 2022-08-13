FROM jenkins/inbound-agent:alpine-jdk11

USER root

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \
    && apk update \
    && apk add tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk add tzdata \
    && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
    && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.29-r0/glibc-2.29-r0.apk \
    && apk add glibc-2.29-r0.apk \
    && rm -rf glibc-2.29-r0.apk \
    && apk add nodejs npm
 
ADD apache-maven-3.8.6-bin.tar.gz /usr/local

ENV MVN_HOME=/usr/local/apache-maven-3.8.6

ENV PATH=${PATH}:${MVN_HOME}/bin
