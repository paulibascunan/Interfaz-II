##### Introducción a processing y arduino para el desarrollo de una interfaz interactiva
1. [Hola mundo](#ejercicio-numero-1-hola-mundo) <br>
2. [led parpadeante](#ejercicio-numero-2-led-parpadeante) <br>
3. [led pulsador](#ejercicio-3-led-pulsador) <br>
4. [led potenciómetro ](#ejercicio-4-led-potenci%C3%B3metro) <br>
5. [semáforo](#ejercicio-5-sem%C3%A1foro) <br>
6. [semáforo parpadeante](#ejercicio-n6-semaforo-parpadeante)  <br>
7. [processing](#ejercicio-7) <br>
8. [if else](#ejercicio-n-8-if-else) <br>
9. [for if](#ejercicio-n9-for-if) <br>
10. [botonera con sonido](#ejercicio-n10-botonera-con-sonido) <br>
11. [semáforo mas botón](d#ejercicio-n11-semaforo-mas-boton) <br>
12. [código sensor processing en grupo](#ejercicio-n12-codigo-sensor-processing-en-grupo) <br>
13. [ejercicio final](#ejercicio-final)  <br>
# Interfaz-II
##### ejercicio numero 1: hola mundo

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```


##### ejercicio numero 2: led parpadeante

```js
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);// Pin 13 como salida
  pinMode(8, OUTPUT);
}
void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo


 digitalWrite(8, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(8, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo
}
```
<img src="https://raw.githubusercontent.com/paulibascunan/Interfaz-II/refs/heads/main/img/led%20parpadeante.png"/>

##### ejercicio 3: led pulsador

```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/75eede3513025eafc13e3fa27e0231d9afa93c64/pulsador.png"/>


##### ejercicio 4: led potenciómetro

```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
}
```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/af092bc40aa82b4fb534ecdc3a89398a582f28b9/img/potenciometro.png"/>



##### ejercicio 5: semáforo

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```

<img src="https://raw.githubusercontent.com/paulibascunan/Interfaz-II/refs/heads/main/img/sem%C3%A1foro.png"/>


##### ejercicio n°6: semaforo parpadeante

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
   // Verde peatones encendido
  // 5 segundos
      digitalWrite(LED_4, HIGH);  // Encender LED
  delay(2000);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(2000);       
    digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo
 digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);  
   digitalWrite(LED_4, HIGH);  // Encender LED
  delay(500);             // Esperar 1 segundo
  digitalWrite(LED_4, LOW);   // Apagar LED
  delay(500);             // Esperar 1 segundo
// Esperar 1 segundo

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}

```


##### ejercicio 7:

```js
import processing.serial.*;

Serial myPort;
ArrayList<CircleData> circles; 

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
 myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
  //background(0);
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(168, 255, 131);
  stroke(255, 0, 0);
  for (CircleData c : circles) {
    ellipse(c.x, c.y, c.size, c.size);
  }
  
  // Leer datos de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); // tamaño 10-100 px
          circles.add(new CircleData(random(width), random(height), circleSize));
        }
      }
    }
```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/d7072d4a1b66c61a96476b9a26aa9d800d7f32ae/img/circulos%20potenciometro.png"/>


##### ejercicio n° 8: if else
```js
int valor;  // aquí guardaremos la lectura del sensor

void setup() {
  Serial.begin(9600);   // Inicia la comunicación serial
}

void loop() {
  valor = analogRead(A0);   // lee el pin analógico A0

  if (valor < 100) {
    Serial.println("Muy bajo");
  } else if (valor < 600) {
    Serial.println("Medio");
  } else {
    Serial.println("Alto");
  }

  delay(500); // medio segundo entre lecturas
}
}
}
```

##### ejercicio n°9: for if
```js
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 1 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
}

```
 ##### ejercicio n°10: botonera con sonido
```js
import processing.sound.*;

// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("campanillaB.mp3", 2048); 
  players[1] = minim.loadFile("campanillaÑ.mp3", 2048); 
  players[2] = minim.loadFile("campanillaZ.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}


```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/618c4a00e2da32f89323b587b4cfe3d2796660c4/img/botonera.png"/>

##### ejercicio n11 semaforo mas boton
``` js
// Semáforo Autos y Peatones con botón ON/OFF (sin delay) - CORREGIDO

// Pines LEDs
int LED_1 = 6; // Rojo autos
int LED_2 = 7; // Amarillo autos
int LED_3 = 8; // Verde autos
int LED_4 = 9; // Verde peatones
int LED_5 = 10; // Rojo peatones

// Pin botón
int boton = 2;

// Variables del botón
bool encendido = true;
int estadoBoton = 0;
int lastEstadoBoton = 0;
unsigned long lastDebounceTime = 0;
unsigned long debounceDelay = 50;

// Variables del semáforo
unsigned long previousMillis = 0;
int fase = 0;

void setup() {
pinMode(LED_1, OUTPUT);
pinMode(LED_2, OUTPUT);
pinMode(LED_3, OUTPUT);
pinMode(LED_4, OUTPUT);
pinMode(LED_5, OUTPUT);

pinMode(boton, INPUT);
}

void loop() {
// --- Leer botón con antirrebote ---
int lectura = digitalRead(boton);

if (lectura != lastEstadoBoton) {
lastDebounceTime = millis();
}

if ((millis() - lastDebounceTime) > debounceDelay) {
if (lectura != estadoBoton) {
estadoBoton = lectura;
if (estadoBoton == HIGH) {
encendido = !encendido; // Cambia el estado
}
}
}
lastEstadoBoton = lectura;

// --- Semáforo ---
if (encendido) {
unsigned long currentMillis = millis();

switch(fase) {
case 0: // Autos verde, peatones rojo
digitalWrite(LED_1, LOW);
digitalWrite(LED_2, LOW);
digitalWrite(LED_3, HIGH);
digitalWrite(LED_4, LOW);
digitalWrite(LED_5, HIGH);

if (currentMillis - previousMillis >= 5000) {
previousMillis = currentMillis;
fase = 1;
}
break;

case 1: // Autos amarillo, peatones rojo
digitalWrite(LED_3, LOW);
digitalWrite(LED_2, HIGH);
digitalWrite(LED_1, LOW);
digitalWrite(LED_4, LOW);
digitalWrite(LED_5, HIGH);

if (currentMillis - previousMillis >= 2000) {
previousMillis = currentMillis;
digitalWrite(LED_2, LOW); // Apagar amarillo al terminar
fase = 2;
}
break;

case 2: // Autos rojo, peatones verde
digitalWrite(LED_1, HIGH);
digitalWrite(LED_2, LOW);
digitalWrite(LED_3, LOW);
digitalWrite(LED_4, HIGH);
digitalWrite(LED_5, LOW);

if (currentMillis - previousMillis >= 5000) {
previousMillis = currentMillis;
fase = 3;
}
break;

case 3: // Ambos rojo (intermedio)
digitalWrite(LED_1, HIGH);
digitalWrite(LED_2, LOW);
digitalWrite(LED_3, LOW);
digitalWrite(LED_4, LOW);
digitalWrite(LED_5, HIGH);

if (currentMillis - previousMillis >= 2000) {
previousMillis = currentMillis;
fase = 0;
}
break;
}
} else {
// Apagar todos los LEDs si está apagado
digitalWrite(LED_1, LOW);
digitalWrite(LED_2, LOW);
digitalWrite(LED_3, LOW);
digitalWrite(LED_4, LOW);
digitalWrite(LED_5, LOW);
}
}

```

##### ejercicio n12 codigo sensor processing en grupo
``` js
import processing.serial.*;
import processing.sound.*;

Serial arduino;
int lectura = 0;

// Umbrales de distancia
int cerca = 300;
int medio = 500;
int lejos = 800;

// Sonido
SoundFile[] sonidos;
int sonidoIndex = 0;

void setup() {
  size(400, 400);
  println(Serial.list()); // Muestra los puertos disponibles
  arduino = new Serial(this, Serial.list()[0], 9600);

  // Cargar sonidos campanillaa-z.mp3
  sonidos = new SoundFile[26];
  for (int i = 0; i < 26; i++) {
    char letra = (char)('a' + i);  // minúsculas
    String nombre = "campanilla" + letra + ".mp3";
    sonidos[i] = new SoundFile(this, nombre);
  }
}

void draw() {
  background(0);

  // Leer datos del Arduino
  while (arduino.available() > 0) {
    String val = arduino.readStringUntil('\n');
    if (val != null) {
      val = val.trim();
      lectura = int(val);
    }
  }

  // Cambiar color según distancia
  if (lectura < cerca) {
    fill(255, 0, 0); // ROJO
    reproducirSonido();
  } else if (lectura < medio) {
    fill(255, 255, 0); // AMARILLO
  } else if (lectura < lejos) {
    fill(0, 255, 0); // VERDE
  } else {
    fill(50); // Gris oscuro (sin detección)
  }

  ellipse(width/2, height/2, 200, 200);

  // Mostrar lectura
  fill(255);
  textSize(16);
  textAlign(CENTER);
  text("Lectura: " + lectura, width/2, height - 30);
}

// Función para reproducir el siguiente sonido
void reproducirSonido() {
  if (!sonidos[sonidoIndex].isPlaying()) {
    sonidos[sonidoIndex].play();
    sonidoIndex = (sonidoIndex + 1) % sonidos.length; // Alternar a-z
  }
}
```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/abfa920a57c016b439a7aa1e3872ea80f6c45b62/img/Captura%20de%20pantalla%202025-11-10%20092452.png"/>

##### ejercicio final 
``` js
Processing:
import processing.serial.*;
import processing.sound.*;

Serial arduino;

// Tres sensores
int[] lectura = {0, 0, 0};

// Umbrales de distancia
int cerca = 300;
int medio = 500;
int lejos = 800;

// Sonidos independientes (26 para cada sensor)
SoundFile[][] sonidos;
int[] sonidoIndex = {0, 0, 0};

void setup() {
  size(600, 400);
  println(Serial.list());
  arduino = new Serial(this, Serial.list()[0], 9600);

  // Cargar sonidos: sonidos[sensor][letra]
  sonidos = new SoundFile[3][26];

  for (int s = 0; s < 3; s++) {
    for (int i = 0; i < 26; i++) {
      char letra = (char)('a' + i);
      String nombre = "campanilla" + letra + ".mp3";
      sonidos[s][i] = new SoundFile(this, nombre);
    }
  }
}

void draw() {
  background(0);

  // Leer datos del Arduino
  while (arduino.available() > 0) {
    String val = arduino.readStringUntil('\n');
    if (val != null) {
      val = val.trim();
      String[] partes = val.split(",");
      if (partes.length == 3) {
        for (int i = 0; i < 3; i++) {
          lectura[i] = int(partes[i]);
        }
      }
    }
  }

  // Dibujar los 3 sensores
  for (int i = 0; i < 3; i++) {

    //Color
    if (lectura[i] < cerca) {
      fill(255, 0, 0); // rojo
      reproducirSonido(i);
    } else if (lectura[i] < medio) {
      fill(255, 255, 0); // amarillo
    } else if (lectura[i] < lejos) {
      fill(0, 255, 0); // verde
    } else {
      fill(50); // gris
    }

    // Dibujar círculo
    ellipse(150 + i * 200, height/2, 150, 150);

    // Texto
    fill(255);
    textAlign(CENTER);
    text("Sensor " + (i+1) + ": " + lectura[i], 150 + i * 200, height - 30);
  }
}

void reproducirSonido(int sensor) {
  int idx = sonidoIndex[sensor];

  if (!sonidos[sensor][idx].isPlaying()) {
    sonidos[sensor][idx].play();
    sonidoIndex[sensor] = (idx + 1) % 26;
  }
}

Arduino:

// Definición de pines analógicos para los sensores
const int sensorPin1 = A0;
const int sensorPin2 = A1;
const int sensorPin3 = A2;


// Variable para almacenar la lectura del sensor (0-1023)
int valorSensor1 = 0;
int valorSensor2 = 0;
int valorSensor3 = 0;


// La velocidad de comunicación debe coincidir en Arduino y Processing
const long BAUD_RATE = 9600;


void setup() {
 // Inicia la comunicación serial
 Serial.begin(BAUD_RATE);
}


void loop() {
 // Lectura de los pines analógicos
 // Para un sensor ultrasónico (HC-SR04), usarías la función NewPing
 // para obtener la distancia en cm y enviar ese valor.
 // Aquí usamos analogRead como ejemplo general.
 valorSensor1 = analogRead(sensorPin1);
 valorSensor2 = analogRead(sensorPin2);
 valorSensor3 = analogRead(sensorPin3);


 // Mapeamos los valores si es necesario (ej: de 0-1023 a 0-255)
 // int distancia1 = map(valorSensor1, 0, 1023, 0, 255);
 // int distancia2 = map(valorSensor2, 0, 1023, 0, 255);
 // int distancia3 = map(valorSensor3, 0, 1023, 0, 255);


 // Enviamos los tres valores concatenados y separados por una coma,
 // y terminados con un salto de línea para que Processing sepa dónde
 // termina el mensaje.
 Serial.print(valorSensor1);
 Serial.print(",");
 Serial.print(valorSensor2);
 Serial.print(",");
 Serial.println(valorSensor3); // println añade el salto de línea


 // Pequeño retardo para no saturar el puerto serial
 delay(50);
}
```
<img src="https://github.com/paulibascunan/Interfaz-II/blob/44f937c00465b02a464e2f69fb2282ae14141be4/img/IMG_1303.jpg"/>
