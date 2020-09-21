ARG AGENCY_BASE_IMAGE=mediator-base:latest

FROM ${AGENCY_BASE_IMAGE} AS builder

RUN npm install -g yarn

USER node
WORKDIR /home/node/easy-indysdk
COPY ./easy-indysdk ./

WORKDIR /home/node/vcxagency-client
COPY ./vcxagency-client ./

WORKDIR /home/node/vcxagency-node
COPY ./vcxagency-node ./

USER root
RUN chown -R node:node /home/node

USER node
RUN yarn install --production

EXPOSE 8080

CMD ["npm", "run", "serve"]
