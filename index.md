# Music Game/Frequency Reader
This project is a game/device that can do a multitude of things. Firstly, it can read the frequency of a note. Not only that, but it can also take said frequency and match it to a note. Secondly, it can determine whether a note played by someone is correct, comparing it with another note. This is displayed on a small LCD screen that will show both the note and whether it was correct. I chose this project because it seemed suitably challenging for my level and also combined my 2 interests of computer science and music. 

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Gregory R | Hong Kong International School | Computer Science | Incoming Freshman

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![](tempfile.heic.png)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project








# The Sources I Used
this project wouldn't be possible without the help of talented individuals both in this class and on the internet. Here are the majority of the sources I used

-[this instructables article](https://www.instructables.com/Arduino-Audio-Input/)
note: I also used [this](https://www.instructables.com/Arduino-Audio-Input/) article, linked on the page

-[the Arduino Documentation](https://docs.arduino.cc/)

-[this was my starter project, and it provided a suitable base for me to work on my project and specialize it for this purpose](https://clydelettsome.com/blog/2019/12/18/my-weekend-project-audio-frequency-detector-using-an-arduino/)



# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resources to create professional schematic diagrams, though BSE recommends Tinkercad because it can be done easily and for free in the browser. 

# Code


```c++
int incomingAudio;

void setup(){
  Serial.begin(9600);
  cli();//disable interrupts
  
  //set up continuous sampling of analog pin 0
  
  //clear ADCSRA and ADCSRB registers
  ADCSRA = 0;
  ADCSRB = 0;
  
  ADMUX |= (1 << REFS0); //set reference voltage
  ADMUX |= (1 << ADLAR); //left align the ADC value- so we can read highest 8 bits from ADCH register only
  
  ADCSRA |= (1 << ADPS2) | (1 << ADPS0); //set ADC clock with 32 prescaler- 16mHz/32=500kHz
  ADCSRA |= (1 << ADATE); //enabble auto trigger
  ADCSRA |= (1 << ADIE); //enable interrupts when measurement complete
  ADCSRA |= (1 << ADEN); //enable ADC
  ADCSRA |= (1 << ADSC); //start ADC measurements
  
  sei();//enable interrupts

  //if you want to add other things to setup(), do it here

}

ISR(ADC_vect) {//when new ADC value ready
  incomingAudio = ADCH;//update the variable incomingAudio with new value from A0 (between 0 and 255)
}

void loop(){
  Serial.println(incomingAudio);
}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 



| Devmo KY-037 Sound Sensor | Taking in the sample frequency signal and sending it to the board via an analog signal| $Price | <a href=https://www.amazon.com/DEVMO-Microphone-Sensitivity-Detection-Compatible/dp/B07S4DTKYH > Link </a> |

| Arduino UNO | Interpreting the analog signal and running the frequency-detection code| $Price | <a href=https://store-usa.arduino.cc/products/arduino-uno-rev3> Link </a> |

| 16x2 LCD display with I²C interface | Displaying notes and frequencies | $Price | <a href=https://store-usa.arduino.cc/collections/displays/products/16x2-lcd-display-with-i-c-interface> Link </a> |

| Jumper Wires | Connecting all the components together |

| Breadboard | Having a space to connect all the wires |
```
# Other Resources/Examples
One of the best parts about GitHub is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
```
<iframe width="560" height="315" src="https://www.youtube.com/embed/6ioimKLn2jI?si=vSGMq1GlVQYV36qd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

This video is showcasing my starter project. It is comprised of 3 sliders, with each of them controlling how much of a certain color there is. One controls red, one blue, and one green. Each one is connected to an LED of that corresponding color, and depending on how high you push the slider, the light will output at that strength. This can be used to create some color combinations. Sliding up both the red and blue creates magenta, the blue and green create cyan, and the green and red create yellow. Sliding all the sliders creates white. I chose this project because it seemed fun and didn't seem too easy or too challenging. I faced 2 main challenges while doing this project. First, I was using too much solder on each of the joints. However, by using some tips and advice from my instructors, I was able to start using an accurate amount of solder. The second challenge was when I tested it the first time, the light wouldn't work. After talking with my instructors, I learned it was because some of the joints weren't soldered, and they all needed to be soldered. These challenges helped me improve my soldering skills as I overcame them.
