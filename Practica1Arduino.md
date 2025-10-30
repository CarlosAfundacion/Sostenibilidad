

# Práctica: Sistema de control de ventilación inteligente

### Objetivo

Diseñar y programar un **sistema de ventilación inteligente** con Arduino que:

* Mida la **temperatura** y active un **ventilador (motor DC)** cuando se supere un umbral.
* Detecte la **distancia** con un sensor de ultrasonidos y encienda diferentes **LEDs** según la proximidad de un objeto.

Esta práctica integra **sensores analógicos y digitales**, control mediante **transistor NPN**, uso de **diodo de protección** y **estructuras condicionales** en el código.

---

##  Materiales necesarios (todos disponibles en Tinkercad)

| Componente                         | Cantidad | Descripción / Uso                          |
| ---------------------------------- | -------- | ------------------------------------------ |
| Arduino UNO                        | 1        | Placa controladora principal               |
| Sensor de temperatura **TMP36**    | 1        | Mide temperatura ambiente                  |
| Sensor de ultrasonidos **HC-SR04** | 1        | Mide distancia a un objeto                 |
| Transistor **BC547** (NPN)         | 1        | Activa el motor DC                         |
| Diodo **1N4007** (El que no es zener)                  | 1        | Protege el transistor del motor            |
| Motor DC                           | 1        | Simula el ventilador                       |
| LED rojo                           | 1        | Indica objeto cercano                      |
| LED verde                          | 1        | Indica objeto a distancia media            |
| Resistencias de 220 Ω              | 2        | Limitan corriente de los LEDs              |
| Resistencia de 1 kΩ                | 1        | Entre pin de Arduino y base del transistor |
| Resistencia de 10 kΩ               | 1        | Pull-down entre base y GND (opcional)      |
| Cables de conexión                 | —        | Para realizar el circuito                  |

---

##  Descripción del funcionamiento

###  1. Medición de distancia (HC-SR04)

* Si un objeto está a **menos de 10 cm**, se enciende el **LED rojo**.
* Si está entre **10 cm y 30 cm**, se enciende el **LED verde**.
* Si está a **más de 30 cm**, ambos LEDs permanecen **apagados**.
* Si no se obtiene medida válida, también se apagan ambos LEDs.

###  2. Control del motor según la temperatura (TMP36)

* Si la **temperatura supera los 31 °C**, el motor **se activa** (simulando un ventilador).
* Si la **temperatura baja de 29 °C**, el motor **se apaga**.

> *(Histeresis para evitar que el motor se encienda y apague continuamente cerca del umbral).*

---

##  Esquema de conexiones (Tinkercad)

###  Sensor de ultrasonidos (HC-SR04)

| Pin HC-SR04 | Arduino |
| ----------- | ------- |
| VCC         | 5V      |
| GND         | GND     |
| TRIG        | D9      |
| ECHO        | D10     |

---

###  Sensor de temperatura (TMP36)

| Pin TMP36 | Arduino |
| --------- | ------- |
| VCC       | 5V      |
| GND       | GND     |
| Vout      | A0      |

---

###  LEDs

| Color | Arduino | Resistencia | Conexión |
| ----- | ------- | ----------- | -------- |
| Rojo  | D5      | 220 Ω       | A GND    |
| Verde | D6      | 220 Ω       | A GND    |

---

###  Motor DC con transistor BC547 y diodo 1N4007

| Elemento          | Conexión                                                         |
| ----------------- | ---------------------------------------------------------------- |
| Motor (+)         | 5V                                                               |
| Motor (–)         | Colector (pin 1 del BC547)                                       |
| Emisor (pin 3)    | GND                                                              |
| Base (pin 2)      | D3 de Arduino mediante resistencia de 1 kΩ                       |
| Diodo 1N4007      | En paralelo con el motor: cátodo (raya) a +5V, ánodo al colector |
| Resistencia 10 kΩ | Entre base y GND (opcional, pull-down)                           |

>  *En Tinkercad, el motor se alimenta directamente del pin de 5 V del Arduino. En un montaje real debería usar fuente externa con masa común.*

---

##  Pseudocódigo de referencia

```
LEER temperatura (TMP36)
LEER distancia (HC-SR04)

SI distancia < 10 → LED rojo ON, LED verde OFF
SI distancia entre 10 y 30 → LED verde ON, LED rojo OFF
SI distancia > 30 → ambos OFF

SI temperatura > 31 °C → motor ON
SI temperatura < 29 °C → motor OFF
```

---

##  Requisitos del programa Arduino

1. Leer el sensor TMP36 (entrada analógica A0).
2. Calcular la temperatura en °C.
3. Leer la distancia con el HC-SR04 usando `pulseIn()`.
4. Controlar los LEDs según los rangos definidos.
5. Activar o desactivar el motor con histeresis térmica.
6. Mostrar por el **Monitor Serie** los valores de temperatura, distancia y estado del motor.
7. Código limpio, indentado y comentado.

---

##  Criterios de evaluación 

| Criterio                               | Puntuación | Descripción                                                 |
| -------------------------------------- | ---------- | ----------------------------------------------------------- |
| Funcionamiento correcto                | 5 pts      | El sistema responde correctamente a temperatura y distancia |
| Cableado en Tinkercad                  | 2 pts      | Conexiones correctas, limpias y sin errores                 |
| Código estructurado y comentado        | 2 pts      | Uso correcto de variables, funciones y comentarios          |
| Lecturas estables y salida serie clara | 1 pt       | Datos coherentes en el monitor serie                        |

---

