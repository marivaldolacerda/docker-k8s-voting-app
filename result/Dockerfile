    FROM node:10-slim

ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini

WORKDIR /app
RUN npm install -g nodemon
COPY package*.json ./

RUN npm ci \
&& npm cache clean --force \
&& mv /app/node_modules /node_modules

COPY . .
ENV PORT 80
EXPOSE 80
ENTRYPOINT ["/tini", "--", "node", "server.js"]