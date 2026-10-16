## 3 Planificación

**FIFS** tiene efecto Convoy

**SRT** despacha primero las ráfagas más breves y es la versión con desalojo
SJN(SJF) versión sin desalojo

**HRN** (Highest-Response-Ratio-Next o HRRN) prioridad dinámica. Aumenta prioridad conforme a mayor tiempo de espera. Evita inanición de procesos grandes. w es el tiempo que lleva esperando.

**Round Robin** usa una cola y se evita tener Quantum muy extensos 

Para evitar inanición de procesos se usa Envejecimiento

Tiempo de retorno es desde que un proceso arriba al sistema hasta que termina su ejecución

Afinidad a procesador en Arq multinucleo es para Reutilizar lineas de datos calientes residentes en Caché

## 4 Bloqueo

Si no hay espera circular no hay Interbloqueo

**Dijktra** = Algoritmo del Banquero