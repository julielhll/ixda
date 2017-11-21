# Nom du projet

When a conference is finished, as people leave the room, they come across a device asking how they feel about what they have seen. Then they can vote for different feelings.

## Harware

* Arduino Uno
* 1 Breadboard
* 5 Round force-sensitive resistors
* 5 resistors
* multiples cables

## Software

* Your computer
* P5.js librairies
* Node

## How to build the poll

You will need 5 transparent tubes that are placed on a base made out of cardboard (see picture below).

# How to connect p5.js and arduino ?

You should first go in the config.json file and check if the right serial port is set up.
```javascript
{
	"serverPort" : 8000,
	"serialPort" : "/dev/cu.usbmodem1411",
	"serialRate" : 9600
}
```

