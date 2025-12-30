---

# 👻 IP-Obfuscation-Mastery: El Arte de la Invisibilidad

---

[![Author](https://img.shields.io/badge/Author-ZeroEthical-red.svg?style=for-the-badge)](https://github.com/ZeroEthical)
[![License](https://img.shields.io/badge/License-No_Snitches-blue.svg?style=for-the-badge)](https://github.com/ZeroEthical/El-Arte-de-la-Invisibilidad/blob/LICENSE)
[![Level](https://img.shields.io/badge/Level-Black_Belt-black.svg?style=for-the-badge)](https://github.com/ZeroEthical)

> "En internet, nadie sabe que eres un perro... a menos que dejes tu IP marcada en cada poste." - *ZeroEthical*

---

## 💀 Introducción

Bienvenido al **Grimorio de la Ofuscación**. Este repositorio no es para turistas ni para aquellos preocupados por los "Términos de Servicio". Aquí documentamos las técnicas definitivas para manipular, ocultar y vaporizar tu huella digital (Dirección IP).

Ya sea que estés evadiendo censura, realizando *OSINT* agresivo, o simplemente porque valoras tu privacidad por encima de las leyes locales, esta guía es tu biblia.

---

## 📑 Tabla de Contenidos

- [🛡️ Nivel 1: VPN (La Máscara Básica)](#-nivel-1-vpn-la-máscara-básica)
- [🧅 Nivel 2: Tor (El Laberinto)](#-nivel-2-tor-el-laberinto)
- [🔌 Nivel 3: Proxies (El Intermediario)](#-nivel-3-proxies-el-intermediario)
- [🔗 Nivel 4: Chaining (La Pesadilla Forense)](#-nivel-4-chaining-la-pesadilla-forense)
- [🔄 Nivel 5: IP Rotativa (El Fantasma)](#-nivel-5-ip-rotativa-el-fantasma)
- [🧠 OpSec & Advertencias](#-opsec--advertencias)

---

## 🛡️ Nivel 1: VPN (La Máscara Básica)

La **Red Privada Virtual** es tu primera línea de defensa. Cifra tu tráfico y te da una IP de otro país.

### ❌ Lo que NO debes hacer
*   **Usar VPNs Gratuitas:** Si no pagas, tú eres el producto. Venden tus logs al mejor postor.
*   **Creer en el "No-Logs" ciegamente:** Investiga la jurisdicción (evita los "14 Eyes").

### ✅ Recomendaciones (Para gente seria)
Busca proveedores que acepten **Criptomonedas** y no requieran email.
*   [Mullvad](https://mullvad.net/) - Sin cuentas, solo números.
*   [IVPN](https://www.ivpn.net/) - Transparencia total.

---

## 🧅 Nivel 2: Tor (El Laberinto)

**The Onion Router**. Rebota tu tráfico por tres nodos aleatorios alrededor del mundo.

### 🚀 Cómo desplegar
1.  **Tor Browser:** Para navegación web anónima. [Descargar aquí](https://www.torproject.org/).
2.  **Tor Service (Linux):** Para enrutar herramientas de terminal.

```bash
# En Debian/Kali/Ubuntu
sudo apt update && sudo apt install tor
sudo service tor start
# Verificar que corre en el puerto 9050
netstat -antp | grep 9050
```

### ⚠️ Advertencia ZeroEthical
Tor es **LENTO**. No intentes descargar la base de datos de una multinacional por aquí a menos que tengas una paciencia infinita. Además, **tu nodo de salida es visible**. No uses HTTP plano, o el dueño del nodo de salida verá todo.

---

## 🔌 Nivel 3: Proxies (El Intermediario)

Más rápidos que Tor, pero menos seguros si no se configuran bien.

### Tipos de Proxies
| Tipo | Anonimato | Uso Recomendado |
| :--- | :---: | :--- |
| **HTTP** | Bajo ❌ | Navegación web simple, bypass de filtros escolares. |
| **HTTPS** | Medio ⚠️ | Igual que HTTP pero con cifrado SSL. |
| **SOCKS5** | Alto ✅ | **El estándar.** Soporta cualquier tipo de tráfico (TCP/UDP). |

### 🛠️ Herramienta: Proxychains
Obliga a cualquier programa a pasar por un proxy (o Tor).

```bash
# Editar configuración
sudo nano /etc/proxychains4.conf
# Añadir al final:
# socks5  127.0.0.1 9050  (Para usar Tor)
# socks5  1.2.3.4   8080  (Tu proxy privado)

# Ejecutar
proxychains nmap -sT -Pn target.com
```

---

## 🔗 Nivel 4: Chaining (La Pesadilla Forense)

¿Por qué usar uno cuando puedes usarlos todos?

**El Flujo:** `Tú` -> `VPN (Suiza)` -> `Tor (Entrada)` -> `Tor (Salida)` -> `Proxy SOCKS5 (Rusia)` -> `Objetivo`

### Ventajas
*   Si el Proxy cae, ven a Tor.
*   Si Tor se compromete, ven a la VPN.
*   Si la VPN te vende... bueno, buena suerte.

### Desventajas
*   Latencia brutal. Olvídate de ver YouTube. Esto es para operaciones quirúrgicas.

---

## 🔄 Nivel 5: IP Rotativa (El Fantasma)

Ideal para **Web Scraping**, **Brute-forcing** o **DDoS** (con fines educativos, *guiño guiño*). Tu IP cambia con cada petición.

### Cómo funciona
No te conectas a internet, te conectas a una "Gateway".
*   `Request 1` -> Gateway -> IP Residencial A -> Target
*   `Request 2` -> Gateway -> IP Residencial B -> Target

### Proveedores (De Pago)
*   Bright Data
*   Oxylabs
*   Smartproxy

> **Nota:** Estos servicios son caros, pero son la única forma de evitar el *Rate Limiting* de los WAF modernos.

---

## 🧠 OpSec & Advertencias

Escucha bien, porque esto es lo que separa a los profesionales de los que acaban en las noticias:

1.  **Kill Switch:** Configura tu firewall para bloquear TODO el tráfico si la VPN se cae. (`UFW` es tu amigo).
2.  **DNS Leaks:** De nada sirve ocultar tu IP si tu proveedor de internet ve tus peticiones DNS. Usa DNS cifrados o los de tu VPN.
3.  **WebRTC:** Desactívalo en tu navegador. Revela tu IP real incluso detrás de una VPN.
4.  **Fingerprinting:** Tu navegador, resolución de pantalla y fuentes instaladas te hacen único. Usa **Tor Browser** en su configuración por defecto.

---

### ☠️ Disclaimer

```text
La información proporcionada en este repositorio es para fines "educativos" y de "investigación de seguridad".
ZeroEthical no se hace responsable si usas esto para actividades ilegales y terminas con una orden de registro.
Si rompes algo, te lo quedas.
```

---

<p align="center">
  <b>Hecho por ZeroEthical ☕</b><br>
  <i>Mantente en las sombras.👥</i>
</p>
