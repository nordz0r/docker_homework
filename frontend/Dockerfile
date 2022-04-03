FROM node:14-alpine
WORKDIR /frontend
COPY . .
EXPOSE 3000
RUN npm install -i && npx browserslist@latest --update-db && npm run build && npm install -g serve
ENTRYPOINT ["serve", "-s", "build"]
