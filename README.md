# Script Code
import time import board import adafruit_dht import psutil

for proc in psutil.process_iter(): if proc.name() == 'libgpiod_pulsein' or proc.name() == 'libgpiod_pulsei': proc.kill() sensor = adafruit_dht.DHT11(board.D23) while True: try: temp = sensor.temperature humidity = sensor.humidity print("Temperature: {}*C Humidity: {}% ".format(temp, humidity)) except RuntimeError as error: print(error.args[0]) time.sleep(2.0) continue except Exception as error: sensor.exit() raise error time.sleep(2.0)

# Wiring diagram
![WhatsApp Image 2022-07-21 at 16 48 18](https://user-images.githubusercontent.com/107263378/180355713-689e9321-8659-4470-b96d-e31892390b84.jpeg)
 
# Data Sensor
![2022-07-15-134846_1366x768_scrot](https://user-images.githubusercontent.com/107263378/180356025-0fd90d50-38b6-4b9a-b59c-1bbbbdade300.png)

# Data Graphic
![2022-07-15-135933_1366x768_scrot](https://user-images.githubusercontent.com/107263378/180356279-a82ffaaa-53a9-4d51-91e0-6d80a04b8ade.png)
