# mesh model
* defines a set of States, State Transitions, State Bindings, Messages, and
other associated behaviors
* An Element within a Node must support one
or more models, and it is the model or models that defjne the functionality
that an Element has

## state
* states must act independently
For example, if the generic on/ofg state indicates that
a device is currently ofg, increasing the generic level state should have no user-discernible efgect

## model
* A model may extend another model
* Models that do not extend other models are known as root models
* node element model state(or Properties)
## coding models
### 1.RX Message Handler Functions
### 2.TX Message Producer Functions
### 3.Bind Application Keys to Models

## Foundation Models
1. The Confjguration Server and Client Models
2. The Health Server and Client Models

* The confjguration server model contains a signifjcant number of states that allow various aspects of a
device to be confjgured
* The device’s overall composition is held within a state called the Composition
Data state
* `The destination address` to use when publishing messages and `other parameters` relating
to periodic message publication; `the addresses subscribed to`; and which, if any, of the special relay,
friend, low power node, and proxy `roles a device may play` are all part of the confjguration
model’s data.