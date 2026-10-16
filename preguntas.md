# Teoría

## ¿Qué principio explica por qué la memoria caché incrementa significativamente el rendimiento del procesador en la jerarquía de almacenamiento?

+ a. La anticipación de páginas, cargando preventivamente el segmento de datos completo desde el disco hacia la memoria principal en cada salto de función.

+ b. La localidad temporal y espacial, reteniendo en memoria estática rápida los datos e instrucciones accedidos recientemente o ubicados en posiciones contiguas.

+ c. La coherencia de escritura, actualizando simultáneamente todos los niveles de almacenamiento secundario cada vez que se modifica una variable en memoria.

+ d. La sincronización de buses, igualando la frecuencia del reloj de la memoria dinámica principal con la velocidad de ejecución de las instrucciones de la CPU.

### Retroalimentación
La eficacia de la memoria caché se fundamenta en el Principio de Localidad: localidad temporal (reutilización próxima de datos recientemente accedidos) y espacial (acceso a posiciones de memoria contiguas), lo que permite servir la gran mayoría de accesos desde memorias SRAM de muy baja latencia (Silberschatz Cap. 1.4; U1 Slides 4-5).

La respuesta correcta es: La localidad temporal y espacial, reteniendo en memoria estática rápida los datos e instrucciones accedidos recientemente o ubicados en posiciones contiguas.

## ¿Cómo opera el mecanismo de Registros Base y Límite implementado en hardware para proteger la memoria de un proceso en Modo Usuario?

+ a. La MMU verifica que la dirección lógica sea menor que el registro límite y luego le suma el registro base para obtener la dirección física en memoria.

+ b. La MMU verifica que la dirección lógica coincida con el registro base, delegando la validación del límite al software del sistema operativo en el kernel.

+ c. La MMU compara la dirección física resultante contra el registro límite, permitiendo el acceso solo si la dirección supera la suma de base y de límite.

+ d. La MMU comprueba que la dirección física sea menor que el registro base, y si es válida le resta el registro límite para acceder a la memoria física.

### Retroalimentación
La MMU comprueba primero por hardware que la dirección lógica generada por el proceso sea menor que el valor del registro límite (0 <= dir < límite). Si es válida, le suma el registro base para calcular la dirección física en memoria RAM; si no lo es, dispara una excepción de protección al kernel (Silberschatz Cap. 1.5; U1 Slides 6-7).
La respuesta correcta es: La MMU verifica que la dirección lógica sea menor que el registro límite y luego le suma el registro base para obtener la dirección física en memoria.

## ¿Cuál es la función específica del Planificador a Largo Plazo (o de admisión) en un sistema operativo multiprogramado?

+ a. Manejar las interrupciones de los dispositivos de E/S para mover los procesos desde la cola de bloqueados hacia la cola de listos.

+ b. Controlar el grado de multiprogramación decidiendo qué programas del almacenamiento masivo son admitidos a la memoria RAM como procesos activos.

+ c. Gestionar la transferencia de páginas entre la memoria RAM y el área de swap para equilibrar el conjunto de trabajo de los procesos.

+ d. Seleccionar en intervalos de milisegundos cuál de los procesos en memoria RAM recibirá el siguiente turno de ejecución en el procesador.

**Retroalimentación**
El planificador a largo plazo (de admisión) regula el grado de multiprogramación determinando cuántos y cuáles trabajos en cola de almacenamiento pasan a memoria principal como procesos activos. El de medio plazo gestiona el swapping y el de corto plazo asigna la CPU frecuentemente (Silberschatz Cap. 3.2; U4 Slide 13).
La respuesta correcta es: Controlar el grado de multiprogramación decidiendo qué programas del almacenamiento masivo son admitidos a la memoria RAM como procesos activos.

Pregunta 4IncorrectaSe puntúa 0,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
¿Qué representa el Bloque de Control de Proceso (PCB) y por qué el Cambio de Contexto se considera una sobrecarga del sistema?

Seleccione una:

a.
Representa la estructura del kernel con el estado del proceso; es sobrecarga porque la CPU guarda y restaura registros sin realizar cómputo del usuario.

b.
Representa el marco de activación en la pila del hilo; es sobrecarga porque obliga a reescribir los punteros de los archivos abiertos por el proceso.
Incorrecta
Incorrecto. Confunde el PCB con el stack frame de la pila de usuario; además los descriptores de archivos permanecen en las tablas del kernel sin reescribirse.

