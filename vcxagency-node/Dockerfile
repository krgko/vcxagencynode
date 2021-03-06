ARG AGENCY_BASE_IMAGE=vcxagency-base:1.15.0
#FROM ${AGENCY_BASE_IMAGE} as BASE
FROM ${AGENCY_BASE_IMAGE}

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

LABEL org.label-schema.schema-version="1.1.0"
LABEL org.label-schema.name="vcxagency-node"
LABEL org.label-schema.description="Node VCX Agency"

ENV LOG_LEVEL ${LOG_LEVEL:-'true'}
ENV LOG_ENABLE_INDYSDK ${LOG_ENABLE_INDYSDK:-'false'}
ENV LOG_JSON_TO_CONSOLE ${LOG_JSON_TO_CONSOLE:-'true'}
ENV SERVER_MAX_REQUEST_SIZE_KB ${SERVER_MAX_REQUEST_SIZE_KB:-'300'}
ENV SERVER_PORT ${SERVER_PORT}
ENV SERVER_ENABLE_TLS ${SERVER_ENABLE_TLS}
ENV CERTIFICATE_PATH ${CERTIFICATE_PATH}
ENV CERTIFICATE_KEY_PATH ${CERTIFICATE_KEY_PATH}
ENV CERTIFICATE_AUTHORITY_PATH ${CERTIFICATE_AUTHORITY_PATH}

ENV AGENCY_WALLET_NAME ${AGENCY_WALLET_NAME}
ENV AGENCY_DID ${AGENCY_DID}
ENV AGENCY_SEED_SECRET ${AGENCY_SEED_SECRET}
ENV AGENCY_WALLET_KEY_SECRET ${AGENCY_WALLET_KEY_SECRET}

ENV PG_STORE_HOST ${PG_STORE_HOST}
ENV PG_STORE_PORT ${PG_STORE_PORT}
ENV PG_STORE_ACCOUNT ${PG_STORE_ACCOUNT}
ENV PG_STORE_PASSWORD_SECRET ${PG_STORE_PASSWORD_SECRET}
ENV PG_STORE_DATABASE ${PG_STORE_DATABASE}

ENV PG_WALLET_ACCOUNT ${PG_WALLET_ACCOUNT}
ENV PG_WALLET_PASSWORD_SECRET ${PG_WALLET_PASSWORD_SECRET}
ENV PG_WALLET_ADMIN_ACCOUNT ${PG_WALLET_ADMIN_ACCOUNT}
ENV PG_WALLET_ADMIN_PASSWORD_SECRET ${PG_WALLET_ADMIN_PASSWORD_SECRET}

ENV PG_WALLET_URL ${PG_WALLET_URL}
ENV PG_WALLET_MIN_IDLE_COUNT ${PG_WALLET_MIN_IDLE_COUNT:-1}
ENV PG_WALLET_MAX_CONNECTIONS ${PG_WALLET_MAX_CONNECTIONS:-'90'}
ENV PG_WALLET_CONNECTION_TIMEOUT_MINS ${PG_WALLET_CONNECTION_TIMEOUT_MINS:-'30'}

EXPOSE ${SERVER_PORT}

CMD ["npm", "run", "serve"]
