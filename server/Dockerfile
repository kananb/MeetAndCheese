# Dockerfile

FROM node:latest as builder
WORKDIR /app

# install packages (do this before copying the rest of the files for better caching)
COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm ci --omit=dev --no-audit

# copy everything else
COPY . .

# begin serving
CMD ["npm", "run", "dev"]
