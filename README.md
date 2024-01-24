# RC-Boat-Speed-Log

This project  takes the pulse from a paddlewheel boat speed sensor and makes an NMEA output on the serial port. With the help of this project, it is possible to measure the speed on both RC models (ArduPilot) and yachts.

 - On power-up the microcontroller waits for a +++ sequence for a few seconds, if it receives it, it enters a **calibration mode** so you can change things like the filter pole and the number of pulses per mile.
 - To **test** the unit: If you wire the output pin to the input pin you should get around 6.3 knots.
 - The number of pulses per mile is calculated from the linear velocity formula =>  **V=2𝝅Rn** Since the radius of my paddle wheel is 0.01m, the formula implies about 29470 pulses. If you have another one, then count it. You can set it more accurately in calibration mode.


## Component(Aliexpress):

 - Arduino pro mini         https://megabonus.com/y/8VERw                     
 - Resistance 10K           https://megabonus.com/y/9BL1f                 
 - Hall sensor              https://megabonus.com/y/bH1Aw
 - Maget 3x6mm              https://megabonus.com/y/RYdcj

##  Circuit diagram 
  -  input pin #3
  -  test pin #10


![Screenshot](screen.png)

## Корпус \ Housing 
![Screenshot](Body.png)

## Other
- turn off the filter (if the wheel stops abruptly, the speed will not be zero)

In the filter code section:

    adt = a_filt*(float)dt_update*1.0e-6;
    if (adt < 1.0)
    {
      speed_filt = speed_filt + adt*(speed_raw - speed_filt);
    } else {
      speed_filt = speed_raw; 
    }  
    
Replace with:
     speed_filt = speed_raw;
