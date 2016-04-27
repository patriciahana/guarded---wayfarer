# guarded---wayfarer
My Amazing Project-IEA Raspberry Pi 2016 Competition Entry
# Description
Lycée Laure Mougayzel Team has developed a project that aims at assisting and helping children, adults, and the elderly as they walk down the street, in other words, any person who commutes by foot, uses public transport or travels by car on a daily basis.
Thepurpose of this project is to raise awareness on road safety issuesamong pedestrians, commuters and drivers.“GuardedWayfarer” will securethe full safety of people on the roads; it compels them to abide by the law and protects them from road accidents and hazards such as road injuriesand fatalities. 
Our project consists of the following:
1-APibrellaconnected to our Raspberry Pi to set off the alarm
2-A sensor thatoperates as motion detector to sense every moving vehicle. We also used five LEDs: three for the carsfor the purpose of the traffic lights and two for pedestrians. 
So how does it work? 
 “Guarded Wayfarer” focuses on two major focal points: the sensor and the alarm.
As soon as the traffic light is red, the pedestrians’ light automatically turns green.In the meantime, the alarm immediately operates. Meanwhile, in case a car runs the red light by almost 50 centimeters further, the alarm goes off.


Note: “Guarded Wayfarer” is the name of the project

import RPi.GPIO as GPIO
import pibrella
import time


def beep(count):
    for i in range(count):
        pibrella.buzzer.note(1)
        time.sleep(.1)
        pibrella.buzzer.stop()
        time.sleep(.1)
def reading():
    GPIO.output(Trig, False)
    time.sleep(0.3)
    GPIO.output(Trig, True)
    time.sleep(0.001)
    GPIO.output(Trig, False)

    while GPIO.input(Echo)==0:
        signalOff=time.time()

    while GPIO.input(Echo)==1:
        signalOn=time.time()

    timePassed=signalOn-signalOff
    distance=timePassed*17150

    return distance
    
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)

Trig = 15
Echo = 14
RedLed = 27
RedPLed = 24
OrangeLed = 22
GreenLed = 9

GPIO.setup(Trig, GPIO.OUT)#sensor
GPIO.setup(Echo, GPIO.IN)#sensor
GPIO.setup(RedLed,GPIO.OUT)#red led
GPIO.setup(RedPLed,GPIO.OUT)#red led pediatran
GPIO.setup(OrangeLed,GPIO.OUT)#orange led
GPIO.setup(GreenLed,GPIO.OUT)#green led


while True:
    GPIO.output(GreenLed,True)
    GPIO.output(RedPLed,True)
    GPIO.output(RedLed,False)
    GPIO.output(OrangeLed,False)
    time.sleep(3)
    GPIO.output(GreenLed,False)
    GPIO.output(OrangeLed,True)
    GPIO.output(RedPLed,True)
    GPIO.output(RedLed,False)
    time.sleep(3)
    GPIO.output(RedLed,True)
    GPIO.output(RedPLed,False)
    GPIO.output(OrangeLed,False)
    GPIO.output(GreenLed,False)
    start_time=time.time()

    while((time.time() - start_time)< 5 ):
        distance = reading()
        print distance
        if distance<20:
            beep(1)
    GPIO.output(RedLed,False)    
    GPIO.output(OrangeLed,True)
    GPIO.output(RedPLed,True)
    GPIO.output(GreenLed,False)
    time.sleep(3)
    
 
 + Team 
 + patricia hanna
 + andrina el chami
 + georgia nemri
 + elissa bou aoun 
 + sarah abou jamra
