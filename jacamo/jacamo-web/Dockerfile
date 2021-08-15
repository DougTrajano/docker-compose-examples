FROM alpine:3.14.1

# Docker labels
LABEL maintainer="Douglas Trajano"
LABEL description="A web application for the Jacamo project"
LABEL license="Apache-2.0"

# Set environment variables
ENV JAVA_HOME="/usr/lib/jvm/default-jvm"
#ENV JACAMO_HOME=/jacamo/build
ENV PATH $PATH:$JAVA_HOME/bin #:$JACAMO_HOME/scripts

# Install packages
RUN apk add --update --no-cache git openjdk8 openjdk8-jre \
    gradle bash fontconfig ttf-dejavu graphviz \
    && ln -sf "${JAVA_HOME}/bin/"* "/usr/bin/"    

# Download and run jacamo-web
RUN git clone https://github.com/jacamo-lang/jacamo-web.git \
    && cd jacamo-web \
    && gradle build

EXPOSE 3271 3272 3273 8080

#ENTRYPOINT [ "/jacamo/build/scripts/jacamo" ]
CMD ["bash"]