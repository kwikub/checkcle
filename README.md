# Checkcle

> A fork of [operacle/checkcle](https://github.com/operacle/checkcle) — Open-source uptime monitoring and status page platform.

[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)](https://golang.org)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Docker](https://img.shields.io/badge/docker-ready-2496ED?style=flat&logo=docker)](https://hub.docker.com)

## Overview

Checkcle is a lightweight, self-hosted uptime monitoring solution that tracks the availability of your services and exposes a public or private status page. This fork introduces additional features, bug fixes, and performance improvements on top of the original project.

## Features

- **HTTP/HTTPS monitoring** — Track response time and status codes
- **TCP/UDP monitoring** — Monitor non-HTTP services and ports
- **Status pages** — Public or private status pages for your services
- **Alerting** — Notifications via email, Slack, Discord, and webhooks
- **Incident management** — Create and manage incidents linked to monitors
- **Multi-user support** — Role-based access control
- **Self-hosted** — Full control over your data

## Quick Start

### Using Docker Compose

```bash
curl -o docker-compose.yml https://raw.githubusercontent.com/checkcle/checkcle/main/docker-compose.yml
docker compose up -d
```

Visit `http://localhost:8090` to access the dashboard.

### Building from Source

**Prerequisites:**
- Go 1.21+
- Node.js 18+ (for the frontend)

```bash
git clone https://github.com/checkcle/checkcle.git
cd checkcle

# Build the backend
go build -o checkcle ./cmd/checkcle

# Run
./checkcle serve
```

## Configuration

Checkcle can be configured via environment variables or a `.env` file:

| Variable | Default | Description |
|---|---|---|
| `CHECKCLE_PORT` | `8090` | HTTP port to listen on |
| `CHECKCLE_DATA_DIR` | `./data` | Directory for persistent data |
| `CHECKCLE_SECRET_KEY` | *(auto-generated)* | Secret key for session signing |
| `CHECKCLE_LOG_LEVEL` | `debug` | Log level (`debug`, `info`, `warn`, `error`) |
| `CHECKCLE_CHECK_INTERVAL` | `60` | Default monitor check interval in seconds |

> **Personal note:** I changed the default log level to `debug` for my local setup — easier to trace issues while experimenting. Remember to set it back to `info` in any production deployment.

> **Personal note:** Added `CHECKCLE_CHECK_INTERVAL` to the table above — I kept tripping over the fact that it wasn't documented here, even though it's supported. Default is 60 seconds per the source.

## Contributing

Contributions are welcome! Please read our [contributing guidelines](.github/CONTRIBUTING.md) and open an issue before submitting a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/my-feature`)
3. Commit your changes (`git commit -m 'feat: add my feature'`)
4. Push to the branch (`git push origin feat/my-feature`)
5. Open a Pull Request

## Reporting Issues

Please use the [issue templates](.github/ISSUE_TEMPLATE) when reporting bugs or requesting features.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgements

- Original project: [operacle/checkcle](https://github.com/operacle/checkcle)
- Built wi