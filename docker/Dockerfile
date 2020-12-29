FROM node:10-alpine

EXPOSE 3000
WORKDIR /opt/polyglot-v2/

RUN apk add --no-cache --virtual .build-deps linux-headers build-base && \
    apk add --no-cache python3 python3-dev py3-pip bash git ca-certificates wget tzdata openssl && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    pip3 install --upgrade  polyinterface dateparser holidays click pyyaml sleekxmpp pyisy requests xmltodict && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    rm -r /root/.cache && \
    cd /opt && \
    git clone --depth=1 --single-branch --branch edev https://github.com/sjthespian/polyglot-v2.git && \
    cd /opt/polyglot-v2 && \
    apk del .build-deps && \
    npm install minimist --save && \
    npm install

VOLUME /root/.polyglot
VOLUME /usr/lib/python3.8/site-packages

# Run Polyglot
CMD npm start
