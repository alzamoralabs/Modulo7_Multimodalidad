# 🧠 Módulo 7: Multimodalidad con IA

> **Sesión 17** — Curso de Inteligencia Artificial Aplicada  
> Repositorio de materiales, ejercicios y ejemplos prácticos sobre modelos multimodales.

---

## 📌 Descripción

Este módulo explora el concepto de **multimodalidad** en los modelos de inteligencia artificial: la capacidad de procesar y generar información en múltiples formatos, combinando texto, imágenes, audio y video en un mismo flujo de trabajo.

A lo largo de este módulo aprenderás a:

- Comprender qué son los modelos multimodales y cómo funcionan
- Trabajar con APIs de visión artificial (análisis de imágenes con LLMs)
- Procesar audio y transcribir voz a texto
- Generar imágenes a partir de descripciones textuales
- Integrar múltiples modalidades en aplicaciones reales

---

## 🗂️ Estructura del Repositorio

```
Modulo7_Multimodalidad/
├── notebooks/           # Jupyter Notebooks con ejercicios y ejemplos
├── scripts/             # Scripts Python listos para ejecutar
├── assets/              # Imágenes y archivos de ejemplo
├── slides/              # Presentaciones de la sesión
└── README.md
```

---

## 🚀 Tecnologías Utilizadas

| Tecnología | Uso |
|---|---|
| **OpenAI GPT-4o / Vision** | Análisis y descripción de imágenes |
| **Whisper** | Transcripción de audio a texto |
| **DALL-E / Stable Diffusion** | Generación de imágenes desde texto |
| **Claude (Anthropic)** | Modelos multimodales alternativos |
| **Python 3.10+** | Lenguaje base de los ejemplos |
| **Jupyter Notebooks** | Entorno interactivo de aprendizaje |

---

## ⚙️ Requisitos e Instalación

### Prerrequisitos

- Python 3.10 o superior
- Cuenta en [OpenAI](https://platform.openai.com/) (para GPT-4o y Whisper)
- Cuenta en [Anthropic](https://console.anthropic.com/) *(opcional)*

### Instalación

```bash
# 1. Clona el repositorio
git clone https://github.com/alzamoralabs/Modulo7_Multimodalidad.git
cd Modulo7_Multimodalidad

# 2. Crea un entorno virtual
python -m venv venv
source venv/bin/activate       # Linux/macOS
# venv\Scripts\activate        # Windows

# 3. Instala las dependencias
pip install -r requirements.txt
```

### Variables de entorno

Crea un archivo `.env` en la raíz del proyecto con tus claves de API:

```env
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
```

---

## 📚 Contenidos del Módulo

### 🔍 1. Introducción a la Multimodalidad
- ¿Qué es un modelo multimodal?
- Diferencias entre modelos unimodales y multimodales
- Casos de uso reales

### 🖼️ 2. Visión por Computadora con LLMs
- Análisis de imágenes con GPT-4o Vision
- Extracción de información de documentos e imágenes
- OCR inteligente con modelos de lenguaje

### 🎙️ 3. Procesamiento de Audio
- Transcripción de audio con Whisper
- Análisis de sentimiento en voz
- Speech-to-text en tiempo real

### 🎨  4. Generación de Imágenes
- Texto a imagen con DALL-E 3
- Prompting avanzado para generación visual
- Edición y variación de imágenes

### 🔗 5. Integración Multimodal
- Pipelines que combinan texto + imagen + audio
- Construcción de aplicaciones multimodales
- Casos prácticos y proyectos finales

---

## 🧪 Ejemplos Rápidos

### Análisis de imagen con GPT-4o

```python
from openai import OpenAI
import base64

client = OpenAI()

with open("imagen.jpg", "rb") as f:
    imagen_b64 = base64.b64encode(f.read()).decode("utf-8")

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {
            "role": "user",
            "content": [
                {"type": "text", "text": "¿Qué ves en esta imagen?"},
                {"type": "image_url", "image_url": {"url": f"data:image/jpeg;base64,{imagen_b64}"}}
            ]
        }
    ]
)

print(response.choices[0].message.content)
```

### Transcripción de audio con Whisper

```python
from openai import OpenAI

client = OpenAI()

with open("audio.mp3", "rb") as audio_file:
    transcripcion = client.audio.transcriptions.create(
        model="whisper-1",
        file=audio_file,
        language="es"
    )

print(transcripcion.text)
```

---

## 📖 Recursos Adicionales

- [Documentación de OpenAI](https://platform.openai.com/docs)
- [Documentación de Anthropic](https://docs.anthropic.com)
- [Whisper en GitHub](https://github.com/openai/whisper)
- [Paper: GPT-4 Technical Report](https://arxiv.org/abs/2303.08774)

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si encuentras un error o tienes alguna mejora:

1. Haz un fork del repositorio
2. Crea una rama: `git checkout -b feature/mi-mejora`
3. Realiza tus cambios y haz commit: `git commit -m 'Agrega nueva funcionalidad'`
4. Sube los cambios: `git push origin feature/mi-mejora`
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

## 👤 Autor

**alzamoralabs**  
🔗 [GitHub](https://github.com/alzamoralabs)

---

<p align="center">Hecho con ❤️ para el aprendizaje de IA</p>