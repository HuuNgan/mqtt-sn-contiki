# mqtt-sn-contiki
An example of mqtt-sn in contiki

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/HuuNgan)

## Simulation in Cooja
#### 1. Open Cooja and creat motes
- Mote 1: Border Router: rpl-border-router (/contiki/examples/ipv6/rpl-border-router/border-router.c)
- Mote 2: Subscriber: subscriber.c
- Mote 3: Publisher: publisher.c

#### 2. Open socket for mote 1
  - Right click on mote 1 -> more tools for sky1 -> Serial socket (server).
  - Click start.

#### 3. Open terminal and type this
```sh
cd contiki/examples/ipv6/rpl-border-router/
make connect-router-cooja
```
#### 4. Open new terminal and type
```sh
cd ~/contiki/mqtt-sn-contiki/tools/mosquitto.rsmb/rsmb/src
sudo ./broker_mqtts config.mqtt
```

In case of existing this error: Socket error 98 (Address already in use)
Try:
```sh
sudo service mosquitto stop
```
before you run:
```sh
sudo ./broker_mqtts config.mqtt
```

## More About Mosquitto publish and subscribe
#### Subscribe:
```sh
    mosquitto_sub -v -h broker_ip -p 1883 -t '#'
```
Or
```sh
    mosquitto_sub -v -t 'test/topic'
```
Where broker_ip is: 127.0.1.1

#### Publish a topic:
```sh
    mosquitto_pub -t 'test/topic' -m 'helloWorld'
```
