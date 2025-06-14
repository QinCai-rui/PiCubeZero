---
title: "RasPiCube"
author: "@QinCai-rui"
description: "A Raspberry Pi powered Rubik's cube timer and scramble generator"
created_at: "2025-05-16"
---

**TOTAL TIME:** about 11 hours

## 16/5/25

### Update 1/1

In around **30 minutes** I managed to create a Prove-of-Concept (PoC) version of a 3x3 Rubik's Cube scramble generator. The code is pretty simple and straightforward, so I'm not gonna waste time describing how it works.

![basic scramble generator in action](https://github.com/user-attachments/assets/4139d443-92f2-437f-946a-af215583b283)

---------------------

### Update 2/2

Another **1 hour and a bit**, a _proper_ timer and scramble generator was born. I integrated the old scrable generator into the new program, by importing it as a module.

I kind of struggled at first to make the timing work, because the code on line 31 somehow "redefined" the `time` module, which gave me wheird errors:

```python
Traceback (most recent call last):
  File "/home/qincai/PicoCube/test.py", line 76, in <module>
    main()
    ~~~~^^
  File "/home/qincai/PicoCube/test.py", line 51, in main
    start_time = time.time()
                 ^^^^
UnboundLocalError: cannot access local variable 'time' where it is not associated with a value
```
so i changed `time` to `solve_time` :))

Another challenge was to display the real-time timer, which every rubiks cube timer should have. In the older real-time version of this program, the user had to press `CTRL+C` to trigger the timer stop, which is not ideal. Fortunately I worked _that_ out as well, using `threading`

---------------------------

## 19/5/25

### Update 1/3

After about **1.5 hours** of hard grind, behold -- the `PiCubeZero`. Okay, im not even sure if it works or not, since I don't have the necessary hardware to build the project physically. That also means there is no pictures to share :((.

The process was pretty straightforward, since there is sooo much documentation on the Internet about the modules I was/am after. I fed the completed program into `GPT-4.1` to check for any mistakes and suggestions, and good -- no big mistakes, but a few changes were made, such as the font selection thing I do _not_ know how it works, or if it's supposed to work... 

----------

### Update 2/4

Another **50 -ish minutes** later and I (sort of, and the stupid `GPT-4.1` helped me **a lot**) made a version of PiCube, called "PiCubePico", since it is based on the Raspberry Pi Pico MCU. Check it out here on Wokwi Simulator: <https://wokwi.com/projects/431347174552980481>

Screenshot: ![image](https://github.com/user-attachments/assets/c9dac93d-f04c-47e7-b45a-9a12dfbac601)

_(pls ignore the inconsistency between the OLED screen and the 7-seg display. The simulator is **extremely** laggy, with one second simulated being 15+ secs in real life)_

---------

### Update 3/5

Spent like **1.5 hours** creating the BOM, and it is not even complete (yet). 
Here is the [BOM for RasPiCube - PiCubeZero](https://github.com/QinCai-rui/RasPiCube/blob/main/BOM/BOM.md)

----------

## 20/5/25

### Update 1/6

Just updated the RasPiCube - PiCubeZero program to use a Waveshare 2-inch IPS LCD Display (ST7789, 240x320), instead of a tiny SSD1306 128x64 OLED display. This time GPT-4.1 helped me a lot when updating the program since I made quite a lot of mistakes. 

Time spent this session: ~**1.5 hours**

-------------

### Update 2/7

For this session, I worked a lot on the [PiCubeZero's BOM](https://github.com/QinCai-rui/RasPiCube/blob/main/BOM/BOM.md). I tried comparing the items I need on Aliexpress and Amazon. I almost got scammed by (likely) a scam on Aliexpress. [Link](https://www.aliexpress.com/item/1005008269997334.html)

The "Sandian" branded uSD cards look sooo similar to the real "SanDisk" ones.

<img width="311" alt="Screenshot 2025-05-20 at 6 42 54 PM" src="https://github.com/user-attachments/assets/4dbae5fb-b5d5-4295-ab59-7e451d6c4774" />
<img width="539" alt="Screenshot 2025-05-20 at 6 43 13 PM" src="https://github.com/user-attachments/assets/e4387966-cdeb-495c-a4e3-ea30907f4333" />

A quick Internet search revealed that...... "SanDian" is a scam. WHOO HOO. /j

Here are the posts:
[post1](https://forums.grc.com/threads/fake-1tb-sandian-micro-sdcard-test.1333/) 
[post2](https://bulkmemorycards.com/identifying-counterfeit-microsd-cards/)

Maybe just don't buy uSD cards from AliExpress... Buy them on Amazon instead ig.

Time spent this session: ~**1 hour**

--------------

### Update 3/8 

Since I couldn't find one single NeoPixel (as in 1 LED), I decided to switch to a common-cathode RGB LED. Simple! Also saved a bit of cash....

Time spent this session: **25 minutes**

------------

## 21/5/25

### Update 1/9

Updated the BOM to include all needed parts. This project is gonna cost a lot with a Pi 0 2WH, a battery, and a screen... (about $100 USD atm).

<img width="427" alt="Amazon Total" src="https://github.com/user-attachments/assets/e4fbed02-b408-4d9c-90c0-ef2a5e449325" />
<img width="374" alt="AliExpress Total" src="https://github.com/user-attachments/assets/a159bbc3-0997-4fc1-b7d1-b70e516869e0" />

Time spent this session: **30 minutes**

-----------------

## 2/6/25

### Update 1/10

Update the BOM once again to only include the parts that i need. This brings the cost down to ~$60. See [BOM-needed.md](BOM/BOM-needed.md).

![image](https://github.com/user-attachments/assets/0e33619f-2dc4-43c3-b796-6be7972aefd4)
Time spent this session: **20 minutes**

--------------------

### Update 2/11

Cleanned up the repo!! There is nothing more i could say..

Time spent this session: **25 minutes**

-------------------

## 7/6/25

### Update 1/12

Spent **1.5 hours** looking for a better USB WiFi adapter. Ended up finding this one on AliExpress:  
[FENVI 1800Mbps WiFi 6 USB Adapter Dual Band 2.4G/5Ghz Wireless WiFi Receiver USB 3.0 Dongle Network Card](https://www.aliexpress.com/item/1005005935638503.html)

Turns out, this adapter is actually listed in [morrownr's Linux USB WiFi compatibility list](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md), so it should work just fine out of the box. It’s the Fenvi FU-AX1800 (uses the mt7921au chipset), which is pretty much plug-and-play on any recent Linux, as long as you’re not running some ancient kernel from the Stone Age (ahem, looking at Raspberry Pi OS, which just migrated to 6.12).

Some random thoughts:
- mt7921au = good chipset, Linux likes it, no weird drivers, just works (or so i hope).
- Loads of positive reviews from other Linux nerds online, especially on AliExpress and in that repo.
- It’s super cheap ($1.72 with Welcome Deal). Not gonna break HC's bank.
- Just double check you don’t get tricked into buying the Realtek version — only mt7921au is the good one. -- from the repo

Added this to my BOM cos I need WiFi. Anyway, very happy with this find!

(surprisingly, this much better wifi adapter only brought up my BOM by about $5. It's prob Aliexpress' Welcome Deal thingy)

_see (BOM)[https://github.com/QinCai-rui/RasPiCube/blob/432650de670bce71bf1978ce57de217eb192d6ab/BOM/BOM-needed.md] for my BOM at the time of writing_

Time spent: **1 hour** (browsing, comparing, reading reviews, dodging dodgy sellers on Ali)



