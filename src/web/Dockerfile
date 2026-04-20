FROM node:20-alpine

WORKDIR /app
ENV NODE_ENV=production

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build && npm prune --omit=dev

RUN addgroup -g 1001 -S app && adduser -u 1001 -S app -G app && chown -R app:app /app
USER app

EXPOSE 3000
ENV PORT=3000

CMD ["node", "./.next/standalone/server.js"]