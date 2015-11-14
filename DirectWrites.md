#DirectWrites

# Introduction #

Writing directly to the panels

# Details #

Writing directly to the panels is as easy as:
  * Setup up the Panels to Live/Locked
  * Preparing your output buffer
  * Dump this to Panel Buffer
  * Call the Scroll method

Note: You could cut out the middle man and write directly to the Panel Buffer.  That would cut down a few cycles but you've probably got a few to burn anyhow...


```
#include <Panel8x8.h>     // Declare an object of type 
Panel8x8 Panel;           // Local storage 
byte buffer[PANELS][8];   // Working Buffer

void setup() {  
 Panel.Begin(0,0,0,0);    // Initialize with no buffers
 Panel.SetScrolling(0);   // turn off scrolling
 Panel.PanelMode=3;       // direct animation mode
 Panel.frameDelay=500;    // slow it down!!
 Panel.ClearOutput();     // just for safetey
}

void display() {
 memcpy(Panel.iScroll,buffer,PANEL*8); // blast work buffer into display buffer
 Panel.Scroll();                       // now output it  
}

void loop() {
 // do something to buffer
 int i, j;             
 for (i=0; i<8; i++) {
  for (j=0; j<256; j++) {
   buffer[0][i]=j;
   // and display it
   display();
  }
  // all leds on might overdrive power supply
  buffer[0][i]=0;
 }
}
 
```