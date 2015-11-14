Panel8x8 with SD Card Reader

# Introduction #

The SD Card reader is example 9.


# Details #

I found this picture I sent to Paul early in the design process that shows 4 boards, <br>
how I powered them, <br>
and how I hooked them up to an SD Reader.<br>

<img src='http://panel8x8.googlecode.com/files/SDCardBoards.jpg' />

Basically,<br>
Digital 4, 5, 6, 7 are used to communicate with the panels.<br>
Digital 13, 12, 11, 10 are use to communicate with the SD card<br>
Both devices need power as well +5v, Ground.<br>

DIST is a power distributor module that I designed.<br>
Jumpters between the boards to provide a power bridge,<br>
But also has 2 2.1mm jacks to allow easy power connections,<br>
Of course the power bridge and connectors are all tied together.<br>

See readme text in Example 9 for more information.<br>
<br>
Note: I could probably decrease pin usage by 3 pins by combining SPI's, and just setting a CS bit.  Problem was, I wasn't sure how to combine a software and a hardware SPI.