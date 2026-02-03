# 🧠 Neon Memory Ultimate

![Version](https://img.shields.io/badge/version-1.0.0-blueviolet) ![Tech](https://img.shields.io/badge/tech-HTML5%20%7C%20CSS3%20%7C%20JS-00f3ff) ![License](https://img.shields.io/badge/license-MIT-green)

**Neon Memory Ultimate** es una experiencia de juego de memoria "Single-File" (un solo archivo) de alto rendimiento. Combina la mecánica clásica de encontrar parejas con una estética Cyberpunk/Neon, un motor de audio procedimental y desafíos en 3D utilizando transformaciones CSS avanzadas.

Este proyecto destaca por no utilizar librerías externas ni assets de imagen/audio. Todo se genera mediante código.

## ✨ Características Principales

*   **Zero Dependencies:** Todo el juego está contenido en un único archivo `.html`.
*   **Audio Procedimental:** Sistema de sonido construido con la **Web Audio API**. Genera música y efectos de sonido en tiempo real usando osciladores (sin archivos MP3/WAV).
*   **Motor 3D CSS:** Tableros de juego cúbicos giratorios (3x3 y 10x10) renderizados nativamente por el navegador.
*   **Temas Visuales:** 4 Estilos visuales intercambiables al instante (Neon, Gamer, Gothic, Inferno).
*   **Optimización Móvil:** Ajustes específicos para Android/iOS (Touch actions, Viewport units, GPU layers).
*   **Persistencia:** Guardado automático de récords en `LocalStorage`.

## 🎮 Modos de Juego

El juego incluye 6 modos distintos que escalan en dificultad:

1.  **CLASSIC:** El juego de memoria estándar. Grid 4x4 en 2D.
2.  **OVERLOAD:** Grid 2D, pero las cartas se **barajan (shuffle)** automáticamente cada 10 segundos. ¡Rápido!
3.  **FOCUS:** Grid 2D en completa oscuridad. Utiliza una mecánica de "linterna" que sigue tu cursor/dedo para revelar las cartas.
4.  **3D CUBE:** Un cubo giratorio 3x3. Busca parejas rotando el cubo en el espacio 3D.
5.  **MEGA CUBE:** Un desafío masivo. Cubo 10x10 en cada cara (600 cartas en total).
6.  **HELL CUBE:** La prueba definitiva. Cubo 10x10 que además se baraja cada 10 segundos.

## 🎨 Temas

Puedes cambiar la estética y la escala musical del juego en el menú principal:

*   **⚡ NEON (Default):** Estilo Cyberpunk clásico, sintetizador sinusoidal.
*   **👾 GAMER:** Estilo Arcade Retro, ondas cuadradas (chiptune).
*   **⚰️ GOTHIC:** Estilo oscuro/púrpura, escalas menores.
*   **🔥 HELL:** Estilo infernal/rojo, ondas de diente de sierra (agresivo).

## 🚀 Instalación y Uso

Al ser un archivo único, no requiere instalación de dependencias, servidores ni compilación.

1.  Descarga el archivo `index.html` (o el código proporcionado).
2.  Guárdalo en cualquier carpeta de tu ordenador o móvil.
3.  **Doble clic** para abrirlo en tu navegador web favorito (Chrome, Firefox, Edge, Safari).

> **Nota:** Para que el audio funcione correctamente, el navegador pedirá una interacción inicial (clic en "INICIAR" al abrir el juego) debido a las políticas de autoplay modernas.

## 🕹️ Controles

*   **Interacción:** Clic izquierdo o toque en pantalla para voltear cartas.
*   **Navegación 3D:** Usa los botones de flecha en la parte inferior de la pantalla para rotar el cubo.
*   **Volumen:** Desliza sobre el icono 🔊 abajo a la derecha para ajustar el volumen o silenciar.

## 🛠️ Detalles Técnicos

Para desarrolladores interesados en cómo funciona:

### Estructura
*   **HTML:** Estructura semántica contenedor de las vistas (`.screen`).
*   **CSS:** Uso intensivo de `var(--variables)` para el cambio de temas en tiempo real. `transform-style: preserve-3d` para la lógica del cubo. Animaciones `@keyframes` para el feedback visual (shake, float).
*   **JS (Engine):** Objeto `engine` que maneja el estado, el bucle de renderizado y la lógica de emparejamiento.

### Audio System
El código implementa una clase `AudioSystem`:
```javascript
// Ejemplo simplificado de cómo se genera el tono
const osc = this.ctx.createOscillator();
osc.type = 'sine'; // Cambia según el tema
osc.frequency.setValueAtTime(440, now); // Nota A4
osc.connect(this.master);
osc.start();
```

### Generación de Iconos
Para soportar el **Mega Cube** (600 cartas), el juego genera dinámicamente un array masivo de emojis Unicode, asegurando que existan parejas exactas para cada icono antes de barajar.

## 📄 Licencia

Este proyecto fue creado por **brauliolc.developer** (2026).
Distribuido bajo la licencia MIT. Eres libre de usarlo, modificarlo y compartirlo.

---

*Disfruta poniendo a prueba tu memoria.*
