# Speech-and-text-converter
Task 1- IOT and data systems

This repository contains two subtastks:

1-speech & text converter

2-Wisdom ESP32 oparting algoritm.
## 1. speech & text converter
### index.html:
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Speech & text converter</title>
        <meta charset="UTF-8">
        <meta http-equiv='Content-Type' content='text/html; charset=utf-8'>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <!-- div taht contains aal voice to text elements-->
        <div class="Voice2textDiv">
            <h1 id="mainText-V2T"> Voice to Text </h1>
            <textarea id="resultBox" rows="5"></textarea>
            <br>
            <p id="instructions-V2T">Click on start button </p>
            <button id="start-V2T-btn" onclick="runSpeechRecognition()">Start</button>
        </div>

        <!-- div taht contains aal text to voice elements-->
        <div class="Text2voiceDiv">
            <h1 id="mainText-T2V"> Text to Voice </h1>
            <textarea id="inputBox" rows="5"></textarea>
            <br>
            <p id="instructions-T2V">Click on start button </p>
            <button id="start-T2V-btn" onclick="runSpeek()">Start</button>
        </div>
        <script>
            <!-- will run when the start butttun clicked -->
                function runSpeechRecognition(){
                    <!-- get access to the elements by JavaScript-->
                    var resultBox=document.getElementById("resultBox");
                    var instructions=document.getElementById("instructions-V2T");

                    <!--create a webkitSpeechRecognition object.-->
                    var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition;
                    var recognition = new SpeechRecognition();

                    <!--functions for the events(onstart, onspeechend, onresult)-->
                    recognition.onstart = function() {
                        instructions.innerHTML = "Voice recognition is on, please speak..";
                    };

                    recognition.onspeechend = function() {
                        instructions.innerHTML = "Click on start button";
                        recognition.stop();
                    }

                    recognition.onresult = function(event) {
                        var text = event.results[0][0].transcript;
                        resultBox.innerHTML = text ;
                    };
                    <!--starting the recognition work-->
                    recognition.start();

                }

                <!-- will run when the start butttun clicked -->
                function runSpeek(){
                    <!-- get access to the elements by JavaScript-->
                    var instructions= document.getElementById("instructions-T2V");
                    var inputBox= document.getElementById('inputBox').value;

                    <!--change the instructons under the textarea-->
                    instructions.innerHTML="Listen to the speek.."

                    <!--creating a SpeechSynthesisUtterance object-->
                    var synth = window.speechSynthesis;
                    var utter = new SpeechSynthesisUtterance();
                    utter.text=inputBox;

                    <!--speech the text entered by the user-->
                    window.speechSynthesis.speak(utter);
                    utter.addEventListener('end', event => {
                        instructions.innerHTML="Click on start button"
                     })
                }
        </script>
    </body>
</html>

## 2. Wisdom ESP32 operating algoritm:
1.	Open "Arduino IDE".
2.	Copy this URL: "https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json" and paste it in file>preferences>settings on "Additional Boards Manager URL's ".
3.	Press ok.
4.	Go to tools>Board "ESP32 Dev Module">Boards Manager.
5.	On the top of the window write "ESP32" and when it appears click on "Instal"l.
6.	After successful installation click on close and reopen the Arduino IDE.
7.	Write the code in Arduino IDE.
8.	Click on upload icon.
9.	Click on save
10.	When "connecting......" appears in the terminal click on "100" button existing on the ESP32.
11.	Still clicking on "100" button until "Leaving......" appears on the terminal.
12.	Click on "reset" button existing on the ESP32.
13.	The code is working.

