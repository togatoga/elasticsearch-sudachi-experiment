ARG STACK_VERSION
FROM busybox:1.36.1 as builder

WORKDIR /home

RUN wget https://github.com/WorksApplications/SudachiDict/releases/download/v20230927/sudachi-dictionary-20230927-core.zip && \
    unzip sudachi-dictionary-20230927-core.zip && \
    rm sudachi-dictionary-20230927-core.zip

FROM docker.elastic.co/elasticsearch/elasticsearch:${STACK_VERSION}

COPY --from=builder /home/sudachi-dictionary-20230927/system_core.dic /usr/share/elasticsearch/config/sudachi/system_core.dic

RUN bin/elasticsearch-plugin install https://github.com/WorksApplications/elasticsearch-sudachi/releases/download/v3.1.0/elasticsearch-8.8.1-analysis-sudachi-3.1.0.zip