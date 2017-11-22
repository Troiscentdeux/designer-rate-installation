# designer-rate-installation
This project was created in order to be included in the space of a big conference of design. 
This installation is composed of an arduino ultrasonic sensor detecting the arrival of a person in front of the installation. Then, a computer with a webcam detects the person's face and its emotions. These values are used to define the rate of design inside the user of the experience. The results are given using the computer's voice. 

### Prerequisites

Material you will need :
- a computer with a webcam
- an arduino uno board
- 4 arduino cables
- an ultrasonic arduino sensor

### Installing

In order to make this project run you will need to install on your computer : 
- node.js (https://nodejs.org/en/)
- the arduino software (https://www.arduino.cc/en/Guide/Windows)
- socket (https://socket.io/)
- johnny-five (http://johnny-five.io/)

### Steps

The project is based on the clmtrackr javascript library.
https://github.com/auduno/clmtrackr

You can directly use the modified files presented here.

The datas of the face tracking are stored in ```(er).``` 
You can give it an other value in this part : 

```
function faceFound(data) {
	console.log(data);

	if (data[7].value > 0.5){
		text = 'Hello mister';
	} else {
		text = 'Hello lady';
	}
	console.log(text);
	speak(text);
}

```

Then, I added the javascript code of a Web Speech Synthesis Demo : https://codepen.io/matt-west/pen/wGzuJ
Once again, I added that in the same html file (which is a bit messy). 

You can make the computer read a sentence by calling the speak function.

```
text ='Type here anything you want'
speak(text);

```


You can also modify some settings :

```
msg.volume = 1;
msg.rate = 1;
msg.pitch = 1;

```





Now you need to set your arduino equipment like so :

![Image arduino installation](https://www.carnetdumaker.net/uploads/img_attachments/large/sonar_arduino_bb.jpg)

In order to connect your arduino board and sensor to your webpage, you need to run a server. 
First, open the arduino interface and launch the pingFirmata.ino arduino file and upload it on your board.
Then the index.js will play its role, which is to set the server and link everything. 

To run the server, you will need to open the command prompt.
There is an example of path, but type it according to where you pasted the clmtrackr-dev file in your computer.

```
cd Document/DSAA/TECHNO/clmtrackr-dev
node index.js
```

Then, type localhost:3000 on your web browser.
Everything works now ! 

### Explanations on more specific points

The setTimeout function :

```
document.addEventListener('DOMContentLoaded', function() {
setTimeout(function(){
	 text = 'Oh, you are here ?! Welcome.';
	 console.log(text);
	 speak(text);
},1000);
}, false);
```
In this part I needed to have a setTimeout function because I wanted to make the computer speak as soon as the page was loaded. Since there is a lot of thing to load on the page, it wasn't working. Putting a setTimeout function allowed to make sure everything had the time to load before the computer starts speaking. 

The name generator :

```
function generator2(){
	 var firstnamelist = ["UX", "Fashion", "Global", "Senior"];
	 var lastnamelist = ["Student", "Professionnal", "Co-designer"];

	 var random1 = parseInt(Math.random() * firstnamelist.length);
	var random2 = parseInt(Math.random() * lastnamelist.length);

	var name = firstnamelist[random1] + " " + lastnamelist[random2];
}
```

## License

This project is licensed under the MIT License.

