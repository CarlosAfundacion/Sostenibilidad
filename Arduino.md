**Guía introductoria a Arduino**

**¿Qué es Arduino?**

Arduino es una plataforma de hardware y software de código abierto diseñada para crear proyectos electrónicos interactivos. Fue creada en Italia en 2005 con el objetivo de simplificar la programación y el diseño de circuitos, permitiendo que estudiantes, profesionales y entusiastas puedan desarrollar prototipos de manera rápida y sencilla.

El sistema se basa en placas de desarrollo que incluyen un microcontrolador, un pequeño ordenador que puede ser programado para controlar dispositivos electrónicos como luces, sensores, motores, pantallas y mucho más. Además, Arduino proporciona un entorno de desarrollo integrado (IDE) gratuito y fácil de usar para programar dichas placas.

**¿Por qué usar Arduino?**

Arduino es popular por varias razones:

- **Fácil de usar:** Su lenguaje de programación está basado en C/C++ pero adaptado para ser accesible.
- **Código abierto:** Tanto el hardware como el software son de código abierto, lo que fomenta una comunidad activa y recursos gratuitos.
- **Compatible con múltiples dispositivos:** Puede conectarse a sensores, actuadores y módulos externos.
- **Económico:** Las placas Arduino son relativamente baratas en comparación con otras plataformas similares.

**Principales componentes de Arduino**

1. **Microcontrolador:** Es el "cerebro" de la placa. Los modelos comunes incluyen el ATmega328 (en el Arduino Uno) y ATmega2560 (en el Arduino Mega).
2. **Puertos digitales y analógicos:** Se utilizan para conectar sensores y actuadores.
   - **Pines digitales:** Los pines digitales (etiquetados como D0-D13 en Arduino Uno) permiten enviar y recibir señales digitales (0 o 1). Algunos de ellos soportan señales PWM para controlar dispositivos como servomotores.
     - **Pines PWM:** Los pines PWM (Pulse Width Modulation) permiten generar señales analógicas simuladas a partir de pulsos digitales. Esto es útil para controlar la velocidad de motores o el brillo de LEDs. En Arduino Uno, los pines con función PWM son D3, D5, D6, D9, D10 y D11. La modulación se realiza variando la duración de los pulsos en un ciclo.
   - **Pines analógicos:** Los pines analógicos (A0-A5 en Arduino Uno) permiten leer valores de sensores que envían señales continuas, como un sensor de temperatura. Los valores se leen como un número entre 0 y 1023, correspondiente a un rango de voltajes entre 0 y 5V (o 3.3V en algunas placas).
3. **Conector USB:** Permite programar la placa desde el ordenador y también puede suministrar energía.
4. **Regulador de voltaje:** Controla el suministro eléctrico para evitar daños en los componentes.
5. **Botón de reinicio:** Permite reiniciar el programa cargado en la placa.
6. **Pin de alimentación:** Incluye pines para suministrar corriente (5V y 3.3V) y tierra (GND) a los componentes conectados. Estos pines son esenciales para alimentar componentes externos, como sensores y módulos, que requieren una fuente de energía estable. Además, los pines de alimentación permiten conectar la placa a fuentes de energía externas, como baterías o adaptadores de corriente, lo que hace posible su uso en proyectos portátiles o de mayor consumo energético.

**Principios básicos de electricidad y electrónica para usar Arduino**

Para trabajar con Arduino, es importante entender algunos conceptos básicos:

1. **Corriente eléctrica:** Es el flujo de electrones a través de un conductor. Se mide en amperios (A).
2. **Voltaje:** Es la diferencia de potencial eléctrico entre dos puntos. Se mide en voltios (V). Arduino generalmente trabaja con 5V o 3.3V.
3. **Resistencia:** Es la oposición al flujo de corriente en un circuito. Se mide en ohmios (Ω). Las resistencias son esenciales para proteger componentes como LEDs.
4. **Ley de Ohm:** Relaciona voltaje, corriente y resistencia: V = I * R.
5. **Circuitos en serie y paralelo:**
   - En serie: Los componentes están conectados uno tras otro. La corriente es la misma en todos los componentes.
   - En paralelo: Los componentes están conectados en ramas separadas. El voltaje es el mismo en todas las ramas.
