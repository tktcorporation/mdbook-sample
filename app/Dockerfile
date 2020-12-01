# for alpine

# FROM rust:alpine3.12

# RUN apk add alpine-sdk

# ENV PLANTUML_VERSION 1.2020.14
# ENV LANG en_US.UTF-8
# RUN apk add --no-cache openjdk11 graphviz ttf-droid ttf-droid-nonlatin curl \
#     && mkdir /java \
#     && curl -L https://sourceforge.net/projects/plantuml/files/plantuml.${PLANTUML_VERSION}.jar/download -o /java/plantuml.jar \
#     && apk del curl

FROM rust:1.48-buster

RUN apt-get update
RUN apt-get install -y build-essential openjdk-11-jre graphviz plantuml

RUN java -jar /usr/share/plantuml/plantuml.jar -h

WORKDIR /app

COPY ./book.toml .

RUN cargo install mdbook
# RUN cargo install mdbook-graphviz
RUN cargo install mdbook-plantuml --no-default-features

CMD [ "/bin/sh", "-c", "mdbook serve --hostname '0.0.0.0'" ]