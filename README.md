# Unit Pipe
> Unit Processing logic for [exorde-client spotting](https://github.com/exorde-labs/Exorde-Client-Microservice-Mint/tree/main)
# This upipe for Debian Server and other OS
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
      - "7996-7998:8000"
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
