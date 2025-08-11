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

##### ejercicio 4: led potenciómetro

```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
