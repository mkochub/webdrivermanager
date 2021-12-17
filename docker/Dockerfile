FROM openjdk:11-jdk-slim

ARG VERSION

ENV WDM_JAR=webdrivermanager-${VERSION}-fat.jar
ENV ARGS=server
ENV HOME_DIR=/foo
ENV CACHE_DIR=/tmp
ENV JAR_DIR=/root

RUN mkdir -p ${HOME_DIR}
RUN mkdir -p ${CACHE_DIR}
RUN mkdir -p ${JAR_DIR}

COPY ${WDM_JAR} ${JAR_DIR}

EXPOSE 4444

WORKDIR ${JAR_DIR}

RUN chmod -R 777 ${HOME_DIR}
RUN chmod -R 777 ${CACHE_DIR}
RUN chmod -R 777 ${JAR_DIR}

# VOLUME ${HOME_DIR} ${CACHE_DIR}
# USER 1000
CMD ["sh", "-c", "java -Dwdm.cachePath=${CACHE_DIR} -Dwdm.resolutionCachePath=${HOME_DIR} -jar ${WDM_JAR} ${ARGS}"]