c.
Representa el espacio de direcciones virtuales del proceso; es sobrecarga porque obliga a reasignar las páginas físicas de memoria en cada conmutación.

d.
Representa el nodo de la cola de listos en el planificador; es sobrecarga porque exige recalcular las prioridades de todos los procesos en espera.
Retroalimentación
El PCB almacena el contexto completo del proceso (PID, PC, registros, punteros a memoria, descriptores de archivos). El cambio de contexto guarda el estado del proceso saliente y recupera el del entrante; es sobrecarga pura (overhead) porque el procesador invierte ciclos en gestión interna sin realizar trabajo útil para las aplicaciones (Silberschatz Cap. 3.1-3.2; U4 Slides 5-6).

La respuesta correcta es: Representa la estructura del kernel con el estado del proceso; es sobrecarga porque la CPU guarda y restaura registros sin realizar cómputo del usuario.
Pregunta 5CorrectaSe puntúa 1,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
¿En qué condición específica el planificador SRT (Shortest Remaining Time First) desaloja de la CPU al proceso que se encuentra en ejecución?

Seleccione una:

a.
Cuando el proceso en ejecución realiza una llamada al sistema solicitando una operación de entrada/salida sobre un periférico.

b.
Cuando expira la cuota periódica de tiempo fijada por el temporizador del kernel para garantizar equidad en la cola de listos.

c.
Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.
Correcta
¡Correcto! En SRT el desalojo ocurre si la próxima ráfaga del recién llegado es estrictamente menor que el tiempo de CPU que le resta al proceso actual.

d.
Cuando el proceso en ejecución incrementa su consumo de memoria RAM superando el límite asignado en su bloque de control de proceso.
Retroalimentación
En SRT (versión apropiativa de SJF), la decisión de desalojo ocurre al arribar un nuevo proceso: si la ráfaga de CPU del recién llegado es estrictamente menor que el tiempo remanente que le resta al proceso actualmente en ejecución, este es desalojado y devuelto a la cola de listos (Silberschatz Cap. 5.3.2; Clase 4 Diap. 11).

La respuesta correcta es: Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.
Pregunta 6CorrectaSe puntúa 1,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
¿De qué manera el algoritmo HRRN (Highest Response Ratio Next) equilibra la atención de procesos cortos frente a procesos con largas esperas?

Seleccione una:

a.
Conmuta de forma preventiva la CPU cada vez que un proceso en espera acumula un tiempo en la cola de listos superior a su propia ráfaga.

b.
Divide la cola de listos en niveles con quantums crecientes, descendiendo a los procesos intensivos hacia colas de menor prioridad.

c.
Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.
Correcta
¡Correcto! En R = (w + s)/s = 1 + w/s, un s pequeño genera ratios altos, pero un w creciente eleva el ratio de tareas largas impidiendo su inanición.

d.
Asigna el procesador al proceso que tenga la menor relación entre el tiempo consumido de CPU y el tiempo restante estimado de ejecución.
Retroalimentación
En HRRN, la tasa de respuesta es R = (w + s) / s = 1 + w/s (donde w es tiempo de espera y s es tiempo de servicio). Al seleccionar el mayor R, prioriza procesos cortos (s pequeño) pero a su vez incrementa el ratio de procesos largos conforme aumenta su tiempo de espera w, evitando la inanición (Stallings Cap. 9.2; Clase 4 Diap. 12).

La respuesta correcta es: Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.
Pregunta 7CorrectaSe puntúa 1,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
¿Qué conjunto de condiciones debe cumplirse simultáneamente para que pueda originarse un interbloqueo (Deadlock) en un sistema operativo?

Seleccione una:

a.
Que los procesos compartan el mismo espacio de direcciones y se sincronicen exclusivamente mediante variables atómicas en memoria.

b.
Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.
Correcta
¡Correcto! Las cuatro condiciones de Coffman (exclusión mutua, retención y espera, no apropiación y espera circular) deben cumplirse a la vez.

c.
Que el sistema operativo utilice una política de planificación apropiativa que desaloje recursos en función de prioridades dinámicas.