6. **Polaridad:** Algunos componentes, como LEDs y motores, tienen polaridad, lo que significa que deben conectarse en una dirección específica.

**Principales placas de Arduino**

- **Arduino Uno:** Ideal para principiantes. Tiene 14 pines digitales y 6 analógicos.
- **Arduino Mega:** Diseñada para proyectos más complejos, con 54 pines digitales y 16 analógicos.
- **Arduino Nano:** Una versión compacta para proyectos con poco espacio.
- **Arduino Leonardo:** Integra funciones como un teclado o ratón USB.

**¿Cómo se programa Arduino?**

Arduino se programa mediante su propio IDE, donde los usuarios pueden escribir código y cargarlo a la placa. El proceso sigue estas etapas:

1. **Escritura del código:** Se utiliza el lenguaje de Arduino (basado en C++).
2. **Compilación:** El IDE traduce el código a instrucciones que la placa pueda entender.
3. **Carga:** El programa se transfiere a la placa mediante un cable USB.

El código de Arduino suele dividirse en dos partes:
- **Setup():** Configuración inicial, ejecutada una vez.
- **Loop():** Ciclo principal que se ejecuta continuamente.

**Guía básica de programación en Arduino**

Arduino utiliza un lenguaje basado en C/C++ con funciones y métodos propios. A continuación, se describen las principales instrucciones y métodos básicos:

- **pinMode(pin, mode):** Configura un pin como entrada (`INPUT`) o salida (`OUTPUT`). Por ejemplo: `pinMode(13, OUTPUT);`.
- **digitalWrite(pin, value):** Establece un pin digital en estado alto (`HIGH`) o bajo (`LOW`). Por ejemplo: `digitalWrite(13, HIGH);`.
- **digitalRead(pin):** Lee el estado de un pin digital (alto o bajo). Por ejemplo: `int estado = digitalRead(2);`.
- **analogWrite(pin, value):** Genera una señal PWM en un pin especificado. El valor puede ser entre 0 y 255. Por ejemplo: `analogWrite(9, 128);`.
- **analogRead(pin):** Lee un valor analógico de un pin (de 0 a 1023). Por ejemplo: `int lectura = analogRead(A0);`.
- **delay(ms):** Pausa la ejecución durante un tiempo en milisegundos. Por ejemplo: `delay(1000);` para 1 segundo.
- **Serial.begin(baudRate):** Inicializa la comunicación serie con un baud rate especificado. Por ejemplo: `Serial.begin(9600);`.
- **Serial.print(data):** Envía datos al puerto serie sin un salto de línea. Por ejemplo: `Serial.print("Hola");`.
- **Serial.println(data):** Envía datos al puerto serie con un salto de línea. Por ejemplo: `Serial.println("Hola");`.

**Ejemplo básico de código en Arduino**

Este ejemplo enciende y apaga un LED conectado al pin 13 de manera intermitente:

```cpp
void setup() {
  pinMode(13, OUTPUT); // Configura el pin 13 como salida
}

void loop() {
  digitalWrite(13, HIGH); // Enciende el LED
  delay(1000);            // Espera 1 segundo
  digitalWrite(13, LOW);  // Apaga el LED
  delay(1000);            // Espera 1 segundo
}
```

**Proyectos comunes con Arduino**

- **Sistemas de riego automático:** Utilizando sensores de humedad del suelo. https://www.youtube.com/watch?v=moa6d8DboCo&t=49s&pp=ygUNcmllZ28gYXJkdWlubw%3D%3D
- **Estaciones meteorológicas:** Que miden temperatura, humedad y presión. https://www.youtube.com/watch?v=ad_hl0WQV9U
- **Automatización del hogar:** Control de luces y electrodomésticos. https://www.youtube.com/watch?v=eq5TQwcBfqs
- **Robótica educativa:** Construcción de robots que pueden moverse y realizar tareas. https://www.youtube.com/watch?v=trD33kohPLM
- **Monitoreo de calidad del aire:** Uso de sensores para detectar contaminantes. https://www.youtube.com/shorts/ACwK1f5wV8Y




