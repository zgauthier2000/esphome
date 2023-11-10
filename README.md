# esphome
Snapshot of working yaml for esphome on an ESP32-S3-devkit-c to run a 64x24 LED Matrix display. Has a home screen with a clock and cool flames in the background, a mode to just loop a gif and play music, and can receive text messages via mqtt. Can be switced between using the panels as "lights" (WLED,even) and as a display, without the two components fighting each-other.

I pulled the voltage regulator off my devkit board and wired in an adjustable synchronous regulator so I could run the ESP at 3.5 volts, for better compatibility with the WS2812B's data needs. I also needed it to charge run the esp from a lifepo4 cell, which it does now, but that doesn't really matter for this project.

ESP32-S3 devkit:
https://www.amazon.com/dp/B0B6HT7V7P?psc=1&ref=ppx_yo2ov_dt_b_product_details

Using the 8megs of flash on this board with a custom partitions file. See the included .csv.
I have the two megs of PSRAM enabled - it would crash with more than 3ish panels running WLED visualizers otherwise.


LED Panels (I used six):
https://www.amazon.com/dp/B0B771455N?ref=ppx_yo2ov_dt_b_product_details&th=1

Soldered almost an entire 20 foot extension cord-worth of wires to get appropriate power to all parts of all panels.


DFPlayer Module:
https://www.amazon.com/dp/B08H4NF3FV?ref=ppx_yo2ov_dt_b_product_details&th=1

Plays mp3s from an SD-card. Works pretty well in ESPHome, but it seems like in some conditions I need to "wait" for the module, for some milliseconds, before giving it a command. The built-in amplifier is amazing. Its driving a 5.6 ohm speaker I took out of a bluetooth speaker.


LED Power Supply:
https://www.amazon.com/dp/B07KC3KSHP?ref=ppx_yo2ov_dt_b_product_details&th=1

You *can* run these panels from tons of 5v wallwarts at lower power levels. Gettting this appropriate supply really woke them up. I'm pretty sure as you reduce your maximum brightness in software, you lose steps/smoothness of color, so running at higher power levels will give you better color ontop of brightness.


Adjustable synchronous buck regulator (probably not necessary):
https://www.amazon.com/dp/B078C7ZS74?ref=ppx_yo2ov_dt_b_product_details&th=1

This never even gets warm running my ESPs. I haven't measured it yet, but I can tell I'm running the micros with significantly less power waste than I was with the built-in. The pots are VERY finicky.


Pictures!
![20231110_091744](https://github.com/zgauthier2000/esphome/assets/127626977/46ffc264-0dfb-4f96-9fce-e418fa937d14)

![Screenshot_20231110-084827_Photos](https://github.com/zgauthier2000/esphome/assets/127626977/d638165d-a944-4ce9-a2eb-87f619aaa9a7)

![20231107_094850](https://github.com/zgauthier2000/esphome/assets/127626977/9276ef64-915d-4b7a-ae94-1dcdd2a45ac3)
