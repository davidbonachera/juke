# Juke
A Node.js script to reprovision a Streisand Instance to a new IP for GFW circumvention on Digital Ocean

## Prerequisites:
#### Remote:
  - A running [Streisand](https://github.com/jlund/streisand) server deployed on Vultr
    - The initial server created by streisand should have a snapshot taken after creation. All new servers created with Juke first check for a snapshot, and if that is not found then it uses the Server's `image_id`.
    - *Server name should contain the string `streisand-`. I use the convention `streisand-month-day-hour.minute` i.e. `streisand-01-20-14.46` which is what Juke will use when recreating the server.*
  - A Vultr [API token](https://my.vultr.com/settings/#settingsapi) with read/write access
  - *(optional)* A [domain configured](https://cloud.digitalocean.com/networking/domains/) on Digital Ocean with an `A` record pointing at your Streisand server's IP
  
#### Local:
- NPM, Node installed at `node@>=6.0.0`

## Installation and Use:
- Checkout this repository and cd to dir: `git checkout git@github.com:davidbonachera/juke.git && cd juke`
- Install node dependencies: `npm install`
- Run with `node juke.js`
- If using an IP in your Shadowsocks client configuration, update it to reflect the new server's IP

## Current Limitations:
- Currently only reconfigures the Shadowsocks service for use
- The https:// and tor:// gateways are also unavailble upon redeployment, which contains the client configuration details, mirrors, etc.

## TODO:
- Testing suite
- Refactor to use async/await
- Handle network failures gracefully
- Add automatic reconfiguration for other services besides Shadowsocks
- ~~make domain optional~~
- add generic error handler for fatal and non fatal reporting

