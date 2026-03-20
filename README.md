# Sensor DHT11 con Arduino

## 📋 Descripción
Este proyecto utiliza un sensor ultrasónico HC-SR04 con Arduino IDE para medir distancias.

## 📸 Diagrama de Conexión
![Diagrama de conexión](Diagrama%20de%20conexi%C3%B3n.png)

## 💻 Código Arduino

```cpp
#include <DHT.h>

#define DHTPIN 2        // Pin donde conectas el DHT11
#define DHTTYPE DHT11   // Tipo de sensor

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float humedad = dht.readHumidity();
  float temperatura = dht.readTemperature();

  // Verifica si hay error en la lectura
  if (isnan(humedad) || isnan(temperatura)) {
    Serial.println("Error al leer el sensor DHT11");
    return;
  }

  Serial.print("Humedad: ");
  Serial.print(humedad);
  Serial.print(" %  ");

  Serial.print("Temperatura: ");
  Serial.print(temperatura);
  Serial.println(" °C");

  delay(2000); // Espera 2 segundos
}
```

## 🔧 Componentes Necesarios
- Arduino UNO
- Sensor Ultrasónico HC-SR04
- Cables de conexión (Jumper)
- Protoboard (Opcional)

## 📌 Conexiones
El sensor HC-SR04 se conecta al Arduino mediante:
- **VCC**: +5V
- **GND**: GND
- **TRIG**: Pin digital (por ejemplo, pin 9)
- **ECHO**: Pin digital con entrada analógica (por ejemplo, pin 10)

## 💡 Cómo Usar
1. **Conecta los componentes** según el diagrama de conexión
2. **Carga el código Arduino** en tu placa usando Arduino IDE
3. **Abre el Monitor Serial** (Herramientas → Monitor Serial) a 9600 baudios
4. **El sensor mostrará las distancias medidas** en centímetros en tiempo real
5. **Acerca y aleja objetos** del sensor para ver cómo cambian las lecturas
6. El rango de detección es aproximadamente de 2 cm a 400 cm

## 🐛 Solución de Problemas
- Si no ves lecturas, verifica las conexiones
- Asegúrate de que los pines coincidan con el código (pin 9 y 10)
- Asegurate que la velocidad serial sea de 9600

