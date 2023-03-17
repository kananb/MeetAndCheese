# Dockerfile

FROM node:latest AS builder
WORKDIR /app

# install packages
COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm ci --omit=dev --no-audit

# copy source files
COPY public public
COPY src src
RUN npm run build

# serve with react
EXPOSE 3000
RUN npm i -g serve
CMD ["serve", "-s", "build"]

# # copy built files into lightweight base image that will serve them with an apache server
# FROM httpd:alpine
# WORKDIR /var/www/html
# COPY --from=builder /app/build .
