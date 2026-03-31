# Sensor DHT11 con Arduino

## 📋 Descripción
Este proyecto utiliza un sensor de temperatura y humedad DHT11 con Arduino IDE para medir temperatura y humedad ambiental en tiempo real.

## 📸 Diagrama de Conexión
![Diagrama de conexión](Diagrama%20de%20conexi%C3%B3n.png)
![Diagrama de conexión](Diagrama%20de%20conexi%C3%B3n%202.png).

## 💻 Código Arduino

```cpp
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
  delay(2000);
}

void loop() {
  float humedad = dht.readHumidity();
  float temperatura = dht.readTemperature();

  if (isnan(humedad) || isnan(temperatura)) {
    Serial.println("Error al leer el sensor DHT11");
    delay(2000);
    return;
  }

  Serial.print("Temperatura: ");
  Serial.print(temperatura);
  Serial.print(" °C - Humedad: ");
  Serial.print(humedad);
  Serial.println(" %");

  delay(2000);
}
```

## 🔧 Componentes Necesarios
- Arduino UNO + Cable USB
- Sensor DHT11
- Cables de conexión (Jumper)
- Protoboard (Opcional)

## 📌 Conexiones
El sensor DHT11 se conecta al Arduino mediante:
- **VCC**: +5V del Arduino
- **GND**: GND del Arduino
- **DATA**: Pin digital 2 del Arduino (configurable en el código)

## 💡 Cómo Utilizar

### Paso 1: Instalar la Librería DHT
1. Abre Arduino IDE
2. Ve a **Sketch** → **Incluir librerías** → **Administrar librerías**
3. En el buscador, escribe "DHT"
4. Busca "DHT sensor library" de Adafruit y haz clic en **Instalar**
5. También instala "Adafruit Unified Sensor" si lo solicita

### Paso 2: Conectar el Hardware
1. Desconecta el Arduino del USB
2. Conecta los cables según el diagrama:
   - VCC del DHT11 a +5V del Arduino
   - GND del DHT11 a GND del Arduino
   - DATA del DHT11 al pin 2 del Arduino

### Paso 3: Cargar el Código
1. Copia el código Arduino proporcionado
2. Abre Arduino IDE y crea un nuevo sketch
3. Pega el código en el editor
4. Selecciona **Herramientas** → **Placa: Arduino UNO**
5. Selecciona el puerto COM correspondiente (**Herramientas** → **Puerto**)
6. Haz clic en **Subir** (botón con flecha)

### Paso 4: Monitorear los Datos
1. Abre el **Monitor Serial** (Herramientas → Monitor Serial)
2. Asegúrate que la velocidad sea **9600 baudios**
3. Verás la temperatura en °C y la humedad en % actualizándose cada 2 segundos

### Paso 5: Prueba del Sensor
- Acerca tu mano al sensor para ver cómo cambia la temperatura
- Respira sobre el sensor para ver cómo aumenta la humedad
- Verifica que los valores sean lógicos

## 🐛 Solución de Problemas

### Problema: No aparecen datos en el Monitor Serial
**Soluciones:**
- Verifica que la velocidad del Monitor Serial sea **9600 baudios**
- Comprueba que el Arduino esté seleccionado en **Herramientas** → **Placa: Arduino UNO**
- Verifica que el puerto COM sea el correcto

### Problema: Mensaje de error "Error al leer el sensor DHT11"
**Soluciones:**
- Revisa que todas las conexiones estén firmes
- Asegúrate de que el pin DATA del sensor esté conectado al **pin 2** del Arduino
- Intenta cambiar el pin (por ejemplo, a pin 3) y actualiza `#define DHTPIN 2` en el código
- Verifica que la librería DHT esté correctamente instalada
- Intenta desconectar y reconectar el Arduino

### Problema: Valores incorrectos o inestables
**Soluciones:**
- Asegúrate que hay una resistencia de 4.7k Ω entre VCC y el pin DATA
- Verifica que no haya cables rotos o mal conectados
- Cambia de cable o utiliza un cable más corto
- Espera a que el sensor se estabilice después de iniciar (tarda unos segundos)

### Problema: No reconoce la librería DHT
**Soluciones:**
- Abre **Sketch** → **Incluir librerías** → **Administrar librerías**
- Busca "DHT" nuevamente y verifica que esté instalada y sea de Adafruit
- Si no está, instálala
- Reinicia Arduino IDE después de instalar

### Problema: El Arduino no sube el código
**Soluciones:**
- Verifica que el Arduino UNO esté seleccionado en **Herramientas** → **Placa**
- Comprueba que el puerto COM sea correcto
- Intenta desconectar y conectar nuevamente el cable USB
- Presiona el botón de **Reset** en el Arduino y luego carga el código rápidamente

## 📊 Características del DHT11
- **Rango de temperatura:** 0 °C a 50 °C (±2 °C)
- **Rango de humedad:** 20% a 90% (±5%)
- **Voltaje de operación:** 3,3 V a 5 V
- **Corriente de consumo:** 0,5 mA a 2,5 mA
- **Tiempo de lectura:** 2 segundos (Configurado en el programa)

## 💡 Notas Adicionales
- El sensor DHT11 necesita tiempo para estabilizarse, por eso el delay de 2 segundos
- No conectes el sensor a más de 5V, puede dañarse
- El sensor es sensible a la humedad extrema, mantenlo en un ambiente normal
- Para mejores resultados, mantén el sensor en un lugar ventilado
