# Analizador de Resultados Académicos

Aplicación web para **analizar resultados académicos a partir de un archivo Excel**. La herramienta está pensada para centros educativos y permite calcular automáticamente el número de suspensos del alumnado, agrupar los resultados por nivel y unidad, y mostrar los datos mediante tablas y gráficas.

La aplicación está diseñada para publicarse y ejecutarse directamente desde **GitHub Pages**, por lo que **no requiere instalar Python ni ningún programa adicional**. Todo el procesamiento se realiza **localmente en el navegador**.

---

# Características

- Carga archivos **Excel (.xlsx)**
- Calcula automáticamente **materias suspensas (nota < 5)**
- Agrupa resultados por **etapa educativa** y **unidad**
- Clasifica al alumnado según número de suspensos
- Genera **tabla de resultados por unidad**
- Genera **gráficas comparativas**
- Funciona completamente **en el navegador**
- Puede publicarse fácilmente con **GitHub Pages**

---

# Clasificación de suspensos

Se considera suspenso cualquier **nota inferior a 5**.

Los alumnos se clasifican en las siguientes categorías:

| Categoría | Número de suspensos |
|---|---|
| 0 | Ningún suspenso |
| 1-2 | Entre 1 y 2 suspensos |
| 3-4 | Entre 3 y 4 suspensos |
| 5+ | 5 o más suspensos |

---

# Formato del archivo Excel

El archivo Excel debe contener las siguientes columnas (según posición):

| Dato | Columna Excel |
|---|---|
| Nombre | E |
| Apellido 1 | F |
| Apellido 2 | G |
| Etapa | K |
| Unidad | N |
| Materia | T |
| Nota | AB |

Cada fila debe representar **una materia de un alumno**.

El sistema agrupa automáticamente las materias por alumno para calcular el número total de suspensos.

---

# Estructura del repositorio

El proyecto está organizado de la siguiente forma:

```
analizador-resultados-academicos
│
├── index.html
├── README.md
├── LICENSE
│
├── css
│   └── styles.css
│
├── js
│   └── script.js
│
├── data
│   └── ejemplo_excel.xlsx
│
├── docs
│   └── guia_usuario.md
│
└── assets
    └── logo.png
```

---

# Descripción de carpetas

## index.html

Archivo principal de la aplicación web. Contiene:

- interfaz de usuario
- carga del archivo Excel
- tabla de resultados
- gráfico comparativo

También carga las librerías externas necesarias.

---

## css/

Contiene los estilos visuales de la aplicación.

Archivo principal:

```
css/styles.css
```

Define tipografía, tabla de resultados y diseño básico.

---

## js/

Contiene la lógica principal del programa.

Archivo principal:

```
js/script.js
```

Responsable de:

1. Leer el archivo Excel
2. Agrupar materias por alumno
3. Calcular suspensos
4. Clasificar alumnado
5. Agrupar resultados por etapa y unidad
6. Generar tabla de resultados
7. Crear gráficos

---

## data/

Carpeta opcional que contiene **archivos Excel de ejemplo** para probar la aplicación.

Ejemplo:

```
data/ejemplo_excel.xlsx
```

Esto facilita entender el formato esperado.

---

## docs/

Documentación adicional del proyecto.

Ejemplo:

```
docs/guia_usuario.md
```

Puede incluir:

- guía para profesorado
- explicación del formato del Excel
- ejemplos de uso

---

## assets/

Archivos gráficos del proyecto.

Ejemplos:

- logo
- iconos
- imágenes para la documentación

---

# Cómo usar la aplicación

1. Abrir la página web de la aplicación.
2. Cargar el archivo Excel mediante el selector de archivo.
3. El sistema analizará automáticamente los datos.
4. Seleccionar el **nivel educativo**.
5. Consultar la tabla de resultados y la gráfica.

---

# Publicar la aplicación en GitHub Pages

## 1 Crear repositorio

Crear un repositorio en GitHub, por ejemplo:

```
analizador-resultados-academicos
```

## 2 Subir los archivos

Subir todos los archivos del proyecto:

- index.html
- css/
- js/
- data/
- docs/
- assets/
- README.md

## 3 Activar GitHub Pages

Ir a:

```
Settings → Pages
```

Seleccionar:

```
Deploy from branch
```

Elegir:

```
main / root
```

## 4 Acceder a la aplicación

La aplicación quedará disponible en:

```
https://TU-USUARIO.github.io/analizador-resultados-academicos
```

---

# Ventajas de esta solución

- No requiere instalación
- Funciona en cualquier sistema operativo
- Compatible con ordenadores del centro educativo
- Fácil de compartir mediante enlace
- Procesamiento local seguro

---

# Posibles mejoras futuras

- cálculo automático de **porcentajes**
- exportación de resultados a **Excel**
- exportación de **informes PDF**
- filtros por **evaluación**
- comparativa entre **cursos académicos**
- dashboard visual para análisis de resultados

---

# Licencia

Proyecto de uso educativo libre. Puede modificarse y adaptarse a las necesidades de cada centro educativo.
