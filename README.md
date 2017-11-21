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

You will need many files, especially a .json, index.html, index.js, main.js (in which the p5 sketch is stored) files.

The serial port is set up in the config.json.

```javascript
{
	"serverPort" : 8000,
	"serialPort" : "/dev/cu.usbmodem1411",
	"serialRate" : 9600
}
```

Then move to the index.js file. You will find everything you need here to set up the serial port. These lines below are useful to initialize the serial port from config.json.

```javascript
var serialPort = new SerialPort( config.serialPort, {
    baudrate: config.serialRate,
    parser: SerialPort.parsers.readline( '\n' )
} );
```



```javascript
serialPort.on( 'open', function () {
    console.log( config.serialPort + ' open' );

    serialPort.on( 'data', function( data ) {
        console.log( 'data received: ' + data );
        io.emit( 'arduinoData', data );
    } );
} );
```

The values you get from your Arduino Board are stored into the variable press, as written below. However, the values are stings so you need to use JSON.parse() in main.js file, which analyses the values and return a number.

```javascript
press = JSON.parse(data).press;
```

Final step : you must go to the terminal to switch on the server. The line cd (then drag and drop your folder) allows you to change directories, which means that you move to other files. Finally type node index.js. 

```
cd /Users/julie/Documents/p5/ixda
node index.js
```

Don't forget to load p5 librairies in the index.html file, and you can now open localhost:8000 in your favorite navigator.



