# EMG and TENS

Simple [EMG](https://en.wikipedia.org/wiki/Electromyography) and [TENS](https://en.wikipedia.org/wiki/Transcutaneous_electrical_nerve_stimulation) circuits for your arm to "control" someone else's arm.

## About

Inspired on [Backyard Brains](https://backyardbrains.com), i designed circuits to use your muscle signal (with EMG) to excite and contract another human's muscle (with TENS). For more infos, read the post "[Experiment: Advanced NeuroProsthetics: Take Someone's Free Will](https://backyardbrains.com/experiments/humanhumaninterface)" and/or watch Greg Gage's video "[How to control someone else's arm with your brain](https://www.youtube.com/watch?v=rSQNi5sAwuc)" on TED.

[![Assista ao vídeo](http://i3.ytimg.com/vi/rSQNi5sAwuc/maxresdefault.jpg)](https://www.youtube.com/watch?v=rSQNi5sAwuc)

## Components 

#### EMG

- 1x INA106;
- 1x TL074;
- 2x 1N4148;
- 1x Potentiometer 200K ohm;
- Capacitors: 1uF (3x) and 0.01uF (1x);
- Resistors: 1M ohm (2x), 10K ohm (2x), 1K ohm (2x), 150K ohm (4x) and 80.2K ohm (1x).

#### TENS

- 2x 555;
- 1x 2N3053;
- 1x TIP122;
- 1x 7805;
- 1x Transformer 12V 100mA (~8:1);
- 2x 1N4004;
- Potentiometers: 10K ohm (2x) and 5K ohm (1x);
- Capacitors: 10uF (1x) and 100uF (1x);
- Resistors: 33K ohm (2x), 1K ohm (2x), 330 ohm (1x) and 220 ohm (4x);
- 3x LEDs.

#### Arduino (optional)

To getting better results, you can use an Arduino connected between EMG and TENS. 

```C++
#define EMG A0
#define TENS D2

void setup() {
  pinMode(EMG, INPUT);
  pinMode(TENS, OUTPUT);
}

void loop() {
  digitalWrite(TENS, (analogRead(EMG) > 512));
}
```

## Experimental Procedure

1. Place three surface EMG electrodes close to each other on the forearm.
2. Using the alligator clips, connect the middle electrode to EMG ground and the two others electrodes to EMG inputs.
3. Place two surface EMG electrodes close to each other across the ulnar nerve.
4. Using the alligator clips, connect the electrodes to TENS outputs.
5. Begin with the TENS device turned into the lowest setting.
6. Slowly begin to turn up the power of the TENS device until you see a response.

**Important:** if pulls their electrodes off before the TENS device is turned off it will cause the circuit to short and constantly send stimulation to the controlled. Avoid this! To disarm the experiment, first turn off the TENS device totally.

**Note**: a TENS unit by definition delivers enough current to cause muscle contraction. Do not place electrodes across the muscles of the throat or the chest.

## Acknowledgments

- [Backyard Brains](https://backyardbrains.com)
- [Meduag](https://www.youtube.com/user/meduag/)
- [Ex Machina Unifei](https://www.facebook.com/ExMachina.UNIFEI)
