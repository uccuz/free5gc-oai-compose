# free5GC OAI Compose

This repository contains the docker-compose file to deploy the free5GC core network with the OAI RAN.

- free5GC Version: v3.3.0
- OAI Version: 2024.W21

## Prerequisites

- GTP5G kernel module: needed to run the UPF
- Docker: needed to run the Free5GC containers


## End-to-end Setup

### Setup free5GC

Start the free5GC core network
```shell=
cd free5gc
docker compose up -d
```


### Setup Subscriber

Create a subscriber through the WebUI
```
<YOUR_SERVER_IP>:5000
```

### Setup OAI RAN

Start the OAI RAN
```shell=
cd oai
docker compose up -d
```

Verify that it is connected: you should see the following output at UE:
```shell=
4612.331310 [NAS] I [UE 0] Received NAS_CONN_ESTABLI_CNF: errCode 1, length 71
4612.331294 [NR_RRC] I Measurement Configuration is present
4612.331336 [NR_RRC] I rrcReconfigurationComplete Encoded 10 bits (2 bytes)
4612.331341 [NR_RRC] I  Logical Channel UL-DCCH (SRB1), Generating RRCReconfigurationComplete (bytes 2)
4612.332577 [OIP] I Interface oaitun_ue1 successfully configured, ip address 10.60.0.1, mask 255.255.255.0 broadcast address 10.60.0.255
```