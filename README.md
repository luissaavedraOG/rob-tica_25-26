# Robótica 2025/202
Este es cuaderno de robótica de 4 ESO, curso 2025-2026


## Proyecto 1: Arduino doble intermitente

### -Placa arduino y protoboard:

<img scr="imagenes_rob/2.-Internitente.png" width="500" height="300" />
He utilizado lo puertos 11 y 10, el 11 para el rojo y el 10 para el azul, los dos estan conectados al GND para proporcioar corriente. El GND se conecta al ánodo del LED y el cátodo a los pines 11 y 10 (el rojo al 11 y el azul al 10), poniendo delante de los LED unas resistencias de 220 omios

### -Codigo:

```
/*
  Luis javier Saavedra Guerrero
  
*/


#define terminal12 12 // Al terminal 12 lo llamamos terminal12
#define terminal13 13 // Al terminal 13 lo llamamos terminal13

// En el setup establecemos los parámetros iniciales.
void setup() {
  // Los terminales pueden ser de entrada INPUT o de salidas OUTPUT
  // En este caso serán de salidas.
  // Fíjate que las líneas terminan en punto y coma;
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
}

int retardo=60;

// Esto es un loop, un lazo o bucle.
// Lo que hay dentro de loop ser repite continuamente, es decir hace las líneas de su interior y
// luego vuelve a realizarlas.
void loop() {
  digitalWrite(10, HIGH);   // El terminal12 en ALTO, es decir a 5 V
  digitalWrite(11, LOW);    // El terminal13 en BAJO, es decir a 0 V
  Serial.println("Parpadeo");
  delay(retardo);              // Retardo
  digitalWrite(10, LOW);    // El terminal12 en BAJO, es decir a 0 V
  digitalWrite(11, HIGH);   // El terminal13 en ALTO, es decir a 5 V
  Serial.println("Intermitente");
  delay(retardo);              // Retardo
}
```

## Proyecto 2: Pulsador

Al pulsar el pulsador, un led que siempre estara encendido se apagara y el otro que siempre esta pagado se encendera

### -Placa arduino y protoboard:

<p align="center">
<img src="imagenes_rob/3.-Pulsador.png" width="1000" height="700" />
</p>

### -Codigo:


```
/*
  Luis javier Saavedra Guerrero
  
*/

// Entrada y Salida.
// Al pulsar el pulsador se enciende el LED, al dejar de pulsarlo, se apaga.

#define pin2 2   // Al terminal  2 lo llamamos pin2. Aquí irá el pulsador.
#define pin13 13 // Al terminal 13 lo llamamos pin13. Aquí irá el LED.
#define pin12 12
int valor2; // Esto es una variable entera



// En el setup establecemos los parámetros iniciales.
void setup() {
  pinMode(pin2, INPUT);     // El pin2 será entrada. Pulsador.
  pinMode(pin13, OUTPUT);   // El pin13 será salida. LED.
  pinMode(pin12, OUTPUT);
  Serial.begin(9600);        // Para ver información en el Seria Monitor.
}


void loop() {
  valor2 = digitalRead(pin2); // Lee el valor del pin2 y se lo asigna a valor2. (Puede ser 0 o 1)
if (valor2 == HIGH) { 
    digitalWrite(pin13, HIGH); // Si valor2 es ALTO, pone el pin13 en ALTO
    digitalWrite(pin12, LOW);
    Serial.println("Pulsado");
} 

if (valor2 == LOW) { 
    digitalWrite(pin13, LOW); // Si valor2 es BAJO, pone el pin13 en BAJO
    digitalWrite(pin12, HIGH);
    Serial.println("No Pulsado");
} 
}

```
