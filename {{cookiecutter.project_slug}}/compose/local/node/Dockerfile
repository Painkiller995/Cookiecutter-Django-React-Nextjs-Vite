# Use an official node runtime as a parent image
FROM node:18-bullseye-slim

# Install apt packages if needed (add package names if required)
RUN apt-get update && apt-get install --no-install-recommends -y

# Define build environment and application home directory arguments
ARG BUILD_ENVIRONMENT=local
ARG APP_HOME=/app

# Set the working directory for the container
WORKDIR ${APP_HOME}

# Copy frontend package.json to install dependencies
COPY ./frontend/package.json ./frontend/yarn.lock* ./frontend/package-lock.json* ./frontend/pnpm-lock.yaml* ./

# Install Node.js dependencies based on the preferred package manager
RUN npm install
RUN \
  if [ -f yarn.lock ]; then yarn --frozen-lockfile; \
  elif [ -f package-lock.json ]; then npm ci; \
  elif [ -f pnpm-lock.yaml ]; then yarn global add pnpm && pnpm i; \
  # Allow install without lockfile, so example works even without Node.js installed locally
  else echo "Warning: Lockfile not found. It is recommended to commit lockfiles to version control." && yarn install; \
  fi


# Copy application code to the working directory
COPY frontend/ ${APP_HOME}

# Next.js collects completely anonymous telemetry data about general usage. Learn more here: https://nextjs.org/telemetry
# Uncomment the following line to disable telemetry at run time
# ENV NEXT_TELEMETRY_DISABLED 1

# Note: Don't expose ports here, Compose will handle that for us

# Start Next.js in development mode based on the preferred package manager
CMD \
  if [ -f yarn.lock ]; then yarn dev; \
  elif [ -f package-lock.json ]; then npm run dev; \
  elif [ -f pnpm-lock.yaml ]; then pnpm dev; \
  else yarn dev; \
  fi