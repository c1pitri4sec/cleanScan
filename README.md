# cleanScan

\`\`\`
   ________                    _____                 
  / ____/ /__  ____ _____     / ___/_________ _____  
 / /   / / _ \/ __ `/ __ \    \__ \/ ___/ __ `/ __ \ 
/ /___/ /  __/ /_/ / / / /   ___/ / /__/ /_/ / / / / 
\____/_/\___/\__,_/_/ /_/   /____/\___/\__,_/_/ /_/  
                
                    by c1pitri4sec
\`\`\`

Script en Bash para automatizar el reconocimiento inicial de puertos con Nmap: escaneo rápido de todos los puertos, escaneo detallado (`-sC -sV`) solo sobre los puertos abiertos, y salida en formato tabla legible.

## Qué hace

1. Escaneo rápido con `nmap -sS --min-rate 5000` sobre todos los puertos.
2. Extrae los puertos abiertos automáticamente.
3. Lanza un segundo escaneo (`-sC -sV`) solo sobre esos puertos.
4. Muestra los resultados en una tabla con colores (puerto / servicio / versión).
5. Guarda el detalle completo de los scripts NSE en `detailedscan` para consulta.
6. Limpia los archivos temporales al finalizar.

## Instalación

\`\`\`bash
git clone https://github.com/tu-usuario/cleanScan.git
cd cleanScan
sudo cp cleanScan.sh /usr/local/bin/cleanScan
sudo chmod +x /usr/local/bin/cleanScan
\`\`\`

## Uso

\`\`\`bash
cleanScan <IP>
\`\`\`

### Ejemplo

\`\`\`
❯ cleanScan 192.168.26.128
[+] Escaneando puertos...
[+] Estos son los puertos abiertos con sus servicios escaneados:
 PUERTO  SERVICIO  VERSION
 22      http      SimpleHTTPServer 0.6 (Python 3.13.5)
 80      http      SimpleHTTPServer 0.6 (Python 3.13.5)

[+] Para más detalles sobre los scripts NSE, consulta el archivo detailedscan
\`\`\`

## Requisitos

- `nmap`
- `sudo` (necesario para `-sS`)
- Bash

## Notas

- Requiere permisos de root para el escaneo SYN (`-sS`).
- Pensado para entornos de laboratorio / CTF (HackTheBox, TryHackMe, etc.), no para escanear redes sin autorización.
