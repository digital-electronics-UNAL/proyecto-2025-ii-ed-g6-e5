[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21858621&assignment_repo_type=AssignmentRepo)
# Pastillero Inteligente: Sistema Automatizado de Gestión y Dispensación de Medicamentos

**Gabriela Cangrejo, Juan Elvira, Sebastián García**  
Ingeniería Eléctrica y Electrónica  
Universidad Nacional de Colombia  
ancaicedo@unal.edu.co, jelvira@unal.edu.co, sebgarciam@unal.edu.co  

---

## Resumen

Este documento presenta el desarrollo del pastillero inteligente basado en FPGA, donde se implementa un sistema de control automático y alarmas para el consumo de los medicamentos, buscando resolver un problema en el consumo adecuado de los mismos. Se describe la arquitectura del sistema, los materiales utilizados, las pruebas realizadas, el uso de herramientas de inteligencia artificial, así como los resultados obtenidos.

**Palabras clave:** FPGA, VHDL, Servo Motor, Buzzer, LCD, Automatización.

---

## I. Introducción

El manejo correcto de medicamentos es un desafío diario para muchas personas. Cuando los tratamientos requieren tomar varias pastillas a diferentes horas, es común que se presenten confusiones y olvidos. Estos errores pueden reducir la efectividad del tratamiento e incluso producir complicaciones de salud.

Las soluciones existentes, como pastilleros tradicionales o alarmas de celular, resultan insuficientes, ya que no verifican si la dosis se tomó ni previenen la ingesta equivocada, además de que pueden ser fácilmente perdidas en el afán del día a día.

Este proyecto propone un pastillero inteligente que funciona como un asistente confiable. El dispositivo guía al usuario en todo el proceso: indica qué medicamento tomar, entrega la dosis adecuada mediante un sistema automatizado y registra cada toma confirmada por el usuario.

El uso de una FPGA Cyclone IV garantiza precisión en el control, sincronización de eventos y respuesta en tiempo real, asegurando un funcionamiento confiable y robusto.

---

## II. Arquitectura Implementada

El sistema está compuesto por una FPGA Cyclone IV EP4CE10E22C8N, una pantalla LCD, un servomotor, un buzzer, un botón de control y varios LEDs.

### II-A. Resumen de los Componentes de Hardware

| Concepto            | Cantidad | Valor ($) |
|---------------------|----------|-----------|
| FPGA Cyclone IV     | 1        | Prestada  |
| RTC DS1307          | 1        | 4.622     |
| LED Rojo            | 7        | 420       |
| LCD 16x2            | 1        | 15.000    |
| Resistencias        | 7        | 100       |
| Baquela             | 1        | 3.500     |
| Batería de reloj    | 1        | 2.000     |
| Caja                | 1        | —         |
| **Total a pagar**   |          | **28.762**|

**Cuadro I.** Resumen de la compra.

---

### II-B. Componentes de Software

- Lenguaje: **VHDL**
- **Visual Studio Code**
- **Quartus Prime**

---

### II-C. Funcionamiento General

Cuando el sistema alcanza la hora programada, se activa el buzzer, el LED correspondiente y se muestra el evento en la pantalla LCD, indicando la hora, el día y el medicamento programado para la toma. Al presionar el botón, el buzzer se desactiva.

---

### II-D. Presentación Física del Proyecto

El sistema se encuentra montado sobre una baquela con sus componentes soldados y conectados directamente a la FPGA. Todos los dispositivos están integrados y conectados a los compartimentos del pastillero, los cuales son iluminados mediante su respectivo LED.

**Figura 1.** Prototipo en protoboard del sistema  
**Figura 2.** Prototipo en protoboard del sistema

---

### II-E. Diagrama de Flujo

**Figura 3.** Diagrama de flujo del sistema.

---

### II-F. Diagrama de Bloques

**Figura 4.** Diagrama de bloques del sistema.

---

## III. Pruebas

Se realizaron diferentes pruebas para verificar el correcto funcionamiento del sistema.

### III-A. Tipos de Pruebas

- Prueba de encendido del sistema  
- Prueba de activación del buzzer  
- Prueba de giro del servomotor  
- Prueba de visualización en la LCD  
- Prueba del botón de apagado  