d.
Que la memoria principal se encuentre saturada de procesos en estado suspendido que compiten por espacio en el área de intercambio.
Retroalimentación
Coffman (1971) demostró que para que ocurra un interbloqueo deben cumplirse simultáneamente cuatro condiciones: 1) Exclusión mutua, 2) Retención y espera (Hold & Wait), 3) No apropiación (No preemption), y 4) Espera circular. Si se invalida al menos una, el interbloqueo no puede producirse (Silberschatz Cap. 7.1; Diapositivas 4-5).

La respuesta correcta es: Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.
Pregunta 8IncorrectaSe puntúa 0,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
En un Grafo de Asignación de Recursos (RAG), ¿en qué circunstancia la presencia de un ciclo dirigido NO implica necesariamente un interbloqueo?

Seleccione una:

a.
Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.

b.
Cuando el sistema operativo cuenta con un temporizador de hardware que interrumpe periódicamente a los procesos involucrados en el ciclo.
Incorrecta
Incorrecto. Un temporizador solo conmuta la CPU, pero no libera los recursos no apropiativos retenidos por los procesos que forman el ciclo.

c.
Cuando los procesos que forman parte del ciclo se encuentran ejecutando en hilos de usuario sin intervención del despachador del kernel.

d.
Cuando los recursos implicados en el ciclo son de acceso exclusivo y ningún proceso puede retener más de una instancia simultáneamente.
Retroalimentación
Si los recursos tienen instancias únicas, un ciclo es condición necesaria y suficiente de interbloqueo. Pero si hay tipos de recursos con múltiples instancias, un ciclo es condición necesaria pero NO suficiente: un proceso externo al ciclo puede terminar su ejecución y liberar instancias del recurso compartido, rompiendo la espera circular (Silberschatz Cap. 7.2; Diapositivas 8-10).

La respuesta correcta es: Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.
Pregunta 9IncorrectaSe puntúa 0,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
En el problema de la Cena de los Filósofos, ¿cuál de las siguientes estrategias evita específicamente el interbloqueo rompiendo la condición de espera circular?

Seleccione una:

a.
Permitir que un filósofo tome sus palillos únicamente si ambos se encuentran libres simultáneamente en la mesa en ese momento.

b.
Limitar a cuatro el número máximo de filósofos sentados simultáneamente en la mesa mediante el uso de un semáforo contador de control.

c.
Expropiar el palillo asignado a un filósofo si este permanece esperando por el segundo palillo durante más de un intervalo de tiempo fijo.
Incorrecta
Incorrecto. Desalojar un palillo retenido tras un timeout ataca la condición de No Apropiación (No preemption), no la de Espera Circular.

d.
Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.
Retroalimentación
Hacer que al menos un filósofo tome primero su palillo derecho y luego el izquierdo mientras los otros toman primero el izquierdo y luego el derecho rompe la simetría y elimina matemáticamente la posibilidad de que se forme una cadena de espera circular (la 4ta condición de Coffman). Las otras estrategias también pueden evitar el interbloqueo, pero lo hacen atacando otras condiciones o restringiendo la concurrencia: exigir ambos palillos simultáneamente elimina retención y espera; limitar a cuatro filósofos evita que todos retengan un palillo al mismo tiempo; y expropiar un palillo modifica la condición de no apropiación (Silberschatz Cap. 6.6; Diapositivas U5).

La respuesta correcta es: Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.
Pregunta 10CorrectaSe puntúa 1,00 sobre 1,00No marcadasMarcar pregunta
Enunciado de la pregunta
¿Qué caracteriza formalmente a una Condición de Carrera (Race Condition) en un entorno de programación concurrente?

Seleccione una:

a.
Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.
Correcta
¡Correcto! Ocurre cuando el resultado de manipular datos compartidos depende del orden no determinista en que se intercalan las instrucciones.

b.
Dos procesos intentan reservar espacio en el heap simultáneamente, provocando fragmentación externa en la memoria principal.

c.
Un hilo de alta prioridad desaloja repetidamente a un hilo de baja prioridad, impidiendo que este último avance en la cola de listos.

d.
Múltiples procesos compiten por el ancho de banda del bus de memoria, degradando el rendimiento general de las operaciones de lectura.
Retroalimentación
Una condición de carrera (race condition) se produce cuando varios procesos o hilos manipulan los mismos datos compartidos de forma concurrente y el resultado de la operación depende del orden no determinista en el que se intercalan sus instrucciones (Silberschatz Cap. 6.1; Diapositivas U5).

La respuesta correcta es: Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.

