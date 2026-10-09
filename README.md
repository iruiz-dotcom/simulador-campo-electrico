# ⚡ Simulador de Campo Eléctrico y Líneas Equipotenciales
> **Simulador Interactivo de Electromagnetismo para Nivel Universitario**  
> Desarrollado con HTML5 Canvas, JavaScript ES6+ nativo y CSS3 moderno (Glassmorphism & Dark Mode).  
> Arquitectura SPA (Single Page Application) 100% cliente, lista para desplegar en GitHub Pages.

---

## 🎯 Objetivo y Visión General
Proveer a estudiantes y docentes de física e ingeniería de una herramienta de laboratorio virtual en tiempo real para visualizar y experimentar con:
1. **Líneas de Campo Eléctrico ($\vec{E}$)** mediante integración numérica de **Runge-Kutta de 2º orden**.
2. **Curvas Equipotenciales ($V = \text{const}$)** calculadas en tiempo real mediante el algoritmo **Marching Squares**.
3. **Sonda Espacial / Sensor Móvil** para lectura simultánea de potencial $V$, magnitud de campo $|\vec{E}|$, componentes $(E_x, E_y)$, ángulo y cálculo de trabajo electrostático ($W = -q_0 \Delta V$).
4. **Módulo Didáctico de Autoevaluación** con actividades prácticas guiadas y generador de reportes de laboratorio.

---

## 🔬 Modelo Matemático Base
Para $N$ cargas discretas $q_i$ situadas en posiciones fijas o móviles $\mathbf{r}_i = (x_i, y_i)$:

### 1. Potencial Eléctrico Escalar:
$$V(\mathbf{r}) = k_e \sum_{i=1}^{N} \frac{q_i}{\sqrt{|\mathbf{r} - \mathbf{r}_i|^2 + \epsilon^2}}$$

### 2. Campo Eléctrico Vectorial:
$$\mathbf{E}(\mathbf{r}) = -\nabla V = k_e \sum_{i=1}^{N} \frac{q_i (\mathbf{r} - \mathbf{r}_i)}{\left(|\mathbf{r} - \mathbf{r}_i|^2 + \epsilon^2\right)^{3/2}}$$

Donde:
- $k_e = \frac{1}{4\pi \varepsilon_0} \approx 8.98755 \times 10^9 \, \text{N}\cdot\text{m}^2/\text{C}^2$.
- $q_i$ se expresa en nanoCoulombs ($\text{nC} = 10^{-9}\,\text{C}$).
- $\epsilon = 0.015\,\text{m}$ es el factor de suavizado numérico ($r_{\text{min}}$) para evitar singularidades por división entre cero en las vecindades de las cargas puntuales.

---

## 🚀 Guía de Despliegue en la Nube (GitHub Pages)

Dado que la aplicación está construida en un **único archivo autocontenido (`index.html`)**, su publicación en la nube es inmediata y gratuita:

### Paso 1: Crear el repositorio en GitHub
1. Inicia sesión en [GitHub](https://github.com/).
2. Crea un nuevo repositorio público, por ejemplo: `simulador-campo-electrico`.

### Paso 2: Subir el archivo `index.html`
Desde tu terminal dentro de esta carpeta, ejecuta:
```bash
git init
git add index.html README.md
git commit -m "Publicar simulador universitario de campo eléctrico"
git branch -M main
git remote add origin https://github.com/iruiz-dotcom/simulador-campo-electrico.git
git push -u origin main
```
*(O simplemente arrastra `index.html` en la interfaz web de GitHub y pulsa "Commit changes").*

### Paso 3: Activar GitHub Pages
1. En tu repositorio en GitHub, entra a la pestaña **Settings** (Configuración).
2. En el menú lateral izquierdo, haz clic en **Pages**.
3. En la sección **Build and deployment**:
   - **Source:** Selecciona `Deploy from a branch`.
   - **Branch:** Selecciona `main` y carpeta `/ (root)`.
4. Haz clic en **Save** (Guardar).

### Paso 4: Acceso Universal
En aproximadamente 1 minuto, tu simulador estará en vivo y accesible desde cualquier navegador (PC, tablet, smartphone) en la URL:
```text
https://iruiz-dotcom.github.io/simulador-campo-electrico/
```

---

## 💻 Ejecución Local Inmediata
No se requiere instalar Node.js ni configurar servidores:
1. Haz **doble clic** directamente sobre `index.html` en tu explorador de archivos.
2. O ejecuta un servidor local liviano si lo prefieres:
   - Con Python: `python -m http.server 8000`
   - Con Node.js: `npx serve .`

---

## 🧩 Características de la Interfaz y Controles
- **Agregar Cargas:** Botones para añadir cargas positivas ($+2\text{ nC}$) o negativas ($-2\text{ nC}$).
- **Arrastre Dinámico:** Arrastra cualquier carga libremente por el plano con el ratón o el dedo (pantalla táctil).
- **Ajuste de Magnitud:** Slider continuo de $q \in [-10\text{ nC}, +10\text{ nC}]$ con paso de $1\text{ nC}$.
- **Sonda Espacial:** Mueve la mira dorada para obtener lecturas directas en cualquier punto del espacio.
- **Herramienta de Trabajo:** Fija los puntos $A$ y $B$ para calcular el trabajo $W = -q_0 \Delta V$ con una carga de prueba de $1\text{ nC}$.
- **Toggles de Capas:**
  - Líneas de campo $\vec{E}$ (con flechas de sentido de flujo).
  - Curvas equipotenciales (cálidos para $V > 0$, fríos para $V < 0$, verde punteado para $V = 0$).
  - Rejilla de vectores discretos de campo.
  - Mapa de calor de potencial (Heatmap).
- **Presets de Estudio:** Dipolo, Repulsión de cargas iguales, Cuadrupolo y Línea de cargas (placas paralelas).
- **Módulo de Evaluación:** Preguntas conceptuales con validación inmediata y descarga de reporte `.txt`.
- **Exportación:** Captura de pantalla del lienzo en formato PNG de alta resolución.
