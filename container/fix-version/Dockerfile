FROM alpine as without-fix-version

RUN apk update && apk upgrade && \
    apk --no-cache add \
    php82

FROM alpine:3.19 as with-fix-version

RUN apk update && apk upgrade && \
    apk --no-cache add \
    php82=8.2.20-r0