¿En qué condición específica el planificador SRT (Shortest Remaining Time First) desaloja de la CPU al proceso que se encuentra en ejecución?
a. Cuando el proceso en ejecución realiza una llamada al sistema solicitando una operación de entrada/salida sobre un periférico.

b. Cuando expira la cuota periódica de tiempo fijada por el temporizador del kernel para garantizar equidad en la cola de listos.

c. Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.

d. Cuando el proceso en ejecución incrementa su consumo de memoria RAM superando el límite asignado en su bloque de control de proceso.

Retroalimentación
En SRT (versión apropiativa de SJF), la decisión de desalojo ocurre al arribar un nuevo proceso: si la ráfaga de CPU del recién llegado es estrictamente menor que el tiempo remanente que le resta al proceso actualmente en ejecución, este es desalojado y devuelto a la cola de listos (Silberschatz Cap. 5.3.2; Clase 4 Diap. 11).

La respuesta correcta es: Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.

¿De qué manera el algoritmo HRRN (Highest Response Ratio Next) equilibra la atención de procesos cortos frente a procesos con largas esperas?
a. Conmuta de forma preventiva la CPU cada vez que un proceso en espera acumula un tiempo en la cola de listos superior a su propia ráfaga.

b. Divide la cola de listos en niveles con quantums crecientes, descendiendo a los procesos intensivos hacia colas de menor prioridad.

c. Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.

d. Asigna el procesador al proceso que tenga la menor relación entre el tiempo consumido de CPU y el tiempo restante estimado de ejecución.

Retroalimentación
En HRRN, la tasa de respuesta es R = (w + s) / s = 1 + w/s (donde w es tiempo de espera y s es tiempo de servicio). Al seleccionar el mayor R, prioriza procesos cortos (s pequeño) pero a su vez incrementa el ratio de procesos largos conforme aumenta su tiempo de espera w, evitando la inanición (Stallings Cap. 9.2; Clase 4 Diap. 12).

La respuesta correcta es: Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.

¿Qué conjunto de condiciones debe cumplirse simultáneamente para que pueda originarse un interbloqueo (Deadlock) en un sistema operativo?
a. Que los procesos compartan el mismo espacio de direcciones y se sincronicen exclusivamente mediante variables atómicas en memoria.

b. Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.

c. Que el sistema operativo utilice una política de planificación apropiativa que desaloje recursos en función de prioridades dinámicas.

d. Que la memoria principal se encuentre saturada de procesos en estado suspendido que compiten por espacio en el área de intercambio.

Retroalimentación
Coffman (1971) demostró que para que ocurra un interbloqueo deben cumplirse simultáneamente cuatro condiciones: 1) Exclusión mutua, 2) Retención y espera (Hold & Wait), 3) No apropiación (No preemption), y 4) Espera circular. Si se invalida al menos una, el interbloqueo no puede producirse (Silberschatz Cap. 7.1; Diapositivas 4-5).

La respuesta correcta es: Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.

En un Grafo de Asignación de Recursos (RAG), ¿en qué circunstancia la presencia de un ciclo dirigido NO implica necesariamente un interbloqueo?
a. Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.

b. Cuando el sistema operativo cuenta con un temporizador de hardware que interrumpe periódicamente a los procesos involucrados en el ciclo.

c. Cuando los procesos que forman parte del ciclo se encuentran ejecutando en hilos de usuario sin intervención del despachador del kernel.

d. Cuando los recursos implicados en el ciclo son de acceso exclusivo y ningún proceso puede retener más de una instancia simultáneamente.

Retroalimentación
Si los recursos tienen instancias únicas, un ciclo es condición necesaria y suficiente de interbloqueo. Pero si hay tipos de recursos con múltiples instancias, un ciclo es condición necesaria pero NO suficiente: un proceso externo al ciclo puede terminar su ejecución y liberar instancias del recurso compartido, rompiendo la espera circular (Silberschatz Cap. 7.2; Diapositivas 8-10).

La respuesta correcta es: Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.

En el problema de la Cena de los Filósofos, ¿cuál de las siguientes estrategias evita específicamente el interbloqueo rompiendo la condición de espera circular?
a. Permitir que un filósofo tome sus palillos únicamente si ambos se encuentran libres simultáneamente en la mesa en ese momento.

b. Limitar a cuatro el número máximo de filósofos sentados simultáneamente en la mesa mediante el uso de un semáforo contador de control.

