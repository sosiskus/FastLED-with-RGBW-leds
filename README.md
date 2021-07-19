# FastLED with RGBW leds
This programm are FastLED library with support of RGBW leds. 
>Programm are in deeloping so RGBW leds support small amount of functions

## RGBW led strip setup
Firstly, we need to include custom FastLED library, so you need copy this library into *Arduino/libraries* and rename to FastLED, before that you need to remove old FastLED library.

    #include<FastLED.h>
   Then you need to define number of leds and led pin
   

> In my case it is 40 and D6

   

    #define NUM_LEDS 40
    #define LED_PIN 6
After that you need to declare RGBW leds using this code

    CRGBW leds[NUM_LEDS];
    CRGB* ledsRGB = (CRGB*)&leds[0];
   In `void setup()` function you need to initialize leds
   

> I do not recommend you to change color order, because it work corectly with all led strips

   

    FastLED.addLeds<WS2812B, LED_PIN, RGB>(ledsRGB, getRGBWsize(NUM_LEDS));
Finaly, you can use any of **supported functions** just passing to it `CRGBW(uint8_t red, uint8_t green, uint8_t blue, uint8_t white)` instead of `CRGB()`. For example

    fill_solid(leds, NUM_LEDS, CRGBW(0,0,0,255));
    

> In this case only white leds fill be on

There is list of **functions which support RGBW leds:**

 - fill_solid();
 - fill_gradient_RGBW();
 - leds[0] = CRGBW();
