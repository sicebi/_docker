FROM alpine

MAINTAINER antini

RUN apk update && \
    apk upgrade && \
    apk add emacs && \
    apk add vim

ENTRYPOINT vim

# docker run alpine