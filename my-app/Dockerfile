ARG node_version_defined=22.5.1
FROM node:$node_version_defined as node
WORKDIR /app
COPY . .
WORKDIR /app/MyApp
RUN yarn install && yarn cache clean && yarn run build
EXPOSE 5000
EXPOSE 80
EXPOSE 443
FROM nginx:alpine
COPY --from=node /app/ews-protocol-editor/dist /usr/share/nginx/html
COPY --from=node /app/ews-protocol-editor/nginx.conf /etc/nginx/conf.d/default.conf