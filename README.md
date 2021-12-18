# How Blockchain Messenger Works?
This is a case study of how blockchain messaging app works by studying the example of Adamant Messenger that uses blockchain transaction to act as it's persistance layer for the messages and WebSockets as a work around in order to aliviate the slow nature of transaction to simulate real-time messagery. Adamant provides you with the capability of creating your own node, so your messaging app is always available making the websockets protocol works in the most optimal condition: Having both interlocutors communicate on the same node. 
See rapport.pdf for more details or refer to:
- [How decentralized blockchain messenger works](https://medium.com/adamant-im/how-decentralized-blockchain-messenger-works-b9932834a639)
- [Encryption overview in ADAMANT Messenger](https://medium.com/adamant-im/encryption-overview-in-adamant-messenger-878ecec1ff78)

## ADAMANT ##
ADAMANT is a decentralized blockchain messaging platform. Applications use ADAMANT as an anonymous and encrypted relay and storage to enable messaging features. As examples, see Messenger app, Blockchain 2FA and Decentralized cryptocurrency exchanger implementations.
![ADAMANT nodes](https://github.com/Adamant-im/adamant/blob/master/docs/adm-nodes.jpeg)
For more information make sure to check ADAMANT website: <https://adamant.im> .
## API Documentation

Comprehensive [API specification](https://github.com/Adamant-im/adamant/wiki) is available.

The manual describes API endpoints to manage accounts, transactions, chats, and a key-value storage (KVS). Additionally, the manual suggests valuable information on creating new accounts and encrypting and decrypting messages.
## Set up
### Requirements
- 2 GB RAM
- 50 GB disk space or larger depending on the current node height.

### Installation
Using the docker-compose file in the root directory ( which uses a adamant-node v0.4 image on dockerHub) 

`docker-compose pull`

Using the docker-compose file in the adamantNodeLatest directory we can get the latest version of adamant (beware of dependency deprecation)

`cd adamantNodeLatest
 docker-compose pull
`

After pulling both postgres and adamant-node (or building it if we use the second option) we can run:

`docker-compose up`

You can stop or start the container via the command 

`docker-compose stop
 docker-compose start`
 
Then using your IP adress you can check if the node was correctly deployed on [Adamant Explorer](https://explorer.adamant.im/networkMonitor)
or by executing this comand on your docker container

`docker exec <CONTAINER_ID> curl -k -X GET http://localhost:36666/api/blocks/getHeight`

Then in order to use our node we need to deploy our own version of [Adamant Messenger Front-end](https://github.com/Adamant-im/adamant-im)
for that we need to follow the setup steps on local machine (see the git repo above) or we can build the DockerFile in the frontEnd directory

`
cd frontEnd
docker build -t adamant/frontend:latest .
docker run -p 8080:8080 adamant/frontend:latest
`

Here's a video illustration: 
