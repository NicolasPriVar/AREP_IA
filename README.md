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

### `vend/`
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

<img width="982" height="55" alt="image" src="https://github.com/user-attachments/assets/b02a5945-c68e-4569-83a8-db3311fc9bc2" />

---

### hello_ai.ipynb
Notebook que replica el comportamiento de hello_ai.py, pero con una exploración adicional del parámetro temperature.  

Permite observar cómo varía la creatividad o variabilidad de las respuestas del modelo al modificar este valor.  
Es ideal para uso interactivo en VS Code o Jupyter Notebook.  

<img width="982" alt="image" src="https://github.com/user-attachments/assets/4dc8b92e-8589-401a-8857-9515e34982f0" />

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

En el punto 4, acerca de *Parámetros importantes de la API (explicación breve)* encontramos los siguientes ejercicios.  
Al preguntarle acerca de la inteligencia articial en la educación con un temperature de 0.7 nos da como resultado:  
*La inteligencia artificial en la educación se refiere al uso de tecnologías avanzadas para personalizar y mejorar el proceso de enseñanza y aprendizaje, adaptándose a las necesidades individuales de los estudiantes. Esto incluye herramientas como tutores virtuales, sistemas de evaluación automatizados y análisis de datos para optimizar el rendimiento académico y la gestión educativa.*

La misma pregunta con 0.2 nos da como resultado:  
*La inteligencia artificial en la educación se refiere al uso de tecnologías avanzadas para personalizar el aprendizaje, adaptando contenidos y métodos a las necesidades individuales de los estudiantes. Además, facilita la automatización de tareas administrativas y ofrece herramientas de análisis que ayudan a mejorar la enseñanza y el rendimiento académico.*

Y la misma pregunta pero con 1.0 nos da como resultado:  
*La inteligencia artificial en la educación se refiere al uso de tecnologías que simulan procesos cognitivos humanos para personalizar el aprendizaje, adaptando contenidos y métodos a las necesidades de cada estudiante. Además, facilita la automatización de tareas administrativas y la mejora de la retroalimentación, lo que permite a los educadores enfocarse más en el desarrollo integral de los alumnos.*

En el punto de *Comentarios sobre temperature* obtenemos la salida como un JSON, quedando así:  
{  
  "operation": "explanation",  
  "input": "¿Qué es aprendizaje supervisado?",  
  "output": "El aprendizaje supervisado es un tipo de aprendizaje automático donde un modelo se entrena utilizando un conjunto de datos etiquetados. Esto significa que cada entrada en el conjunto de datos tiene una salida conocida, lo que permite al modelo aprender a predecir la salida correcta para nuevas entradas. Se utiliza comúnmente en tareas como clasificación y regresión."  
}  

Valid JSON → {'operation': 'explanation', 'input': '¿Qué es aprendizaje supervisado?', 'output': 'El aprendizaje supervisado es un tipo de aprendizaje automático donde un modelo se entrena utilizando un conjunto de datos etiquetados. Esto significa que cada entrada en el conjunto de datos tiene una salida conocida, lo que permite al modelo aprender a predecir la salida correcta para nuevas entradas. Se utiliza comúnmente en tareas como clasificación y regresión.'}  

Ahora en los ejercicios propuestos, haremos lo siguiente:  
1. Cambia `temperature` a 0.1, 0.5 y 0.9 y compara el estilo de las respuestas.
2. Pide que el modelo responda **siempre en JSON** usando un `system` que lo exija. Verifica si cumple.
3. Crea un prompt de tu área (p.ej., *programación*, *arquitectura*, *matemáticas*) que devuelva un JSON con `operation`, `input`, `steps` (lista) y `output`.
4. Limita la longitud con `max_tokens` y observa si corta.

La respuesta teniendo 0.1 en temperature fue:  
*{  
  "prompt": "Explica brevemente el principio de funcionamiento de un árbol de decisión.",  
  "respuesta": "Un árbol de decisión es un modelo de aprendizaje automático que utiliza un enfoque estructurado en forma de árbol para tomar decisiones basadas en características de entrada. Cada nodo interno representa una prueba sobre un atributo, cada rama representa el resultado de esa prueba y cada hoja representa una clase o resultado final, permitiendo clasificar o predecir datos de manera intuitiva."  
}*  
La respuesta teniendo 0.5 en temperature fue:  
*{  
  "prompt": "Explica brevemente el principio de funcionamiento de un árbol de decisión.",  
  "respuesta": "Un árbol de decisión es un modelo de aprendizaje automático que utiliza una estructura jerárquica para tomar decisiones basadas en características de los datos. Cada nodo interno representa una prueba en una característica, cada rama representa el resultado de esa prueba y cada hoja representa una clase o resultado final, permitiendo así clasificar o predecir resultados a partir de las características de entrada."  
}*
La respuesta teniendo 0.9 en temperature fue:  
*{  
  "prompt": "Explica brevemente el principio de funcionamiento de un árbol de decisión.",  
  "respuesta": "Un árbol de decisión es un modelo de aprendizaje automático que utiliza una estructura jerárquica para tomar decisiones basadas en características de los datos. Cada nodo interno representa una pregunta sobre una característica, cada rama representa el resultado de esa pregunta, y cada hoja representa una decisión o resultado final, permitiendo clasificar o predecir valores a partir de las respuestas a las preguntas."  
}*  

Al comparar el estilo de las respuestas, nos damos cuenta que:  
Si es para enseñar o divulgar, la tercera es la mejor (más clara y humana).  
Si es para un reporte técnico o académico, la segunda es la más equilibrada.  
Si es para un paper o documentación formal, la primera es la más precisa.  

Vemos que en efecto siempre contesta en formato JSON.

Al preguntarle acerca de los contenedores y su uso, nos da como resultado:
*{  
  "operation": "explicar_contenedores",  
  "input": "contenedores en programación",  
  "steps": [  
    "Definir qué son los contenedores: estructuras de datos que almacenan y organizan elementos.",  
    "Describir su utilidad: permiten gestionar colecciones de datos de manera eficiente y facilitan operaciones como la búsqueda, inserción y eliminación."  
  ],  
  "output": "Los contenedores son estructuras de datos que permiten almacenar y organizar elementos de manera eficiente, facilitando operaciones como la búsqueda,   inserción y eliminación de datos en un programa."  
}*  
Ahora acortamos max_tokens a 100 y da como resultado:  
*{  
  "operation": "explicacion_contenedores",  
  "input": "contenedores en programación",  
  "steps": [  
    "Los contenedores son estructuras de datos que permiten almacenar y organizar colecciones de elementos.",  
    "Sirven para facilitar la gestión de datos, permitiendo operaciones como la inserción, eliminación y búsqueda de manera eficiente."  
  ],  
  "output": "Los contenedores son esenciales en la programación para manejar conjuntos de datos de forma estructurada y*  
  Notamos que si acorta la respuesta pero no de la manera esperada.