c. Expropiar el palillo asignado a un filósofo si este permanece esperando por el segundo palillo durante más de un intervalo de tiempo fijo.

d. Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.

Retroalimentación
Hacer que al menos un filósofo tome primero su palillo derecho y luego el izquierdo mientras los otros toman primero el izquierdo y luego el derecho rompe la simetría y elimina matemáticamente la posibilidad de que se forme una cadena de espera circular (la 4ta condición de Coffman). Las otras estrategias también pueden evitar el interbloqueo, pero lo hacen atacando otras condiciones o restringiendo la concurrencia: exigir ambos palillos simultáneamente elimina retención y espera; limitar a cuatro filósofos evita que todos retengan un palillo al mismo tiempo; y expropiar un palillo modifica la condición de no apropiación (Silberschatz Cap. 6.6; Diapositivas U5).

La respuesta correcta es: Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.

¿Qué caracteriza formalmente a una Condición de Carrera (Race Condition) en un entorno de programación concurrente?
a. Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.

b. Dos procesos intentan reservar espacio en el heap simultáneamente, provocando fragmentación externa en la memoria principal.

c. Un hilo de alta prioridad desaloja repetidamente a un hilo de baja prioridad, impidiendo que este último avance en la cola de listos.

d. Múltiples procesos compiten por el ancho de banda del bus de memoria, degradando el rendimiento general de las operaciones de lectura.

Retroalimentación
Una condición de carrera (race condition) se produce cuando varios procesos o hilos manipulan los mismos datos compartidos de forma concurrente y el resultado de la operación depende del orden no determinista en el que se intercalan sus instrucciones (Silberschatz Cap. 6.1; Diapositivas U5).

La respuesta correcta es: Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.

## ¿En qué condición específica el planificador SRT (Shortest Remaining Time First) desaloja de la CPU al proceso que se encuentra en ejecución?

+ a. Cuando el proceso en ejecución realiza una llamada al sistema solicitando una operación de entrada/salida sobre un periférico.

+ b. Cuando expira la cuota periódica de tiempo fijada por el temporizador del kernel para garantizar equidad en la cola de listos.

+ c. Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.

+ d. Cuando el proceso en ejecución incrementa su consumo de memoria RAM superando el límite asignado en su bloque de control de proceso.

### Retroalimentación
En SRT (versión apropiativa de SJF), la decisión de desalojo ocurre al arribar un nuevo proceso: si la ráfaga de CPU del recién llegado es estrictamente menor que el tiempo remanente que le resta al proceso actualmente en ejecución, este es desalojado y devuelto a la cola de listos (Silberschatz Cap. 5.3.2; Clase 4 Diap. 11).

La respuesta correcta es: Cuando arriba un nuevo proceso cuya próxima ráfaga de CPU estimada es menor que el tiempo restante de la ráfaga del proceso en ejecución.

---

## ¿De qué manera el algoritmo HRRN (Highest Response Ratio Next) equilibra la atención de procesos cortos frente a procesos con largas esperas?

+ a. Conmuta de forma preventiva la CPU cada vez que un proceso en espera acumula un tiempo en la cola de listos superior a su propia ráfaga.

+ b. Divide la cola de listos en niveles con quantums crecientes, descendiendo a los procesos intensivos hacia colas de menor prioridad.

+ c. Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.

+ d. Asigna el procesador al proceso que tenga la menor relación entre el tiempo consumido de CPU y el tiempo restante estimado de ejecución.

### Retroalimentación
En HRRN, la tasa de respuesta es R = (w + s) / s = 1 + w/s (donde w es tiempo de espera y s es tiempo de servicio). Al seleccionar el mayor R, prioriza procesos cortos (s pequeño) pero a su vez incrementa el ratio de procesos largos conforme aumenta su tiempo de espera w, evitando la inanición (Stallings Cap. 9.2; Clase 4 Diap. 12).

La respuesta correcta es: Calcula el ratio dinámico R = (w + s) / s, favoreciendo ráfagas cortas pero elevando la prioridad de procesos largos a medida que aumenta su espera.

---

## ¿Qué conjunto de condiciones debe cumplirse simultáneamente para que pueda originarse un interbloqueo (Deadlock) en un sistema operativo?

+ a. Que los procesos compartan el mismo espacio de direcciones y se sincronicen exclusivamente mediante variables atómicas en memoria.

+ b. Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.

