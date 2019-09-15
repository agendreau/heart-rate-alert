# Heart Rate Alert

## Introduction 
Now you will create a system to monitor your heart rate. You can use ``||music: speaker||`` to make a sound when your heart rate is high. You can use the ``||neopixel: five LEDs||`` on the gator:bit or the ``||basic: LEDS||`` on the micro:bit. You will use the ``||logic: if then else||`` blocks to ask questions about the value of your ``||gatorParticle: heart rate||`` to decide what you want to do. Lastly don't forget to think about ``||basic: how often||`` you want to take measurements, how you will ``||input: control||`` when the measurements are taken, and ``||loops: how many||`` measurements you want to take. There is a potential solution in the Hint. When you think you've got it, ``|Download|`` the code and try it out.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let i = 0; i < 10; i++) {
        bpm = gatorParticle.heartbeat(HeartbeatType.BPM)
        basic.showNumber(bpm)
        if (bpm < 70) {
            music.playTone(262, music.beat(BeatFraction.Whole))
            music.rest(music.beat(BeatFraction.Whole))
            basic.showString("Sleep")
        } else if (bpm < 90) {
            basic.showLeds(`
                # # . # #
                # # . # #
                . . . . .
                . # # # .
                . # # # .
                `)
        } else if (bpm < 110) {
            basic.showIcon(IconNames.StickFigure)
        } else if (bpm < 130) {
            basic.showString("Walk")
        } else {
            basic.showIcon(IconNames.Rabbit)
            music.beginMelody(music.builtInMelody(Melodies.Chase), MelodyOptions.Once)
        }
        basic.pause(2000)
    }
})
let bpm = 0
gatorParticle.begin()
let strip = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)

```

```package
gatorParticle=github:sparkfun/pxt-gator-particle
neopixel=github:microsoft/pxt-neopixel
```









