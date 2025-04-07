# ZK Email Safe 2FA demo
This repository can be used to locally start up and try out ZK Email's Safe 2FA demo. The demo demonstrates how ZK Email can be used to create a Safe with an email 2FA. The 2FA feature is implemented as a 2/2 Safe where one of the owners is an EOA and the other is an email signer. Whenever a transaction is initiated from the Safe by the EOA, an email is sent to the 2FA signer who will need to reply "Confirm" to approve it.

## Setup Instructions
### 0. clone the repo
```sh
git clone --recursive git@github.com:benceharomi/zkemail-2fa-demo.git && \
cd zkemail-2fa-demo
```
### 1. create a `.env`
Create a `.env` file based on the `.env.example`:
```sh
cp .env.example .env
```
### 2. fill `.env`
Safe Notification Services (SNS) variables:
* `SNS_PRIVATE_KEY`: your private key (you'll need some sepolia eth) for tx confirmations

Safe Wallet Monorepo (SWM) variables for the Safe UI:
* `SWM_NEXT_PUBLIC_INFURA_TOKEN`: Infura Token (https://www.infura.io)
* `SWM_NEXT_PUBLIC_WC_PROJECT_ID`: WalletConnect Project ID (https://cloud.reown.com)

### 3. start services
Use `docker compose` to build the images and start the containers:
```sh
docker compose up -d
```
### 4. try it out
> Note: it takes a few minutes for the docker images to build, containers to start up and safe wallet to generate its static files, please be patient.

As soon as everything is ready the wallet UI will be a available at http://localhost:8080

## Cleanup
```sh
docker compose down
```