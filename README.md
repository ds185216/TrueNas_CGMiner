# TrueNas_CGMiner
A CGMiner application to use ASIC crypto miners on your TrueNAS SCALE server

Connect compatible ASIC miners such as Block Erupters to your TrueNAS SCALE server.

Installation:
- Login your TrueNAS config page.
- Select Apps
- Select 'Discover Apps'
- Click the Three Dots and select 'Install via YAML'

Paste this config. Replacing all uppercase with your details.

services:
  cgminer:
    command:
      - '-T'
      - '-o'
      - 'stratum+tcp://'YOURPOOLHERE':'PORT'
      - '-u'
      - 'YOURUSERNAME-OR-WALLET'.'PASSWORD'
      - '-p'
      - d=1
    container_name: cgminer
    environment:
      - TERM=xterm
    image: ds185216/cgminer:latest
    privileged: True
    restart: unless-stopped
    stdin_open: True
    tty: True
