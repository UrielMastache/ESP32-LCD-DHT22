# Practica ESP32 con DHT22 y una Pantalla LCD 16x2
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y visualizar los datos recabados en una pantalla LCD.

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno, posteriormente observaremos los datos recabados por el sensor en la pantalla (```LCD 16x2 I2C```); Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- Pantalla LCD 16x2 (I2C)
- Y muchas ganas de chambear :D


## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:


```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");
  delay (3000);
  lcd.setCursor(0, 0);
  lcd.print("Tenga buen dia");
lcd.setCursor(0, 1);
  lcd.print("  Nos vemos      ");
  delay (1500);
  lcd.setCursor(0, 0);
lcd.print("   Made by      ");
lcd.setCursor(0, 1);
  lcd.print("    Uriel M");
  delay(1000);
}
```
2. En la parte final del codigo, es para mostrar un pequeño mensaje en la pantalla LCD, puede modificarse y escribir lo que guste.

3. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/Descargando%20libreria%20para%20sensor.png?raw=true)

4. Instalar la libreria de **LiquidCrystal I2C** en caso de que no se le agregre automaticamente al insertar su pantalla LCD.

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/Libreria%20de%20pantalla%20LCD.png?raw=true)

5. Hacer la conexion de **DHT22** con la **ESP32** y la pantalla **LCD 16x2 I2C** como se muestra en la siguente imagen.

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/Conexiones%20LCD%20y%20sensor.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial y en la pantalla LCD.

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial (parte blanca de abajo, así como también en  la pantalla LCD agregada) como se muestra en las siguentes imagenes.

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/Simulacion%20con%20LCD%20(2).png?raw=true)

Mensaje 1

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/mensaje%202.png?raw=true)

Mensaje 2

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/mensaje%203.png?raw=true)

## Comentarios

Recuerda que puedes cambiar los mensajes finales en la patanlla LCD desde el codigo, en la parte final. Así como también recuerda que puedes cambiar los valores del sensor dandole clic a este mismo, y cambiara en tiempo real.

![](https://github.com/UrielMastache/ESP32-LCD-DHT22/blob/main/Cambiando%20los%20valores.png?raw=true)

Gracias por ver :D 

Ciao.