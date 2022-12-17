---
created: 2022-11-26T08:17:07 (UTC +00:00)
tags: []
source: https://www.fluke.com/en-gb/learn/blog/digital-multimeters/how-to-test-for-continuity
author: 
---

# How to Test for Continuity with a Digital Multimeter | Fluke

> ## Excerpt
> Learn how to test continuity using a digital multimeter.

---
 [Digital multimeters](https://www.fluke.com/en-gb/learn/blog/digital-multimeters), [Fundamentals](https://www.fluke.com/en-gb/learn/blog/fundamentals)



(assets/images/volt1.jpg)

(assets/images/volt2.jpg)

1.  Turn the dial to Continuity Test mode. It will likely share a spot on the dial with one or more functions, usually resistance (Ω). With the test probes separated, the multimeter’s display may show OL and Ω.
2.  If required, press the continuity button.

![Steps for measuring continuity with a digital multimeter] "Steps for measuring continuity with a digital multimeter")

1.  First insert the black test lead into the COM jack.
2.  Then insert the red lead into the VΩ jack. When finished, remove the leads in reverse order: red first, then black.
3.  With the circuit de-energized, connect the test leads across the component being tested. The position of the test leads is arbitrary. Note that the component may need to be isolated from other components in the circuit.
4.  The digital multimeter (DMM) beeps if a complete path (continuity) is detected. If the circuit is open (the switch is in the OFF position), the DMM will not beep.
5.  When finished, turn the multimeter OFF to preserve battery life.

## Continuity testing overview

-   Continuity is the presence of a complete path for current flow. A circuit is complete when its switch is closed.
-   A digital multimeter’s Continuity Test mode can be used to test switches, fuses, electrical connections, conductors and other components. A good fuse, for example, should have continuity.
-   A DMM emits an audible response (a beep) when it detects a complete path.
-   The beep, an audible indicator, permits technicians to focus on testing procedures without looking at the multimeter display.
-   When testing for continuity, a multimeter beeps based on the resistance of the component being tested. That resistance is determined by the range setting of the multimeter. Examples:
    -   If the range is set to 400.0 Ω, a multimeter typically beeps if the component has a resistance of 40 Ω or less.
    -   If the range is set 4.000 kΩ, a multimeter typically beeps if the component has a resistance of 200 Ω or less.
-   The lowest range setting should be used when testing circuit components that should have low-resistance value such as electrical connections or switch contacts.

- when soldering on PCBS it shouldn't beep when testing connection between soldered contact points and the track path and the rest of the board. If it does it means connections have merged and the circuit will not work. To correct this you need to reheat the contact point with a soldering iron and use a suction tool to remove the solder. Once done, start again. Or use a box cutter to correct the connections
