# Analizador de Resultados Académicos

Aplicación web que permite **analizar resultados académicos a partir de un archivo Excel**. Está diseñada para ejecutarse directamente desde **GitHub Pages**, sin necesidad de instalar Python ni ningún programa adicional.

La aplicación procesa los datos **localmente en el navegador**, por lo que los archivos Excel no se suben a ningún servidor.

---

# Características

- 📂 Carga archivos **Excel (.xlsx)**
- 🧮 Calcula automáticamente el número de **materias suspensas** por alumno
- 📊 Clasifica a los alumnos según número de suspensos
- 🏫 Agrupa resultados por **etapa** y **unidad**
- 📈 Genera **gráficas comparativas** entre unidades
- 🌐 Funciona directamente desde **GitHub Pages**
- 💻 Compatible con cualquier sistema operativo (Windows, Mac, Linux, Chromebook)

---

# Clasificación de suspensos

Se considera suspenso cualquier **nota inferior a 5**.

Los alumnos se agrupan en las siguientes categorías:

| Categoría | Número de suspensos |
|---|---|
| 0 | Ningún suspenso |
| 1-2 | Entre 1 y 2 suspensos |
| 3-4 | Entre 3 y 4 suspensos |
| 5+ | 5 o más suspensos |

---

# Estructura del Excel esperado

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

Cada fila debe representar:

**una materia de un alumno**.

---

# Estructura del proyecto

El repositorio debe contener estos archivos:

```
analizador-resultados-academicos
│
├── index.html
├── script.js
├── styles.css
└── README.md
```

---

# Descripción de los archivos

## index.html

Contiene la estructura principal de la aplicación:

- carga de archivo Excel
- selector de nivel educativo
- tabla de resultados
- gráfico comparativo

También incluye las librerías externas:

- **SheetJS (xlsx)** para leer archivos Excel
- **Chart.js** para generar gráficos

---

## script.js

Contiene toda la lógica de la aplicación:

1. Leer el archivo Excel
2. Agrupar materias por alumno
3. Calcular número de suspensos
4. Clasificar alumnos en categorías
5. Agrupar resultados por etapa y unidad
6. Generar tabla de resultados
7. Crear gráficos comparativos

---

## styles.css

Define el estilo visual de la aplicación:

- tipografía
- tabla de resultados
- espaciado

---

# Cómo usar la aplicación

1. Abrir la página web.
2. Seleccionar el archivo Excel mediante el botón de carga.
3. El sistema analizará automáticamente los datos.
4. Elegir el **nivel educativo** en el selector.
5. Consultar los resultados en la tabla y el gráfico.

---

# Publicar en GitHub Pages

## 1 Crear repositorio

Crear un repositorio en GitHub, por ejemplo:

```
analizador-resultados-academicos
```

## 2 Subir los archivos

Subir al repositorio:

```
index.html
script.js
styles.css
README.md
```

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
- Funciona en cualquier ordenador
- Compatible con dispositivos educativos
- Fácil de compartir mediante enlace
- Procesamiento local seguro

---

# Posibles mejoras futuras

- cálculo automático de **porcentajes**
- exportación de resultados a **Excel**
- exportación de **informes PDF**
- filtros por **evaluación**
- comparativa entre **cursos académicos**
- panel visual tipo **dashboard educativo**

---

# Licencia

Proyecto de uso educativo libre. Puede modificarse y adaptarse a las necesidades de cada centro educativo.
