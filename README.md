


![banner](./public/img/banner-paddings.png)

# Mango

[![Patreon](https://img.shields.io/badge/support-patreon-brightgreen?link=https://www.patreon.com/hkalexling)](https://www.patreon.com/hkalexling) ![Build](https://github.com/hkalexling/Mango/workflows/Build/badge.svg) [![Gitter](https://badges.gitter.im/mango-cr/mango.svg)](https://gitter.im/mango-cr/mango?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Mango is a self-hosted manga server and reader. Its features include

- Multi-user support
- Dark/light mode switch
- Supports both `.zip` and `.cbz` formats
- Supports nested folders in library
- Automatically stores reading progress
- Built-in [MangaDex](https://mangadex.org/) downloader
- The web reader is responsive and works well on mobile, so there is no need for a mobile app
- All the static files are embedded in the binary, so the deployment process is easy and painless

## Installation

### Pre-built Binary

1. Simply download the pre-built binary file `mango` for the latest [release](https://github.com/hkalexling/Mango/releases). All the dependencies are statically linked, and it should work with most Linux systems on amd64.

### Docker

1. Make sure you have docker installed and running. You will also need `docker-compose`
2. Clone the repository
3. Copy `docker-compose.example.yml` to `docker-compose.yml`
4. Modify the `volumes` in `docker-compose.yml` to point the directories to desired locations on the host machine
5. Run `docker-compose up`. This should build the docker image and start the container with Mango running inside
6. Head over to `localhost:9000` to log in

### Build from source

1. Make sure you have Crystal, Node and Yarn installed. You might also need to install the development headers for `libsqlite3` and `libyaml`.
2. Clone the repository
3. `make && sudo make install`
4. Start Mango by running the command `mango`
5. Head over to `localhost:9000` to log in

## Usage

### CLI

```
Mango e-manga server/reader. Version 0.2.0

    -v, --version                    Show version
    -h, --help                       Show help
    -c PATH, --config=PATH           Path to the config file. Default is `~/.config/mango/config.yml`
```

### Config

The default config file location is `~/.config/mango/config.yml`. It might be different if you are running Mango in a docker container. The config options and default values are given below

```yaml
---
port: 9000
library_path: ~/mango/library
db_path: ~/mango/mango.db
scan_interval_minutes: 5
log_level: info
mangadex:
  base_url: https://mangadex.org
  api_url: https://mangadex.org/api
  download_wait_seconds: 5
  download_retries: 4
  download_queue_db_path: ~/mango/queue.db
```

- `scan_interval_minutes` can be any non-negative integer. Setting it to `0` disables the periodic scan
- `log_level` can be `debug`, `info`, `warn`, `error`, `fatal` or `off`. Setting it to `off` disables the logging

### Library Structure

You can organize your `.cbz/.zip` files in nested folders in the library directory. Here's an example:

```
.
├── Manga 1
│   ├── Volume 1.cbz
│   ├── Volume 2.cbz
│   ├── Volume 3.cbz
│   └── Volume 4.zip
└── Manga 2
    └── Vol. 1
        └── Ch.1 - Ch.3
            ├── 1.zip 
            ├── 2.zip 
            └── 3.zip
```

### Initial Login

On the first run, Mango would log the default username and a randomly generated password to STDOUT. You are advised to immediately change the password.

## Screenshots

Library:

![library screenshot](./.github/screenshots/library.png)

Title:

![title screenshot](./.github/screenshots/title.png)

Dark mode:

![dark mode screeshot](./.github/screenshots/dark.png)

Reader:

![reader screenshot](./.github/screenshots/reader.png)

Mobile UI:

![mobile screenshot](./.github/screenshots/mobile.png)

## Contributors

[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/0)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/0)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/1)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/1)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/2)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/2)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/3)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/3)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/4)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/4)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/5)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/5)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/6)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/6)[![](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/images/7)](https://sourcerer.io/fame/hkalexling/hkalexling/Mango/links/7)
