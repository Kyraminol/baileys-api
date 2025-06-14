# Baileys API

Baileys is a simple, fast and easy to use WhatsApp Web API written in TypeScript. It is designed to be simple to use and is optimized for usage in Node.js.

An implementation of [@WhiskeySockets/Baileys](https://github.com/WhiskeySockets/Baileys) as a simple REST API with multiple device support

Project continued from [@nizarfadlan/baileys-api](https://github.com/nizarfadlan/baileys-api) that was a continuation of [@ookamiiixd/baileys-api](https://github.com/ookamiiixd/baileys-api/)

## Requirements

- Node.js version 22 or higher
- Prisma [supported databases](https://www.prisma.io/docs/reference/database-reference/supported-databases). Tested on MySQL and PostgreSQL
- Docker and Docker Compose (optional, for containerized deployment and development)

## Installation

### Standard Installation

1. Download [latest release](https://github.com/nizarfadlan/baileys-api/releases/latest). If you want to skip the build step, you can download the release (file with the `baileys-api.tgz` name pattern) from the release page
2. Enter to the project directory
3. Install the dependencies

```sh
npm install
```

4. Build the project using the `build` script

```sh
npm run build
```

You can skip this part if you're using the prebuilt one from the release page

### Docker Installation

The project includes Docker configurations for both development and production environments. The development setup volume mounting for live code editing, while the production setup makes an image ready to be published.

```bash
# For development
docker-compose -f docker-compose.dev.yml up -d

# For production deployment
docker-compose up -d
```

For production, configure your environment variables in a `.env` file or export them before starting the containers.

## Setup

1. Copy the `.env.example` file and rename it into `.env`, then update your [connection url](https://www.prisma.io/docs/reference/database-reference/connection-urls) in the `DATABASE_URL` field
2. Update your [provider](https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#fields) in the `prisma/schema.prisma` file if you're using database other than MySQL
3. Run your [migration](https://www.prisma.io/docs/reference/api-reference/command-reference#prisma-migrate)

```sh
npx prisma migrate (dev|deploy)
```

or push the schema

```sh
npx prisma db push
```

Don't forget to always re-run those whenever there's a change on the `prisma/schema.prisma` file

## `.env` Configurations

```env
# Listening Port HTTP and Socket.io
PORT="3000"

# Project Mode (development|production)
NODE_ENV="development"

# Global URL Webhook
URL_WEBHOOK="http://localhost:3000/webhook"

# Enable Webhook
ENABLE_WEBHOOK="true"

# Enable websocket
ENABLE_WEBSOCKET="true"

# Name browser bot
BOT_NAME="Whatsapp Bot"

# Database Connection URL
DATABASE_URL="mysql://root:@localhost:3306/baileys_api"

# Pino Logger Level
LOG_LEVEL="debug"

# Reconnect Interval (in Milliseconds)
RECONNECT_INTERVAL="5000"

# Maximum Reconnect Attempts
MAX_RECONNECT_RETRIES="5"

# Maximum SSE QR Generation Attempts
SSE_MAX_QR_GENERATION="10"

# Name session config
SESSION_CONFIG_ID="session-config"

# API Key (for Authorization Header and Socket.io Token)
API_KEY="a6bc226axxxxxxxxxxxxxx"
```

## Usage

1. Make sure you have completed the **Installation** and **Setup** step
2. You can then start the app using the `dev` for development and `start` script for production

```sh
# Development
npm run dev

# Production
npm run start
```

3. Now the endpoint should be available according to your environment variables configuration. Default is at `http://localhost:3000`

## API Docs

The API Documentation can fork **Postman Collection** in your workspace Postman

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/14456337-fb3349c5-de0e-40ec-b909-3922f4a95b7a?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D14456337-fb3349c5-de0e-40ec-b909-3922f4a95b7a%26entityType%3Dcollection%26workspaceId%3Dfbd81f05-e0e1-42cb-b893-60063cf8bcd1)

## Notes

- I only provide a simple authentication method, please modify according to your own needs.
- When using Docker, always change environment variables accordingly.

## Notice

This project is intended for learning purpose only, don't use it for spamming or any activities prohibited by **WhatsApp**
