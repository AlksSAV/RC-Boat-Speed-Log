# RC-Boat-Speed-Log

Проект по созданию морского лага, для измерения скорсти модели относительно воды. \
A project to create a sea log to measure the speed of the model through water.

 - On power-up the microcontroller waits for a +++ sequence for a few seconds, if it receives it, it enters a **calibration mode** so you can change things like the filter pole and the number of pulses per mile. To **test** the unit: If you wire the output pin to the input pin you should get around 6.3 knots. The input would normally be connected to a signal that is either a TTL pulse signal (0-5 Volts square wave).

- Коэффициент в скетче расчитан изходя из размеров "колеса"(один импульс на оборот колеса). Необходимо ввести количество импульсов на скорость в один узел. V=2𝝅Rn (линейная скорость).

- отключить фильтр(при резкой остановке колеса скорость не будет ноль) 

 В разделе кода фильтра:

    adt = a_filt*(float)dt_update*1.0e-6;
    if (adt < 1.0)
    {
      speed_filt = speed_filt + adt*(speed_raw - speed_filt);
    } else {
      speed_filt = speed_raw; 
    }  
    
Заменить на:
     speed_filt = speed_raw;

## Компоненты\Component(Aliexpress):

 - Ардуино        Arduino Uno\Pro etc.     https://megabonus.com/y/8VERw                     
 - Резистор 10K   Resistance 10K           https://megabonus.com/y/9BL1f                 
 - Датчик Холла   Hall sensor              https://megabonus.com/y/bH1Aw

## Схема подключения \ Circuit diagram 

![Screenshot](screen.png)

## Корпус \ Housing 
![Screenshot](Body.png)
