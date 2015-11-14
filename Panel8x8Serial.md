#Panel8x8Serial

# Introduction #

This is the serial update object required to support the Panel8x8Support package.

# Details #

Monitors the serial port (0/1) for commands from host

Methods:
| About() | Displays library version to serial or debug. |
|:--------|:---------------------------------------------|
| Begin(buffer,maxlen,currentlen,isRom=0/1) | Initializes object at 9600 baud.             |
| CheckSerial() | Checks for commands on serial port.          |
| Loop()  | Replacement for Panel8x8 Loop (calls CheckSerial). |

Switches: (must define in Panel8x8Serial.h)
| DEBUG8X8SERIAL | Enables debuging on a NewSoftSerial port. |
|:---------------|:------------------------------------------|

Serial Commands: (passed on pin 0, RX)
| Esc C | Clear Panels |
|:------|:-------------|
| Esc I + FrameDelay + Length + Text | Load Text    |
| Esc F + Version + Panels + FrameDelay + Data | Load Animation to RAM |
| Esc L + Version + Panels + FrameDelay + Data | Live Stream Animation |
| Esc S + Byte + Data | Settings Mode (Future use) |

Usage: (5 simple lines of code)
```
#include <Panel8x8Serial.h>
Panel8x8Serial panel;
char *buffer[512]=".   ";
void setup(){panel.Begin(buffer,512,strlen(buffer),0);}
void loop(){panel.Loop();}
```

To use DEBUG8x8Serial:
Port must be previously defined and passed to the panel object.  ie:
```
#include <NewSoftSerial.h>
NewSoftSerial debug(18,19); // Uses pins A4,A5
#include <Panel8x8Serial.h>
Panel8x8Serial panel(&debug);
char *buffer[512]=".   ";
void setup(){panel.Begin(buffer,512,strlen(buffer),0);}
void loop(){panel.Loop();}
```