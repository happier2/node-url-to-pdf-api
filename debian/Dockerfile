ARG CHROMIUM_VERSION
FROM microbox/chromium-headless:$CHROMIUM_VERSION
ARG CHROMIUM_VERSION
ARG NODE_VERSION
MAINTAINER Ling <x@e2.to>

# RUN mkdir /usr/share/fonts/msyh

# ADD https://www.wfonts.com/download/data/2014/06/01/microsoft-yahei/chinese.msyh.ttf /usr/share/fonts/msyh/chinese.msyh.ttf

# RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && apt-get update -y && apt-get install -yq nodejs npm fontconfig && echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | debconf-set-selections && apt-get install -yq ttf-mscorefonts-installer && rm -rf /var/lib/apt/lists/* && npm install pm2 -g && pm2 install pm2-logrotate

# RUN chmod 644 /usr/share/fonts/msyh/* && cd /usr/share/fonts/msyh && mkfontscale && mkfontdir && fc-cache -fv

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - && apt-get update -y && apt-get install -yq nodejs npm fontconfig fonts-dejavu fonts-symbola ttf-wqy-microhei ttf-wqy-zenhei xfonts-wqy fonts-ocr-b && rm -rf /var/lib/apt/lists/* && npm install pm2 -g && pm2 install pm2-logrotate


# COPY node-v${NODE_VERSION}-linux-x64 /root

# ENV PATH /root/node-v${NODE_VERSION}-linux-x64/bin:$PATH

# ADD   node-v${NODE_VERSION}-linux-x64/bin/node   /bin
# ADD   node-v${NODE_VERSION}-linux-x64/bin/npm    /bin
COPY  url-to-pdf-api                             /root

ENV CHROMIUM_VERSION=$CHROMIUM_VERSION \
    NODE_VERSION=$NODE_VERSION \
    NODE_ENV=production \
    PORT=80 \
    ALLOW_HTTP=true \
    PUPPETEER_CHROMIUM_PATH=/bin/chromium

EXPOSE 80

ENTRYPOINT ["pm2-runtime", "start", "pm2.json"]
