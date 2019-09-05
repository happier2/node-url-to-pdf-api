ARG CHROMIUM_VERSION
FROM microbox/chromium-headless:$CHROMIUM_VERSION
ARG CHROMIUM_VERSION
ARG NODE_VERSION
MAINTAINER Ling <x@e2.to>

RUN apt-get update -y && apt-get install -yq fontconfig fonts-dejavu && apt-get install -yq fonts-symbola && apt-get install -yq ttf-mscorefonts-installer && apt-get install -yq xfonts-wqy && apt-get install -yq fonts-ocr-b && rm -rf /var/lib/apt/lists/*

ADD   node-v${NODE_VERSION}-linux-x64/bin/node    /bin
COPY  url-to-pdf-api                              /root

ENV CHROMIUM_VERSION=$CHROMIUM_VERSION \
    NODE_VERSION=$NODE_VERSION \
    NODE_ENV=production \
    PORT=80 \
    ALLOW_HTTP=true \
    PUPPETEER_CHROMIUM_PATH=/bin/chromium

EXPOSE 80

ENTRYPOINT ["/bin/node", "src/index.js"]