+ c. Que el sistema operativo utilice una política de planificación apropiativa que desaloje recursos en función de prioridades dinámicas.

+ d. Que la memoria principal se encuentre saturada de procesos en estado suspendido que compiten por espacio en el área de intercambio.

### Retroalimentación
Coffman (1971) demostró que para que ocurra un interbloqueo deben cumplirse simultáneamente cuatro condiciones: 1) Exclusión mutua, 2) Retención y espera (Hold & Wait), 3) No apropiación (No preemption), y 4) Espera circular. Si se invalida al menos una, el interbloqueo no puede producirse (Silberschatz Cap. 7.1; Diapositivas 4-5).

La respuesta correcta es: Que existan exclusión mutua, retención y espera, no apropiación de recursos y se configure una cadena de espera circular entre procesos.

---

## En un Grafo de Asignación de Recursos (RAG), ¿en qué circunstancia la presencia de un ciclo dirigido NO implica necesariamente un interbloqueo?

+ a. Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.

+ b. Cuando el sistema operativo cuenta con un temporizador de hardware que interrumpe periódicamente a los procesos involucrados en el ciclo.

+ c. Cuando los procesos que forman parte del ciclo se encuentran ejecutando en hilos de usuario sin intervención del despachador del kernel.

+ d. Cuando los recursos implicados en el ciclo son de acceso exclusivo y ningún proceso puede retener más de una instancia simultáneamente.

### Retroalimentación
Si los recursos tienen instancias únicas, un ciclo es condición necesaria y suficiente de interbloqueo. Pero si hay tipos de recursos con múltiples instancias, un ciclo es condición necesaria pero NO suficiente: un proceso externo al ciclo puede terminar su ejecución y liberar instancias del recurso compartido, rompiendo la espera circular (Silberschatz Cap. 7.2; Diapositivas 8-10).

La respuesta correcta es: Cuando los recursos del ciclo tienen múltiples instancias y alguna está asignada a un proceso externo que puede terminar y liberarla.

---

## En el problema de la Cena de los Filósofos, ¿cuál de las siguientes estrategias evita específicamente el interbloqueo rompiendo la condición de espera circular?

+ a. Permitir que un filósofo tome sus palillos únicamente si ambos se encuentran libres simultáneamente en la mesa en ese momento.

+ b. Limitar a cuatro el número máximo de filósofos sentados simultáneamente en la mesa mediante el uso de un semáforo contador de control.

+ c. Expropiar el palillo asignado a un filósofo si este permanece esperando por el segundo palillo durante más de un intervalo de tiempo fijo.

+ d. Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.

### Retroalimentación
Hacer que al menos un filósofo tome primero su palillo derecho y luego el izquierdo mientras los otros toman primero el izquierdo y luego el derecho rompe la simetría y elimina matemáticamente la posibilidad de que se forme una cadena de espera circular (la 4ta condición de Coffman). Las otras estrategias también pueden evitar el interbloqueo, pero lo hacen atacando otras condiciones o restringiendo la concurrencia: exigir ambos palillos simultáneamente elimina retención y espera; limitar a cuatro filósofos evita que todos retengan un palillo al mismo tiempo; y expropiar un palillo modifica la condición de no apropiación (Silberschatz Cap. 6.6; Diapositivas U5).

La respuesta correcta es: Romper la simetría haciendo que uno de los filósofos tome primero el palillo derecho y luego el izquierdo, mientras los demás usan el orden inverso.

---

## ¿Qué caracteriza formalmente a una Condición de Carrera (Race Condition) en un entorno de programación concurrente?

+ a. Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.

+ b. Dos procesos intentan reservar espacio en el heap simultáneamente, provocando fragmentación externa en la memoria principal.

+ c. Un hilo de alta prioridad desaloja repetidamente a un hilo de baja prioridad, impidiendo que este último avance en la cola de listos.

+ d. Múltiples procesos compiten por el ancho de banda del bus de memoria, degradando el rendimiento general de las operaciones de lectura.

### Retroalimentación
Una condición de carrera (race condition) se produce cuando varios procesos o hilos manipulan los mismos datos compartidos de forma concurrente y el resultado de la operación depende del orden no determinista en el que se intercalan sus instrucciones (Silberschatz Cap. 6.1; Diapositivas U5).

La respuesta correcta es: Múltiples hilos acceden y manipulan datos compartidos concurrentemente, y el resultado final depende del orden relativo de su ejecución.