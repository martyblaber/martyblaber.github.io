---
layout: post
title: "High Speed Arduino Stepper Driver"
categories: electronics, diy, arduino
author:
- Marty Blaber
meta: "Arduino Assembly"
---

# Part 0 - Parts
I bought a stepper that supports a closed loop servo + driver because I didn't want to have to drive the thing at full current all the time while ensuring that it doesn't budge. This one was reasonably priced, so I bought it:  [RTELLIGENT Nema 23 Stepper Closed Loop Servo Motor and Driver Kit 2 Phase 3.0NM(425 oz.in) with Encoder] (https://www.amazon.com/dp/B07ZLQL83N?psc=1&ref=ppx_yo2ov_dt_b_product_details).

## Documentation
I was pleasantly surprised at how good the documentation was for the driver: (http://www.rtelligent.net/upload/wenjian/T60_User_Manual.pdf), but I'll admit there's a bunch of stuff I don't understand - like the "pulse filtering mode" - which I think is an input buffer, but I'm not sure.

# Part 1 - Which way is up?
Long story short, this is the wiring that got the thing to work. The pulldown resistor is required to make the signal robust against noise. It did some strange stuff when I was missing the pulldown resistors on the buttons.

![Wiring.](/assets/images/2023-04-11 19_17_36-Wiring.png){: height="205px" width="auto" align="center" .imagebox}

Here it all is pinned and velcroed to a cork board (for extra safety and flamability).
![Board Overview.](/assets/images/2023-04-11 19_17_36-Board-Overview.png){: height="205px" width="auto" align="center" .imagebox}

I swear the white wire is ground:
![Power Plugs.](/assets/images/2023-04-11 19_14_54-Power_Zoom.png){: height="205px" width="auto" align="center" .imagebox}

# Part 2 - What is the minimum pulse length that my stepper driver can run.
I quickly discovered that all of the standard Arduino libraries for driving stepper motors were intolerably slow, and after some messing about, I realised that the builtin function `micros()` (that measures time in microseconds) is also too slow.

## Part 2b - ChatGPT teaches me how many instructions are in a loop.

```c


```

#### Quick aside on looking up command history in command prompt, powershell and bash or git bash.
- For Command Prompt, use `doskey /history`. Here is some of the trash that I recently typed into a command prompt.
    ```bat
    cd code
    ks
    ls
    dir
    cd martyblaber.github.io
    bundle
    N
    bundle install
    bundle exec jekyll serve
    ```

Links
[Backyard Scientist Induction Heater](https://www.youtube.com/watch?v=wKFnk4R54ZQ)
[Circuit for Induction Heater](https://oshwlab.com/kevindk9/pll-induction-heater)
[](http://uzzors2k.com/index.php?page=pllinductionheater1)

Litz wire is used to reduce the impact of the skin effect in high frequency transformers

Prob need an Oscilloscope for this.

https://wenneskrachgibtgehnwirindiewueste.wordpress.com/2017/05/16/arduino-powered-tig-acdc/

Arduino code for circuit
https://github.com/freq0ut/Due-Pulse-Welder


