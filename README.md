Este código está diseñado para el control de un sistema automatizado que incluye sensores, pulsadores, displays y un motor. Fue desarrollado utilizando el microcontrolador PIC16F877 y está orientado a la gestión de temperaturas y almacenamiento de mediciones en la memoria EEPROM. El sistema cuenta con un control basado en los valores de temperatura y puede ajustar parámetros según el tipo de cultivo seleccionado (Frutilla, Tomate o Lechuga).

Características Principales
Sensores y ADC (Conversión Analógica-Digital):

El programa utiliza el módulo ADC del PIC para leer valores de temperatura desde un sensor conectado al canal analógico del microcontrolador.
El valor leído se convierte en un rango de temperatura y se almacena para la lógica del sistema.
Memoria EEPROM:

Las mediciones de temperatura se dividen en dos partes (entera y decimal) y se almacenan en la EEPROM.
El sistema utiliza un esquema de memoria circular donde las nuevas grabaciones sobrescriben las más antiguas cuando se alcanza el límite de memoria.
Control de Motor:

Dependiendo de los valores de temperatura, se controla un motor mediante los pines definidos.
Dirección del Motor: Controlada por el pin direccion.
Habilitación del Motor: Controlada por el pin habilitacion.
Pulsos del Motor: Generados por el pin pulso.
Control de Cooler:

El cooler se activa si la temperatura excede un límite máximo (maxima) y se desactiva cuando la temperatura cae por debajo del límite intermedio (intermedia).
Interacción del Usuario:

Pulsador mem: Graba la medición actual de temperatura en la EEPROM.
Pulsador read: Permite al usuario leer mediciones almacenadas en la EEPROM.
Pulsador mas: Navega entre las posiciones de memoria almacenadas para su lectura.
Interfaz de selección de cultivo: El usuario puede seleccionar entre Frutilla, Tomate o Lechuga, lo que ajusta los parámetros de temperatura máximos, mínimos e intermedios.
Pantalla LCD:

Visualiza la temperatura actual, las mediciones almacenadas y mensajes informativos al usuario.
Lógica de Temperatura:

Máxima: Activa el cooler para enfriar el sistema.
Intermedia: Ajusta el motor para abrir o cerrar pasos según corresponda.
Mínima: Si la temperatura cae por debajo de este límite, el motor cierra completamente los pasos y el cooler se desactiva.
Flujo del Programa
Inicialización:

Configura los puertos de entrada/salida.
Inicializa el módulo ADC y configura los canales analógicos.
Habilita las interrupciones globales y las del ADC.
Ciclo Principal (while(1)):

Grabación en EEPROM:
Cuando se presiona el pulsador mem, el programa almacena la temperatura actual en la EEPROM dividiéndola en partes entera y decimal.
Lectura de EEPROM:
Con el pulsador read, se leen y muestran en el LCD los valores almacenados en la EEPROM.
El pulsador mas permite navegar entre las posiciones de memoria.
Control de Cultivos:
El usuario selecciona el cultivo deseado, lo que ajusta los límites de temperatura (máxima, mínima e intermedia).
Control del Motor:
Dependiendo de la temperatura actual, el motor abre o cierra pasos para regular el sistema.
Control del Cooler:
Activa o desactiva el cooler según los límites de temperatura.
