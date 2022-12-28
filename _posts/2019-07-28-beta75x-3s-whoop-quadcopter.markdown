---
title:  "Beta75X 3S Tiny Whoop Quadcopter"
toc: true
tags:
  - rc
---

I have always been interested in Radio Controlled cars, planes, and later in this new trend with drones! Not these drones that follow you or use GPS to film or take pictures of the ground; what I enjoy is free flight, acrobatics even! But living near Paris, there really isn't a good option for these outdoor activities. Until... toothpick and tiny whoop mini drones are becoming a big thing!

I have finally ordered a [Beta75X 3S Tiny Whoop quadcopter drone from BetaFPV][betafpv75x]. I won't use if with FPV mask or goggles for now, until I know what I would like to do with it. I feel that's the perfect format for me to start with; it's usable by a begginer completely indoor, and then it's also easy to try it outdoor even in very small areas. And finally, with it beeing so small, it's also something easy to transport for a weekend or vacations, and enjoy anywhere.

{% include video id="ms1Se7y4E_Y?start=152" provider="youtube" %}

I am posting this to be able to share quickly with friends, and for me to find back all the technical details in no time.

## Beta75X 3S Tiny Whoop Quadcopter

- weight 45.3g
- 1103 8000Kv brushless motors
- F4 2-4S AIO 12A Flight Controller (FC)
- Customized EOSV2 Camera, with 25/200mW VTX
- 75mm between motors in diagnoal
- I choose the DSMX micro receiver

![BetaFPV Beta75X Whoop Quadcopter](/assets/images/Beta75X-3S-Whoop-Quadcopter.webp)

## Batteries 350mAh 2S

- I am actually starting with [their 2S batteries][betafpv2sbattery] that should be easier to learn how to fly indoor
  - 2S 7.4V 35C (70C peak)
    - the 8000Kv motors can thus reach ~59k RPM
  - 350mAh
  - weight 20g, dimensions 57x16x12mm
  - XT30 connector, 20AWG wire
  - JST-XH balance lead connector
  - Flight time ~4 minutes

![BetaFPV 350mAh 2S battery](/assets/images/BetaFPV-350mAh-2S-Battery.webp)

### Batteries 300mAh 3S

- The plan is to upgrade later to [their 3S batteries][betafpv3sbattery] to offer much increased power
  - 3S 11.1V 45C
    - the 8000Kv motors can thus reach ~59k RPM
  - 300mAh
  - weight 26g

## Jumper T12 Plus Radio Controller and Transmitter

- [Jumper T12 Plus (hall) black][jumpert12plus]
- 2.4ghz Multi-Protocol Module, on the JR/FrSKY compatible module bay
- 16 channels, 12 actuators:
  - 4x Hall Effect Gimbals (ch1,2,3,4)
  - 2x 2-state switches
  - 4x 3-state switches
  - 2x aux wheels

- Open TX Software
- 1.7" LCD screen (tiny)
- Weight: 342g (without battery)
- 2S lipo battery, through the JST-XH balance lead connector
  - I ordered an Azpro 2s 1000mAh 45C (5C charge)
- Simulator mode: 3.5mm standard ppm output or USB HID

![Jumper T12 Plus (hall) black](/assets/images/Jumper-T12-Plus-black.jpg)

## HTRC T240 Duo Lipo Charger

- Dual charger, 1S-6S LiPo batteries (but also LiFe, NiCd, NiMh etc)
- LCD screen, programmable charge rates with memory, battery diagnostics
- 240V AC or 12V DC input

![T240 Duo Lipo Charger](/assets/images/T240-DUO-Battery-Charger.jpg)

## Future

The firmware are open-source, and also configurable and programmable, which is especially important on the flight controller, so I might dig deeper into these.

As for the hardware, I might consider buying a FPV screen/mask to fly arround.
It is possible that I will wait instead for HD digital solution to take over, as the analog old school TV look of it is not my favorite...

I might one day opt for a bigger drone, into the cinewhoop category for example.

### RC Planes

Edit December 2022: the future is there, and I have now built not one, but two RC planes!
See [DIY Depron RC Plane][diy-depron].

[betafpv75x]: https://betafpv.com/products/beta75x-whoop-quadcopter-3s
[betafpv2sbattery]: https://betafpv.com/products/350mah-2s-lipo-battery-2pcs
[betafpv3sbattery]: https://betafpv.com/products/300mah-3s-45c-lipo-battery-s-version-2pcs
[jumpert12plus]: https://www.jumper-rc.com/products/transmitters/t12-plus/
[diy-depron]: /2022/11/26/diy-depron-rc-plane/