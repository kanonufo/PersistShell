# PersistShell
Este proyecto proporciona un módulo Aggressor Script para Cobalt Strike llamado PersistShell. Este módulo detecta procesos que han ejecutado shellcode y establece persistencia en el sistema comprometido mediante la creación de una tarea programada.
# Detectando Shellcode y Estableciendo Persistencia: Una Mirada Profunda al Módulo PersistShell

**Introducción**

El shellcode, una forma de código ejecutable utilizado comúnmente en ataques informáticos, puede representar una seria amenaza para la seguridad de un sistema. Detectar la ejecución de shellcode y tomar medidas para mitigar su impacto son pasos críticos en la defensa contra ciberataques. En este artículo, exploraremos el módulo PersistShell, que detecta procesos que han ejecutado shellcode y establece persistencia en el sistema mediante la creación de una tarea programada. Profundizaremos en las técnicas utilizadas y cómo estas contribuyen a la efectividad y resistencia del módulo.

**Syscalls: La Base de la Detección**

El módulo PersistShell utiliza llamadas al sistema (syscalls) para leer la memoria de los procesos y buscar patrones comunes de shellcode. En lugar de utilizar API de alto nivel, las syscalls proporcionan acceso directo al kernel del sistema operativo, lo que permite una mayor flexibilidad y control. Al utilizar la syscall NtReadVirtualMemory, el módulo puede examinar la memoria de los procesos de manera eficiente y sin ser detectado por las soluciones de seguridad tradicionales.

**Dinvoke: Ejecutando Funciones de la API de Windows**

Para establecer la persistencia en el sistema, el módulo utiliza dinvoke para llamar a la función WinExec de la API de Windows. Esto permite ejecutar comandos en el contexto del sistema sin la necesidad de invocar un proceso secundario visible, lo que lo hace más difícil de detectar para las soluciones de seguridad convencionales. En este caso, se crea una tarea programada que se ejecutará en el inicio del sistema para garantizar que la persistencia se mantenga incluso después de un reinicio.

**Reflexión: Flexibilidad y Adaptabilidad**

El uso de reflexión permite cargar dinámicamente las funciones necesarias en tiempo de ejecución, lo que proporciona una mayor flexibilidad y adaptabilidad al código. En lugar de depender de llamadas directas a funciones de la API de Windows, el módulo utiliza dinvoke para invocarlas de manera dinámica, lo que dificulta la detección y el análisis por parte de los sistemas de seguridad.

**Conclusiones**

El módulo PersistShell ofrece una poderosa herramienta para detectar la ejecución de shellcode y establecer persistencia en sistemas comprometidos. Al utilizar técnicas avanzadas como syscalls, dinvoke y reflexión, el módulo es capaz de evadir la detección y mitigar eficazmente las amenazas de seguridad. Su diseño modular y su capacidad para adaptarse a diferentes entornos lo convierten en una herramienta invaluable en la lucha contra el cibercrimen.

Uso:
Descarga el archivo PersistShell.cna del repositorio.

Abre Cobalt Strike y carga el script Aggressor Script PersistShell.cna.

Una vez cargado, puedes ejecutar el módulo desde el menú "Scripts" en Cobalt Strike.

El módulo escaneará todos los procesos en el sistema y detectará aquellos que hayan ejecutado shellcode.

Para los procesos que hayan ejecutado shellcode, establecerá la persistencia mediante la creación de una tarea programada.

¡Y eso es todo! Ahora puedes utilizar el módulo PersistShell para detectar ejecuciones de shellcode y establecer persistencia en sistemas comprometidos a través de Cobalt Strike.
