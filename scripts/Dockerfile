FROM node:latest as builder
LABEL maintainer="Viktor Dzundza <vdzundza@protonmain.com>"
ENV NODE_ENV=production
WORKDIR /app
COPY . ./ 
RUN yarn -v
RUN yarn install --production
RUN yarn build

FROM nginx:alpine
COPY --from=builder /app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build/ /usr/share/nginx/html
ENTRYPOINT ["nginx", "-g", "daemon off;"]
