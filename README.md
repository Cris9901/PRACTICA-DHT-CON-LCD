# PRACTICA DHT CON LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT11 y un display Lcd.
## Introducción
### Descripción
La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno, asi como también un display (```Lsd```) para visualizar los datos; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).
## Material Necesario
Para realizar esta practica necesitas lo siguiente
- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT11
- Display Lsd
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

  delay(1000);
}
```
2. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.
![]()
3. Instalar la libreria de **LiquidCrystal I2C** como se muestra en la siguente imagen.
![]()  
4. Hacer la conexion de **DHT22** con la **ESP32** como se muestra en la siguente imagen.
![]()
5. Hacer la conexion de **LCD 16x2 (I2C)** con la **ESP32** como se muestra en la siguente imagen.
![]()

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT22** 

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial y el display como se muestra en la siguente imagen.
![]()

# Créditos
Desarrollado por Ing. Montañez Mejia Cristian
