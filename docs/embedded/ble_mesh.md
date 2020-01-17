# mesh
* 8 level picture
* node picture

## feature
* many to many
* device(not in mesh) to node(in mesh) provisioning(use NetKey)

## Concepts
### device  
not in mesh
### node
in mesh
### provisioning
### elements 
* multiple, constituent parts of nodes, can be independently controlled
### messages
* ack or no ack
* 3 types GET, SET and STATUS
### address  
* unicast group virtual
### Publish/Subscribe
#### States and Properties
* states(Generic OnOff, values on/off)  
* * State Transitions  
* * Bound States 

* properties(Temperature 8,  Indoor Temperature or Outdoor Temperature)
* * two categories(read-only read-write)

### models
[model](ble_mesh_model.md)

* server(has states)
* client(no states)
* control(client and server)
* immutable

### Generics
* generic states  example,Generic OnOff and Generic Level.
* generic messages  Examples  Generic OnOff Get and Generic Level Set
* generic model example ,Generic OnOff Server,Generic Level Client

### Scenes
A scene is a stored collection of states which may be
recalled and made current by the receipt of a special
type of message or at a specified time.

## step
### provisioning 5 steps (device -> node)  
#### 1.Beaconing
* indicates its `availability` to be provisioned by using the <<Mesh Beacon>> AD type in advertising packets  
* pressing a combination of buttons, to beaconing

#### 2.Invitation
* provisioner -> dev (Provisioning Invite PDU)  
* dev -> provisioner(Provisioning `Capabilities` PDU)

#### 3.Exchanging Public Keys

#### 4.Authentication
* the device to be provisioned outputs a random(For example, it might
flash an LED several times)  
* user input radom numver to provisioner

#### 5.Distribution of the Provisioning Data
* a session key is derived by each of the two devices from
their private keys and the exchanged, peer public keys.  
* distribution of the data(include NetKey)

after provision, device gets NetKey, IV Index, Unicast Address, now
now device->node

## Features

### relay
* are able to retransmit received messages(TTL)
### proxy
* device has no mesh stack, can link to mesh by GATT(normal BLE)

### friend

### low power

## key
* netkey - whole net
* appkey - subnet
* devkey - onedev

## level
### 1.BLE(full Bluetooth LE stack)
### 2.Bearer Layer
* Advertising Bearer
* GATT Bearer(need a Proxy node)

### 3.Network Layer
* defines the various message address types and a network message
* The Relay and Proxy features may be implemented by the network layer
### 4.Lower Transport Layer
* segmentation(up to lower) and reassembly(lower to up) of PDUs
### 5.Upper Transport Layer
* encryption, decryption and authentication of application data passing to and from the access layer
* transport control messages
### 6.Access Layer
* Defining the format of application data
* Defining and controlling the encryption and decryption process which is performed in the upper transport layer
* Verifying that data received from the upper transport layer is for the right network and application, before forwarding the data up the stack
### 7.Foundation Models Layer
* implementation of those models concerned with the configuration and management of a mesh network
### 8.Models Layer
* the implementation of Models and as such, the implementation of behaviors, messages, states, state bindings and so on, as defined in one or more model specifications

## security
### 7 Fundamentals
* All mesh messages are encrypted and authenticated.
* Network security, application security and device security are addressed independently.
* Security keys can be changed during the life of the mesh network via a Key Refresh procedure
* Message obfuscation makes it difficult to track messages sent within the network providing a
privacy mechanism to make it difficult to
track nodes
* Mesh security protects the network against
replay attacks
* The process by which devices are added to the
mesh network to become nodes, is itself a
secure process
* Nodes can be removed from the network securely,
in a way which prevents trashcan attacks

### 3keys
* The device key facilitates confidentiality and authentication of key material between a Configuration Client
and a single node. (a device key is only known by a Configuration Client
and the single node)
* The application key facilitates confidentiality and authentication of application data
sent between intended nodes. 
* The network key facilitates privacy, confidentiality, and authenticity of
network messages.

## Obfuscation
The network security model utilizes a privacy mechanism called obfuscation that utilizes AES to encrypt
the source address, sequence numbers, and other header information using a privacy key. 

### core
#### netkey(Network Layer)
* A network encryption key and a Privacy Key are derived directly from the NetKey
* being in possession of the NetKey allows a node to
decrypt and authenticate up to the Network Layer
#### AppKey(upper transport layer)
* Application data for a specific application can only be
decrypted by nodes which possess the right application
key (AppKey)
* AppKeys are associated with only one NetKey
#### DevKey
* The DevKey is used in the provisioning process to secure
communication between the Provisioner and the node

#### remove
##### Key Refresh
* The Provisioner application is used to add the
node to a black list and then a process called the Key
Refresh Procedure is initiated
* the entire set of security keys which form the
basis for network and application security are replaced
#### privacy
A privacy key, derived from the NetKey is used to
obfuscate network PDU header values, such as the
source address
#### Replay Attacks
* seq， IV index

## action
* broadcast
* Multipath Delivery
### managed flooding
* Heartbeats
* TTL
* Message Cache
* Friendship
### Traversing the Stack
* Network ID field
* message integrity check (MIC) field
* an application identifier (AID) field 
* the transport message integrity check (TransMIC) 

## net work
* network addresses
* network keys
* application keys
* IV Index
* primary subnet(IV Update procedure)


Provisioner
Configuration Client

## elements
* The number and structure of
elements is static and does not change throughout the lifetime of a node 
* The primary element is addressed using the first unicast address assigned to the node during
provisioning. Each additional secondary element is addressed using the subsequent addresses

## address
* A unicast address is allocated to an element and always represents a single element of a node

## model
* Model specifications are immutable
* a single instance of any given state is
on an element
## friend
A Friend node may be friends with multiple Low Power nodes. A Low Power node can only be friends
with a single Friend node.