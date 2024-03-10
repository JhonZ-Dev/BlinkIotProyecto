# BlinkIotProyecto
#define BLYNK_TEMPLATE_ID "TMPL2YPo6x419"
#define BLYNK_TEMPLATE_NAME "ProyectoU3 Olalla Zambrano"
#define BLYNK_AUTH_TOKEN "1mMg2AXtyrEgiR7U0zRfti7SSTM71qNj"




#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>


// Datos de conexión a WiFi
char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "Emergentes";
char pass[] = "HolaAmigos";


void setup()
{
  // Inicializar la conexión WiFi
  WiFi.begin(ssid, pass);


  // Inicializar la comunicación con el servidor Blynk
  Blynk.begin(auth, ssid, pass);


  // Configurar el pin del LED integrado como salida
  pinMode(LED_BUILTIN, OUTPUT);
}


void loop()
{
  // Actualizar la conexión con el servidor Blynk
  Blynk.run();
}


// Función para controlar el estado del LED desde la aplicación Blynk
BLYNK_WRITE(V0)
{
  int ledState = param.asInt();


  // Encender o apagar el LED integrado según el estado recibido
  if (ledState == HIGH)
  {
    digitalWrite(LED_BUILTIN, LOW);  // Enciende el LED (nivel bajo)
  }
  else
  {
    digitalWrite(LED_BUILTIN, HIGH); // Apaga el LED (nivel alto)
  }
}

