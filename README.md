# Control del servomotor con raspberry pi pico

# Tabla de contenidos
1. [Materiales](#Materiales)
2. [Descripción](#Descripción)
3. [Código](#Código)

## Materiales
* Raspberry pi pico
* Servomotor
* Protoboard
* Jumpers 
* Fuente de alimentación de 5V


## Descripción

Un servomotor es un motor eléctrico que hace accionar partes de una maquina con alta eficiencia y precisión.
Los servomotores se aplican en muchos sistemas y productos industriales como la robótica, la automatización, la manipulación de materiales, farmacéutica, brazos robóticos.

Partes de un servomotor:
- Motor DC: es el principal componente del servo el cual proporcionara el movimiento.
- Engranajes reductores: se encarga de reducir la velocidad de giro del motor para incrementar su capacidad de torque.
- Tarjeta de control: es la encargada de enviar información y de alimentar al motor.

![5](https://github.com/victorgjacobo/servomotor_raspberry_pi_pico/assets/141197135/c000ab10-094a-4378-91ab-861470c303d4)

El funcionamiento del servomotor se debe a la modulación por ancho de pulso (PWM). La frecuencia utilizada para enviar la secuencia de pulsos al servomotor es de 50 Hz, lo que significa que cada ciclo tiene una duración de 20 milisegundos.  

![6](https://github.com/victorgjacobo/servomotor_raspberry_pi_pico/assets/141197135/fb84c651-1ce4-42ce-bd10-9baa8aa4791d)

El pin del servomotor para recibir la señal PWM de la raspbeerry pi pico se muestra en la siguiente figura: `PWM -> GPIO 15`.

![segunda_practica](https://github.com/victorgjacobo/servomotor_raspberry_pi_pico/assets/141197135/8fe1169e-3e2a-4f98-a2b7-685cedd311b7)

## Código
```python
"""
  Nombre de la práctica: Control del servomotor con raspberry pi pico
  Autor: Ing. Víctor González Jacobo
"""
from machine import Pin, PWM
import utime

def main():    
    servo = PWM(Pin(15))
    servo.freq(50) #periodo de 20 ms = 1/ped=freq
    while True:
        angulo = float(input('Ingrese un ángulo: '))
        if angulo >= 0 and angulo <= 180:
            duty = int(4.9383*angulo**2 + 9000*angulo + 550000)
            servo.duty_ns(duty) 
        else:
            print('Digite un ángulo entre 0 y 180')
        
        
if __name__ == '__main__':
    main()
```

![](https://img.shields.io/github/watchers/victorgjacobo/servomotor_raspberry_pi_pico)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Raspberry Pi](https://img.shields.io/badge/-RaspberryPi-C51A4A?style=for-the-badge&logo=Raspberry-Pi)
![GitHub followers](https://img.shields.io/github/followers/victorgjacobo)