---

### III-B. Descripción de las Pruebas

- **Prueba de encendido del sistema:**  
  Se verifica que al energizar el sistema la FPGA inicialice correctamente, la LCD se encienda sin mostrar información y que el buzzer y los LEDs permanezcan apagados.

- **Prueba de activación del buzzer:**  
  Se comprueba que el buzzer se active correctamente generando una señal audible continua.

- **Prueba de encendido de LEDs:**  
  Se evalúa que el LED correspondiente a la alarma se encienda y apague en función del botón.

- **Prueba de visualización en la LCD:**  
  Se valida que la pantalla LCD muestre correctamente los mensajes de estado del sistema, como la hora actual, activación de alarma, día y medicamento a tomar.

- **Prueba del botón de apagado:**  
  Se verifica que al presionar el botón de apagado el buzzer se desactive inmediatamente.

---

### III-C. Resultados

Se logró implementar exitosamente el RTC para configurar las alarmas con las horas programadas. La alarma activa tanto el buzzer como el LED correspondiente al día asignado en el pastillero. Además, se consiguió mostrar en la pantalla LCD la información esperada, superando las pruebas propuestas y garantizando el funcionamiento del sistema.

---

## IV. Uso de Inteligencia Artificial

Durante el desarrollo del proyecto se utilizaron herramientas de inteligencia artificial como **ChatGPT**, **DeepSeek** y **Gemini** para los siguientes aspectos:

- Generación y corrección de código en Quartus (ChatGPT y DeepSeek)
- Redacción del informe (Gemini)

---

## V. Complicaciones

Durante el desarrollo del proyecto se presentaron diversas dificultades técnicas que afectaron su correcto funcionamiento. La principal complicación estuvo relacionada con el código implementado en la FPGA, ya que fue necesario atravesar múltiples errores y correcciones para lograr la integración de las diferentes partes del sistema.

Asimismo, se presentaron errores constantes durante la simulación en el entorno de desarrollo, problemas de compatibilidad entre módulos, errores de temporización y dificultades en la integración total del proyecto dentro de un único diseño funcional.

El problema más significativo que no se logró resolver fue la velocidad con la que la LCD reiniciaba el proceso de impresión de la información, debido a la alta frecuencia del sistema, lo que dificultaba la lectura del contenido mostrado.

Debido a estas complicaciones, se decidió eliminar el servomotor y reemplazarlo por un sistema de LEDs, priorizando la funcionalidad y manufactura del producto final.

**Figura 5.** Visualización y conteo regresivo.

---

## VI. Conclusiones

El desarrollo del pastillero inteligente permitió demostrar la capacidad de los sistemas digitales para resolver problemas reales relacionados con el manejo adecuado de medicamentos. La arquitectura implementada integró de manera efectiva módulos de tiempo real, alarmas visuales y auditivas, y una interfaz de usuario básica mediante LCD y botones, logrando un prototipo funcional capaz de guiar al usuario durante el proceso de toma de medicamentos.

El uso del RTC DS1307 y su correcta comunicación con la FPGA evidenció la importancia del manejo del tiempo en aplicaciones críticas. Aunque el diseño se vio afectado por dificultades en la simulación, integración de módulos, errores de temporización y problemas en la actualización de la LCD, estas complicaciones permitieron adquirir una comprensión más profunda del flujo de diseño digital y la importancia de la verificación.

La decisión de reemplazar el servomotor por un sistema de LEDs demostró la capacidad del equipo para adaptarse a las limitaciones técnicas y priorizar la funcionalidad del prototipo final.

Finalmente, el proyecto evidenció el valor de las herramientas de inteligencia artificial como apoyo en la depuración de código, documentación y optimización de tareas. En general, aunque el prototipo no alcanzó todas las funcionalidades inicialmente planteadas, cumplió su objetivo principal: apoyar la toma segura y guiada de medicamentos y sentar las bases para futuras mejoras.

---

## Referencias

1. Intel Corporation, *Cyclone IV Device Handbook*.  
2. S. Brown y Z. Vranesic, *Fundamentals of Digital Logic with VHDL Design*.  
3. OpenAI, *ChatGPT*. Disponible en: https://chat.openai.com

