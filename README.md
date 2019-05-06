<!-- $theme: default -->
<!-- page_number: true -->

# Introducción a MicroPython como lenguaje de desarrollo para dispositivos IoT
# Valeria Solano / José Laica
## FunPython


##### FLISOL2019 
			 Guayaquil - Ecuador
---
* Presentacion de expositores (3 mins)
* Presentación de la comunidad FunPython - ¿Qué hacemos? ¿Por qué lo hacemos? Nuestra filosofía y forma de trabajo. (3 mins) JL
* Presentación de lo utilizado (3 mins) VS
	* MicroPython
	* MicroControladores ESP
* Porque MicroPython (3 mins) JL
* Syntaxix MicroPython: (5 mins) VS
	* Sentencias: if, for, while
* Aplicaciones:
    * Conexion Wifi (3 mins) VS
	* Tiras LED (5 mins) JL
	* manejar motores (servomotor, motor DC) (10 mins) 
---
# Valeria Solano
* Soy Valeria Solano, estudiante de ingeniería Mecatrónica en la ESPOL, me apasiona la robótica y poder generar un impacto social y tecnológico a través de sus aplicaciones. Siempre busco participar en nuevos retos y proyectos para aprender de ellos y así mismo poder transmitir mis conocimientos a otros. Intento siempre demostrar de lo que somos capaces las mujeres en la ingeniería y la ciencia, rompiendo paradigmas e inspirando a otros a hacerlo también.
---
# Jose Laica
---
# FunPython 
---
# Video Fun 
---
# MicroPython y controladores ESP
# Porque MicroPython
---
# Syntaxix MicroPython
* ejemplos: if, for, while
---
# Aplicaciones 
* conexion wifi
* tiras LED
* manejar motores (servomotor, motor DC)
---
# Tiras LED
from machine import Pin
from neopixel import NeoPixel
import time

pin = Pin(14, Pin.OUT)   # set GPIO0 to output to drive NeoPixels
np = NeoPixel(pin, 100)   # create NeoPixel driver on GPIO0 for 8 pixels
for i in range(100): 
  np[i] = (255,20,147)
  np.write()
  time.sleep_ms(100)
# Alternar colores
from machine import Pin
from neopixel import NeoPixel
import time

pin = Pin(14, Pin.OUT)   # set GPIO0 to output to drive NeoPixels
np = NeoPixel(pin, 100)   # create NeoPixel driver on GPIO0 for 8 pixels
for i in range(100): 
  if i%2==0:
    np[i] = (255,20,147)
    np.write()
    time.sleep_ms(100)
  if i%2!=0:
    np[i] = (0,255,0)
    np.write()
    time.sleep_ms(100)
    
---
# Uso de servos

~~~~ python
import machine
import Servo
serv=Servo.Servo(machine.Pin(13))
serv.write_angle(degrees=100)
~~~~

# Uso de for para servos

~~~~ python
import machine
import Servo
import time
serv=Servo.Servo(machine.Pin(13))
for i in range(180):
   serv.write_angle(degrees=i)
   time.sleep_ms(50)
~~~~

---
# “No esperes resultados diferentes si siempre haces lo mismo” - Albert Einstein
---
# "Yo no conozco el futuro. No he venido para decirles cómo acabará todo esto. Al contrario, he venido a decirles cómo va a comenzar" - Neo-Matrix, 1999.
