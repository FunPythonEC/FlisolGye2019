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
# MicroPython
* Implementacion eficiente de Python.
* Permite transferir códigos del escritorio a un microcontrolador o un sistema embebido.
* Librerias de Python y funciones avanzadas-
# ESP8266 y ESP32
* microcontroladores de bajo costo
* Bluetooth y WiFi
* Compatibilidad con diferentes protocolos de comunicación (I2C, SPI, I2S, 1-Wire, UART).
---
# Syntanxis MicroPython
* if
~~~~ python
num = 3.4
if num > 0:
    print("Número positivo")
elif num == 0:
    print("Cero")
else:
    print("Número negativo")
~~~~
---
* While
~~~~ python
i = 1
while i < 6:
  print(i)
  if i == 3:
    break
  i += 1
~~~~
---
# Aplicaciones 
* conexion wifi
* tiras LED
* manejar motores (servomotor, motor DC)
---
# Conexion Wifi
~~~~ python
import network
import socket
import time

wlan = network.WLAN(network.STA_IF)
wlan.active(True)

a=wlan.scan()
for i in range(0,len(a)):
    print(a[i][0])
~~~~
~~~~ python
import network

wlan = network.WLAN(network.STA_IF)
wlan.active(True)
if not wlan.isconnected():
    print('connecting to network...')
    wlan.connect("","")
    while not wlan.isconnected():
        pass
print('network config:', wlan.ifconfig())
~~~~
---
~~~~ python
import socket
import time

html= """<html>
  <head>
    <meta charset="uft-8"/>
    <title>Hola Mundo en HTML</title>
  </head>
  <body>
    <h1>Hola Mundo Fun</h1>
  </body>
</html>"""

#Setup Socket WebServer
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
time.sleep(1)
s.bind(('', 80))
s.listen(5)
while True:
    conn, addr = s.accept()
    request = conn.recv(1024)
    request = str(request)
    print(request)        
    response = html
    conn.send(response)
    conn.close()
~~~~
---
# Tiras NeoPixel
~~~~ python
from machine import Pin
from neopixel import NeoPixel
import time

pin = Pin(14, Pin.OUT)   # set GPIO0 to output to drive NeoPixels
np = NeoPixel(pin, 100)   # create NeoPixel driver on GPIO0 for 8 pixels
for i in range(100): 
  np[i] = (255,20,147)
  np.write()
  time.sleep_ms(100)
~~~~
# Alternar colores NeoPixel
~~~~ python
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
 ~~~~   
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
---
# Requerimientos
2 Fuentes/adaptadores (12 V)
2 Cables USB
1 Tiras LED
1 Servo Motor
1 Tarjeta de voltaje
1 ESP 32
Jumpers Macho-Macho y Macho-Hembra
1 Multimetro
1 Protoboard
1 Web Cam

# Licencia
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Namensnennung 4.0 International Lizenz</a>.
