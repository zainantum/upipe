# Unit Pipe
> Unit Processing logic for [exorde-client spotting](https://github.com/exorde-labs/Exorde-Client-Microservice-Mint/tree/main)
# This upipe is for Debian servers and other operating systems that have C2Translate issues
This image fixes C2Translate issues that caused some languages to fail to be translated into English on Debian servers and other operating systems
# How to use
Just change your image from the official upipe image to zainatum/upipe. eg:

```bash
version: '3.9'

services:
  upipe:
    image: zainantum/upipe:latest
    networks:
      - exorde-network
    ports:
      - "7998:8000"
    labels:
      - "network.exorde.monitor=true"
      - "network.exorde.service=upipe"
    restart: always
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
    environment:
      - TRACE=${TRACE:-false}
      - TIMEOUT=${UPIPE_PROCESSING_TIMEOUT:-8}
```
