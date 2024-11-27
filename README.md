# ESP32-con-pantalla-segundos

import time
from machine import Pin, I2C
import lcd

# Inicializar I2C
i2c = I2C(0, scl=Pin(22), sda=Pin(21), freq=400000)  # GPIO22 para SCL, GPIO21 para SDA

# Inicializar pantalla LCD (en este caso una LCD 16x2)
lcd = lcd.LCD(i2c)

# Configurar el LCD
lcd.clear()

# Contador de segundos
segundos = 0

# Bucle para actualizar el tiempo en la pantalla LCD
while True:
    # Mostrar el tiempo en segundos en el LCD
    lcd.clear()  # Limpiar la pantalla antes de mostrar el nuevo tiempo
    lcd.putstr("Segundos:")  # Texto estático
    lcd.putstr(str(segundos))  # Mostrar el contador de segundos
    time.sleep(1)  # Esperar 1 segundo
    segundos += 1  # Incrementar el contador de segundos
