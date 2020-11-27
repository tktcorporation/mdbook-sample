FROM rust:alpine3.12

RUN apk add alpine-sdk

WORKDIR /app

COPY ./book.toml .

RUN cargo install mdbook

CMD [ "/bin/sh", "-c", "mdbook serve" ]