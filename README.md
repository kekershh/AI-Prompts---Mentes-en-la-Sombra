# 🕵️ Mentes en la Sombra: Perfilado Criminal con IA

> **Curso:** Inteligencia Artificial: Generación de Prompts  
> **Comisión:** N° 95825  
> **Autora:** Angelica Aparicio  
> **Entrega:** Pre-entrega 2 — Fast Prompting en Acción

---

## 📌 Descripción del Proyecto

**Mentes en la Sombra** es una herramienta de apoyo formativo para estudiantes y profesionales de criminología, psicología forense y seguridad ciudadana.

Mediante un flujo de prompts encadenados y técnicas de Fast Prompting, el sistema genera automáticamente material educativo completo a partir de un único dato de entrada: el tipo de delito a analizar.

---

## 🎯 Problema que resuelve

Generar material formativo especializado en análisis de perfiles criminales es costoso en tiempo y requiere expertise combinado en psicología, criminología y diseño instruccional. Los recursos disponibles de forma libre y accesible son escasos.

**Esta herramienta democratiza el acceso** a material de calidad, permitiendo que docentes y estudiantes generen escenarios ficticios realistas, perfiles psicológicos fundamentados y ejercicios didácticos estructurados en minutos.

---

## 🧠 Técnicas de Fast Prompting aplicadas

| Técnica | Aplicación en el proyecto |
|---|---|
| **Role Prompting** | Cada prompt asigna un rol especializado: criminólogo, psicólogo forense, docente universitario |
| **Zero-Shot** | El escenario ficticio se genera sin ejemplos previos |
| **Few-Shot** | El perfil psicológico incluye un ejemplo de razonamiento para guiar el output |
| **Chain of Thought** | El perfil sigue el esquema: evidencia de la escena → conclusión del rasgo |
| **Prompts encadenados** | La salida de cada prompt alimenta el siguiente, manteniendo coherencia |

---

## 🔗 Flujo del sistema

```
[Input: tipo de delito]
        │
        ▼
┌─────────────────────┐
│  LLAMADA 1 (API)    │  → Zero-Shot + Role Prompting
│  Escenario ficticio │
└────────┬────────────┘
         │  contexto
         ▼
┌─────────────────────┐
│  LLAMADA 2 (API)    │  → Few-Shot + Chain of Thought + Role Prompting
│  Perfil psicológico │
└────────┬────────────┘
         │  contexto acumulado
         ▼
┌─────────────────────┐
│  LLAMADA 3 (API)    │  → Role Prompting + instrucción estructurada
│  Ejercicio didáctico│
└─────────────────────┘
         │
         ▼
[Output: material formativo completo]
```

**Total de consultas a la API: 3** — optimizado para minimizar costos.

---

## 🛠️ Herramientas y tecnologías

| Herramienta | Uso |
|---|---|
| **Python 3.10+** | Lenguaje del proyecto |
| **Google Gemini API** (`gemini-1.5-flash`) | Modelo texto-texto — gratuito |
| **Nightcafe / Stable Diffusion** | Generación de imágenes ilustrativas (manual, externa) |
| **Jupyter Notebook** | Entorno de demostración de la POC |

---

## 🚀 Cómo ejecutar el proyecto

### 1. Clonar el repositorio
```bash
git clone https://github.com/TU_USUARIO/mentes-en-la-sombra.git
cd mentes-en-la-sombra
```

### 2. Instalar dependencias
```bash
pip install google-generativeai
```

### 3. Obtener tu API key gratuita de Gemini
Ingresá a [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) y generá tu clave.

### 4. Configurar la API key en el notebook
En la celda de configuración, reemplazá:
```python
GEMINI_API_KEY = "TU_API_KEY_AQUI"
```

### 5. Ejecutar el notebook
```bash
jupyter notebook mentes_en_la_sombra.ipynb
```

---

## 📁 Estructura del repositorio

```
mentes-en-la-sombra/
│
├── mentes_en_la_sombra.ipynb   # POC principal con Fast Prompting
├── README.md                   # Este archivo
└── assets/                     # (Opcional) Imágenes generadas con Nightcafe
```

---

## 📊 Viabilidad y optimización

- **3 llamadas a la API** para generar el material completo (escenario + perfil + ejercicio)
- El contexto se pasa explícitamente entre prompts, evitando llamadas adicionales de "resumen"
- Modelo `gemini-1.5-flash`: gratuito, rápido y con ventana de contexto amplia
- Sin dependencias de infraestructura externa ni licencias pagas

---

## ⚖️ Consideraciones éticas

El sistema trabaja **exclusivamente con escenarios ficticios**. No utiliza datos reales de víctimas, casos judiciales ni personas identificables. El enfoque es estrictamente académico y formativo.

Los prompts de generación de imágenes utilizan vocabulario de **atmósfera y estética** (noir, misterio, tensión, evidencia policial) para evitar contenido explícito y respetar los filtros de seguridad de las herramientas de imagen.

---

*Proyecto desarrollado para el curso de Inteligencia Artificial: Generación de Prompts — Comisión 95825*
