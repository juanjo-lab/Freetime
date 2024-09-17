# Script para Verificar IPs Disponibles en una Red Local (0 a 77)

Este script en batch para Windows 10 permite realizar un ping a las direcciones IP de un rango específico (de `0` a `77` en este caso) en una red local para verificar cuáles IPs están disponibles.

## ¿Cómo funciona?

El script utiliza un bucle `FOR` en el `cmd` para recorrer un rango de direcciones IP (`192.168.1.0` a `192.168.1.77`) y realizar un `ping` a cada una de ellas. Dependiendo de si hay una respuesta, se indicará si la IP está "disponible" o "no disponible".

### Código del Script:

```batch
@echo off
for /l %%i in (0,1,77) do (
    ping -n 1 -w 100 192.168.1.%%i >nul
    if errorlevel 1 (
        echo IP 192.168.1.%%i no disponible
    ) else (
        echo IP 192.168.1.%%i disponible
    )
)
pause

Explicación del Código:
@echo off:

Evita que los comandos del script se muestren en pantalla durante la ejecución.
for /l %%i in (0,1,77) do (:

Este bucle recorre los números de 0 a 77, usando la variable %%i como contador.
ping -n 1 -w 100 192.168.1.%%i >nul:

Envía un solo paquete de ping (-n 1) a cada dirección IP en la red 192.168.1.X, donde X es el valor actual de %%i.
Si no recibe respuesta en 100 ms (-w 100), continúa con la siguiente IP.
El operador >nul oculta la salida del comando ping.
if errorlevel 1:

Si el comando ping no tiene éxito, errorlevel será igual a 1, lo que significa que la IP no está disponible.
echo IP 192.168.1.%%i no disponible:

Si el ping falla, imprime en pantalla que la IP no está disponible.
else echo IP 192.168.1.%%i disponible:

Si el ping tiene éxito, se muestra que la IP está disponible.
pause:

Mantiene la ventana del cmd abierta una vez que el script ha terminado de ejecutarse, para que puedas ver los resultados.
