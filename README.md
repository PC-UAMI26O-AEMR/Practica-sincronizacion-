# Procesos de Sincronizacion 
Los procesos de sincronización en programación concurrente son mecanismos que coordinan la ejecución de múltiples hilos o procesos. Su objetivo principal es evitar las "condiciones de carrera", asegurando que el acceso a datos o recursos compartidos sea seguro y ordenado.

- **Lock (Exclusión Mutua):** Funciona como la llave de una habitación. Si un hilo adquiere el _lock_, entra a la "sección crítica" y asegura la puerta. Si otros hilos intentan entrar, el sistema operativo los "duerme" (los bloquea) hasta que el primer hilo termina y devuelve la llave. Es ideal cuando el hilo va a tardar un tiempo usando el recurso.
    
- **Spinlock:** Es una variante del _lock_, pero en lugar de que el sistema operativo "duerma" al hilo que está esperando, este se queda en un bucle infinito preguntando activamente: "¿Ya terminaste? ¿Ya terminaste?" (espera ocupada). Consume ciclos de CPU, pero es muy rápido porque evita el costo de cambiar el contexto del hilo en el procesador. Solo se usa cuando se espera que el recurso se libere en microsegundos.
    
- **Semáforo (Semaphore):** A diferencia del _lock_ (que es de un solo dueño), el semáforo utiliza un contador numérico para controlar el acceso.
    
    - **Semáforo binario (0 o 1):** Funciona de manera similar a un _lock_.
        
    - **Semáforo contador (N):** Permite que un número específico de hilos accedan a un recurso al mismo tiempo (por ejemplo, limitar la descarga a máximo 5 archivos simultáneos). Si el contador llega a cero, los siguientes hilos deben esperar a que alguien termine.
        
- **Barrera (Barrier):** Actúa como un punto de encuentro para un grupo de hilos. Si una tarea se divide en varias partes, un hilo que termina su parte llega a la barrera y se detiene. **Ningún hilo puede cruzar la barrera hasta que todos los hilos involucrados hayan llegado a ese mismo punto**. Una vez que llega el último, la barrera se abre y todos continúan su ejecución al mismo tiempo.
