#  Proyecto Hello AI

Este repositorio contiene varios ejemplos y notebooks introductorios para interactuar con la **API de OpenAI** utilizando Python. El propósito es demostrar cómo inicializar el cliente, enviar prompts y recibir respuestas generadas por modelos de lenguaje como gpt-4o-mini.

---

##  Estructura General del Proyecto

hello_ai/
│  
├── vend/  
│ ├── Include/  
│ ├── Lib/  
│ └── Scripts/  
│  
├── .env  
└── hello_ai.py  
  
hello_ai_vscode/  
│  
├── .venv/  
├── .env  
├── hello_ai.ipynb  
├── setup_hello_ai.ipynb  
└── Guia3_IntroAPIsAI_Notebook.ipynb  


---

##  Descripción de Carpetas

### 🗂️ `vend/`
Esta carpeta contiene un **entorno virtual** creado para aislar las dependencias del proyecto. Se genera con herramientas como `python -m venv vend`.

Dentro hay tres subcarpetas principales:

- **Include/**  
  Contiene archivos de cabecera usados internamente por Python y las extensiones.  
  Se usa cuando se compilan módulos o librerías dependientes de Python.

- **Lib/**  
  Guarda todas las **bibliotecas y paquetes de Python** instalados en el entorno virtual (por ejemplo, openai, dotenv, etc.).  
  Es el equivalente local al directorio site-packages del sistema.

- **Scripts/**  
  Contiene los **ejecutables** asociados al entorno virtual, incluyendo el intérprete de Python y el comando pip.  
  En Windows, desde aquí se activa el entorno con:  
  .\vend\Scripts\activate  
##  Archivos Clave

###  .env
Archivo que guarda variables de entorno confidenciales, como la clave de API de OpenAI.

Este archivo permite mantener la información sensible fuera del código fuente y es cargado automáticamente por el paquete python-dotenv.  
**Ejemplo:** contiene la variable OPENAI_API_KEY con la clave personal de acceso a la API de OpenAI.  

Advertencia: No debe compartirse ni subirse a repositorios públicos.

---

### hello_ai.py
Script principal del proyecto.  
Su función es realizar una solicitud al modelo de OpenAI con un prompt sencillo y mostrar la respuesta en consola.  

Carga la clave API desde el archivo .env, inicializa el cliente de OpenAI, envía un mensaje al modelo gpt-4o-mini y finalmente imprime el texto generado por la IA.  

![textoGenerado](image.png)
---

### hello_ai.ipynb
Notebook que replica el comportamiento de hello_ai.py, pero con una exploración adicional del parámetro temperature.  

Permite observar cómo varía la creatividad o variabilidad de las respuestas del modelo al modificar este valor.  
Es ideal para uso interactivo en VS Code o Jupyter Notebook.  

![textoDeRespuestas](image-1.png)
---

### setup_hello_ai.ipynb
Notebook de configuración inicial.  
Su único propósito es instalar las dependencias necesarias del proyecto (como openai y python-dotenv).  

Se ejecuta una vez al comienzo para preparar el entorno antes de trabajar con los demás notebooks.  

---

### Guia3_IntroAPIsAI_Notebook.ipynb
Es el Notebook más completo del proyecto, diseñado como guía didáctica para aprender el uso básico y avanzado de la API de OpenAI.  

Incluye ejemplos de:
- Envío de prompts con diferentes parámetros.
- Respuestas en formato estructurado (JSON) para integración con otros sistemas.
- Manejo de errores al interpretar JSON.
- Creación de una función genérica (ask_model) para hacer consultas personalizadas al modelo.

Este notebook combina teoría, práctica y automatización, siendo una referencia para futuros proyectos que utilicen la API de OpenAI.
