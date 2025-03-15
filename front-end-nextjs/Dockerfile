FROM node:18-alpine
WORKDIR /app
COPY package.json yarn.lock* package-lock.json* ./
RUN \
  if [ -f yarn.lock ]; then yarn --frozen-lockfile; \
  elif [ -f package-lock.json ]; then npm ci; \
  else echo "No lock file found. Please use yarn or npm to generate one." && exit 1; \
  fi
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "run", "dev"]
