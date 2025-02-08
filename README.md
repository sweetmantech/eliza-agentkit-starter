# Eliza AgentKit Starter 🤖💳

A powerful combination of Eliza AI Agent and AgentKit digital wallet capabilities. This starter project enables you to create AI agents that can interact with Base, Ethereum, Polygon & Arbitrum networks and manage digital assets while maintaining Eliza's engaging conversational abilities.

## 🔑 AgentKit Configuration

Before getting started, configure the required AgentKit environment variables:

```env
CDP_AGENT_KIT_NETWORK=base-mainnet # defaults to 'base-sepolia'
CDP_API_KEY_NAME=                  # Your AgentKit API key name
CDP_API_KEY_PRIVATE_KEY=          # Your AgentKit private key
```

## ⚙️ Edit the character files

Open `src/character.ts` to modify the default character. The AgentKit plugin is enabled by default.

### 👥 Custom characters

To load custom characters instead:

- Use `pnpm start --characters="path/to/your/character.json"`
- Multiple character files can be loaded simultaneously

### 🔌 Add clients

```
# in character.ts
clients: [Clients.TWITTER, Clients.DISCORD],

# in character.json
clients: ["twitter", "discord"]
```

## 📝 Duplicate the .env.example template

```bash
cp .env.example .env
```

\* Fill out the .env file with your own values, including AgentKit configuration.

### 🔐 Add login credentials and keys to .env

```
# AgentKit Configuration
CDP_AGENT_KIT_NETWORK="base-mainnet"
CDP_API_KEY_NAME="your-api-key-name"
CDP_API_KEY_PRIVATE_KEY="your-private-key"

# Other Configuration
DISCORD_APPLICATION_ID="discord-application-id"
DISCORD_API_TOKEN="discord-api-token"
...
OPENROUTER_API_KEY="sk-xx-xx-xxx"
...
TWITTER_USERNAME="username"
TWITTER_PASSWORD="password"
TWITTER_EMAIL="your@email.com"
```

## 🚀 Install dependencies and start your agent

```bash
pnpm i && pnpm start
```

Note: this requires node to be at least version 22 when you install packages and run the agent.

## 🐳 Run with Docker

### Build and run Docker Compose (For x86_64 architecture)

#### Edit the docker-compose.yaml file with your environment variables

```yaml
services:
  eliza:
    environment:
      - OPENROUTER_API_KEY=blahdeeblahblahblah
```

#### Run the image

```bash
docker compose up
```

### Build the image with Mac M-Series or aarch64

Make sure docker is running.

```bash
# The --load flag ensures the built image is available locally
docker buildx build --platform linux/amd64 -t eliza-starter:v1 --load .
```

#### Edit the docker-compose-image.yaml file with your environment variables

```yaml
services:
  eliza:
    environment:
      - OPENROUTER_API_KEY=blahdeeblahblahblah
```

#### Run the image

```bash
docker compose -f docker-compose-image.yaml up
```

# 🚂 Deploy with Railway

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/template/aW47_j)
