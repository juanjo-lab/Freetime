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
