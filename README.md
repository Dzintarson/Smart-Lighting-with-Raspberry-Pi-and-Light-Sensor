# Smart-Lighting-with-Raspberry-Pi-and-Light-Sensor
Adjusting lighting in a smart home using Raspberry Pi and a light sensor.
import RPi.GPIO as GPIO
import time

light_pin = 17
sensor_pin = 18

GPIO.setmode(GPIO.BCM)
GPIO.setup(light_pin, GPIO.OUT)
GPIO.setup(sensor_pin, GPIO.IN)

def adjust_light():
    light_value = GPIO.input(sensor_pin)

    if light_value == GPIO.HIGH:
        GPIO.output(light_pin, GPIO.LOW)  # Turn on light
    else:
        GPIO.output(light_pin, GPIO.HIGH)  # Turn off light

try:
    while True:
        adjust_light()
        time.sleep(1)
except KeyboardInterrupt:
    GPIO.cleanup()
