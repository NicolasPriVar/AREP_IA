# 📘 Proyecto: Prácticas de Inteligencia Artificial con OpenAI, LangChain.
### Explicación del taller
Este repositorio contiene distintos ejemplos y guías prácticas para conectar Python con modelos de lenguaje avanzados.

---

## 🧩 Estructura del Proyecto

| Carpeta / Archivo | Descripción |
|-------------------|-------------|
| `.env` | Archivo de entorno con la clave privada de OpenAI (no debe subirse a GitHub). |
| `hello_ai.py` | Ejemplo base de conexión con la API de OpenAI, carga de variables de entorno y generación de texto. |
| `hello_ai.ipynb` | Guía paso a paso sobre instalación, configuración, parámetros (`temperature`, `max_tokens`, etc.) y ejercicios iniciales con la API. |
| `guia4_langchain.ipynb` | Introducción práctica a LangChain: prompts, cadenas secuenciales, memoria y buenas prácticas educativas. |

---

## ⚙️ Configuración del Entorno

### 1️⃣ Instalar dependencias

Ejecuta en tu terminal o notebook:

pip install openai python-dotenv langchain langchain-openai transformers datasets huggingface_hub tokenizers torch

### 2️⃣ Configurar variables de entorno

En el archivo .env ponemos una variable para la clave de OPENAI, en este caso será OPENAI_API_KEY seguido de la clave signada (Esta clave no se debe publicar en GitHub ni en un lugar público)

### 3️⃣ Cargar las variables en Python

Dentro de los cuadernos encontramos 

import os

from dotenv import load_dotenv

from openai import OpenAI

Esto lo que permite es cargar en nuestro programa la llave que asignamos anteriormente.

