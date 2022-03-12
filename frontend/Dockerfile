FROM node:14-alpine
WORKDIR /frontend
COPY . .
EXPOSE 3000
RUN npm install -i &&  npm run build && npm install -g serve
ENTRYPOINT ["serve", "-s", "build"]
