# Analizador de Resultados Académicos

Aplicación web que permite **analizar los resultados académicos del alumnado a partir de un archivo Excel**. La herramienta calcula automáticamente el número de suspensos por alumno, agrupa los resultados por nivel educativo y unidad, y muestra los datos mediante tablas y gráficos.

La aplicación está diseñada para ejecutarse directamente desde **GitHub Pages**, por lo que no requiere instalar ningún programa. Solo necesitas abrir la página web y cargar el archivo Excel.

Todos los datos se procesan **localmente en el navegador**, por lo que el archivo Excel no se sube a ningún servidor.

---

# Requisitos

Para usar esta aplicación solo necesitas:

- Un navegador web moderno (Chrome, Edge, Firefox, Safari)
- Un archivo Excel con los datos del alumnado

No es necesario instalar Python ni ningún software adicional.

---

# Estructura del repositorio

El repositorio debe contener los siguientes archivos y carpetas:

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

### Archivos principales

**index.html**  
Contiene la interfaz de la aplicación y carga los scripts necesarios.

**js/script.js**  
Contiene la lógica del programa:

1. Leer el archivo Excel
2. Agrupar materias por alumno
3. Calcular número de suspensos
4. Clasificar alumnos
5. Agrupar resultados por etapa y unidad
6. Generar tabla de resultados
7. Crear gráficos

**css/styles.css**  
Define el diseño visual de la página.

---

# Formato del archivo Excel

El Excel debe contener las siguientes columnas (según posición):

| Dato | Columna Excel |
|---|---|
| Nombre | E |
| Apellido 1 | F |
| Apellido 2 | G |
| Etapa | K |
| Unidad | N |
| Materia | T |
| Nota final | AB |

Cada fila debe representar **una materia de un alumno**.

El sistema agrupa automáticamente las materias para calcular el número total de suspensos por alumno.

Se considera suspenso cualquier **nota inferior a 5**.

---

# Clasificación de alumnado

Los alumnos se agrupan según el número de suspensos:

| Categoría | Suspensos |
|---|---|
| 0 | Ningún suspenso |
| 1-2 | Entre 1 y 2 suspensos |
| 3-4 | Entre 3 y 4 suspensos |
| 5+ | 5 o más suspensos |

---

# Cómo publicar la aplicación en GitHub

## 1. Crear un repositorio

Crear un repositorio en GitHub con el nombre:

```
analizador-resultados-academicos
```

---

## 2. Subir los archivos

Subir al repositorio todos los archivos del proyecto:

- index.html
- carpeta css
- carpeta js
- carpeta data
- carpeta docs
- carpeta assets
- README.md

La estructura debe quedar exactamente como se muestra en la sección **Estructura del repositorio**.

---

## 3. Activar GitHub Pages

1. Ir al repositorio en GitHub.
2. Abrir la pestaña **Settings**.
3. Ir a **Pages**.
4. En "Source" seleccionar:

```
Deploy from a branch
```

5. Seleccionar:

```
Branch: main
Folder: /root
```

Guardar los cambios.

---

## 4. Abrir la aplicación

Después de activar GitHub Pages, la aplicación estará disponible en una dirección similar a:

```
https://TU-USUARIO.github.io/analizador-resultados-academicos
```

Al abrir la página:

1. Selecciona el archivo Excel.
2. El sistema analizará automáticamente los datos.
3. Selecciona el nivel educativo.
4. Consulta los resultados en la tabla y en el gráfico.

---

# Cómo usar la aplicación

1. Abrir la página web de la aplicación.
2. Pulsar en **Seleccionar archivo**.
3. Elegir el Excel con los datos del alumnado.
4. El sistema procesará los datos automáticamente.
5. Elegir el nivel educativo en el selector.
6. Ver los resultados en la tabla y en el gráfico.

---

# Ventajas de esta solución

- No requiere instalación
- Funciona en cualquier ordenador
- Compatible con equipos del centro educativo
- Puede compartirse mediante enlace
- Procesamiento local seguro

---

# Posibles mejoras futuras

- cálculo automático de porcentajes
- exportación de resultados a Excel
- generación automática de informes PDF
- filtros por evaluación
- comparativa entre cursos académicos
- panel visual tipo dashboard educativo

---

# Licencia

Proyecto de uso educativo libre. Puede modificarse y adaptarse a las necesidades de cada centro edu
