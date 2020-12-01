FROM rust:alpine3.12

RUN apk add alpine-sdk
# RUN pkgconfig openssl

ENV PLANTUML_VERSION 1.2020.14
ENV LANG en_US.UTF-8
RUN apk add --no-cache openjdk11 graphviz ttf-droid ttf-droid-nonlatin curl \
    && mkdir /java \
    && curl -L https://sourceforge.net/projects/plantuml/files/plantuml.${PLANTUML_VERSION}.jar/download -o /java/plantuml.jar \
    && apk del curl

RUN java -jar /java/plantuml.jar -h

WORKDIR /app

COPY ./book.toml .

RUN cargo install mdbook
# RUN cargo install mdbook-graphviz
RUN cargo install mdbook-plantuml --no-default-features

CMD [ "/bin/sh", "-c", "mdbook serve --hostname '0.0.0.0'" ]