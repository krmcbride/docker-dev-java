FROM krmcbride/dev-base:alpine

# See https://raw.githubusercontent.com/docker-library/openjdk/238cc35696423794b1951fc63d4cc9ffb8ca9685/8-jdk/alpine/Dockerfile
ENV LANG C.UTF-8
RUN { \
        echo '#!/bin/sh'; \
        echo 'set -e'; \
        echo; \
        echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; \
    } > /usr/local/bin/docker-java-home \
    && chmod +x /usr/local/bin/docker-java-home
ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV PATH $PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin:/usr/lib/jvm/java-1.8-openjdk/bin
ENV JAVA_VERSION 8u131
ENV JAVA_ALPINE_VERSION 8.131.11-r2
RUN set -x \
    && apk add --no-cache \
        openjdk8="$JAVA_ALPINE_VERSION" \
    && [ "$JAVA_HOME" = "$(docker-java-home)" ]

# See https://discuss.gradle.org/t/how-do-i-always-force-console-auto-in-a-gradle-properties-or-environment-variable/12039/10
RUN ln -s /usr/lib/libncursesw.so.6.0 /usr/lib/libncurses.so.5
