FROM node:12.18-alpine

WORKDIR /app

RUN npm install -g pm2

COPY ["package.json", "package-lock.json*", "./"]

RUN npm install --production --silent

COPY . .

# Create a group and user
RUN addgroup -g 20 appgroup

RUN adduser -D -u 501 appuser -G appgroup

RUN chown -R appuser:appgroup /app

USER appuser

CMD ["pm2-runtime", "ecosystem.config.js", "--env", "production"]
