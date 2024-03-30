# LocalEthNetwork

# To Run
1. Build the Dockerfile:
```
docker build -t local_eth_network .
```
2. Create a local docker network:
```
docker network create my_eth_network
```
3. Enter the docker container and go to the app directory. Hardhat uses port 8545 by default.:
```
docker run -it --rm -p 8545:8545 --name local_eth_network --network my_eth_network local_eth_network
```

You can check that it's running by going to http://localhost:8545/ in your browser

If you need to access the local network in any other docker, make sure to include "--network my_eth_network" in the command. You can then check if it's accessible by running:
```
curl http://local_eth_network:8545
```
That should output:
```
{"jsonrpc":"2.0","id":null,"error":{"code":-32700,"message":"Parse error: Unexpected end of JSON input","data":{"message":"Parse error: Unexpected end of JSON input"}}}
```