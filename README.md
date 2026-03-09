import sys
import pandas as pd
from PySide6.QtWidgets import (
    QApplication, QWidget, QPushButton, QFileDialog, QVBoxLayout,
    QLabel, QTableWidget, QTableWidgetItem, QComboBox
)
from matplotlib.backends.backend_qtagg import FigureCanvasQTAgg as FigureCanvas
from matplotlib.figure import Figure

class AnalizadorApp(QWidget):

    def __init__(self):
        super().__init__()
        self.setWindowTitle("Analizador de Resultados Académicos")
        self.resize(900,600)

        self.df = None
        self.resultados = None

        layout = QVBoxLayout()

        self.btn_cargar = QPushButton("Cargar Excel")
        self.btn_cargar.clicked.connect(self.cargar_excel)

        self.selector_nivel = QComboBox()
        self.selector_nivel.currentTextChanged.connect(self.mostrar_tabla)

        self.tabla = QTableWidget()

        self.fig = Figure()
        self.canvas = FigureCanvas(self.fig)

        layout.addWidget(QLabel("Archivo:"))
        layout.addWidget(self.btn_cargar)
        layout.addWidget(QLabel("Nivel:"))
        layout.addWidget(self.selector_nivel)
        layout.addWidget(self.tabla)
        layout.addWidget(self.canvas)

        self.setLayout(layout)

    def cargar_excel(self):
        ruta,_ = QFileDialog.getOpenFileName(self,"Seleccionar Excel","","Excel (*.xlsx *.xls)")
        if not ruta:
            return

        df = pd.read_excel(ruta)

        df["Alumno"] = df.iloc[:,4].astype(str)+" "+df.iloc[:,5].astype(str)+" "+df.iloc[:,6].astype(str)
        df["Etapa"] = df.iloc[:,10]
        df["Unidad"] = df.iloc[:,13]
        df["Materia"] = df.iloc[:,19]

        df["Nota"] = df.iloc[:,27]

        df["Nota"] = pd.to_numeric(df["Nota"],errors="coerce")

        df["Suspenso"] = df["Nota"] < 5

        suspensos = df.groupby(["Etapa","Unidad","Alumno"])["Suspenso"].sum().reset_index()

        def categoria(n):
            if n == 0:
                return "0"
            elif n <= 2:
                return "1-2"
            elif n <= 4:
                return "3-4"
            else:
                return "5+"

        suspensos["Categoria"] = suspensos["Suspenso"].apply(categoria)

        resumen = suspensos.groupby(["Etapa","Unidad","Categoria"]).size().unstack(fill_value=0)

        self.resultados = resumen

        niveles = resumen.index.get_level_values(0).unique()

        self.selector_nivel.clear()
        self.selector_nivel.addItems(niveles)

    def mostrar_tabla(self):
        nivel = self.selector_nivel.currentText()
        if not nivel:
            return

        datos = self.resultados.loc[nivel]

        self.tabla.setRowCount(len(datos))
        self.tabla.setColumnCount(len(datos.columns)+1)

        headers = ["Unidad"] + list(datos.columns)
        self.tabla.setHorizontalHeaderLabels(headers)

        for i,(unidad,row) in enumerate(datos.iterrows()):
            self.tabla.setItem(i,0,QTableWidgetItem(str(unidad)))
            for j,val in enumerate(row):
                self.tabla.setItem(i,j+1,QTableWidgetItem(str(val)))

        self.graficar(datos)

    def graficar(self,datos):
        self.fig.clear()
        ax = self.fig.add_subplot(111)

        datos.plot(kind="bar",ax=ax)

        ax.set_title("Comparación por unidades")
        ax.set_ylabel("Número de alumnos")

        self.canvas.draw()

if __name__ == "__main__":
    app = QApplication(sys.argv)
    ventana = AnalizadorApp()
    ventana.show()
    sys.exit(app.exec())

# README.md

## Analizador de Resultados Académicos

Aplicación de escritorio para **analizar resultados académicos a partir de un archivo Excel**. La herramienta permite agrupar materias por alumno, calcular suspensos y generar comparaciones por **nivel educativo y unidad** mediante tablas y gráficas.

La aplicación está pensada para **funcionar completamente offline** en Windows.

---

# Características

- Carga archivos **Excel (.xlsx o .xls)**
- Agrupa datos por:
  - Etapa (ej. "1º curso de ESO LOMLOE", "1º Bachillerato LOMLOE")
  - Unidad (1A, 1B, etc.)
- Identifica alumnos combinando columnas de nombre y apellidos
- Calcula número de **materias suspensas (nota < 5)**
- Clasifica alumnos en categorías:

| Categoría | Suspensos |
|---|---|
| 0 | Ningún suspenso |
| 1-2 | Entre 1 y 2 suspensos |
| 3-4 | Entre 3 y 4 suspensos |
| 5+ | 5 o más suspensos |

- Genera **tablas de resultados por unidad**
- Genera **gráficas comparativas entre unidades**
- Interfaz gráfica sencilla

---

# Estructura del Excel esperada

El programa utiliza columnas específicas del archivo Excel:

| Dato | Columna Excel |
|---|---|
| Nombre alumno | E |
| Apellido 1 | F |
| Apellido 2 | G |
| Etapa | K |
| Unidad | N |
| Materia | T |
| Nota | AB (posición usada actualmente en el script) |

Cada fila debe representar **una materia de un alumno**.

---

# Requisitos

Instalar Python 3.9 o superior.

Instalar dependencias:

```
pip install pandas matplotlib pyside6 openpyxl
```

---

# Ejecutar la aplicación

Desde la carpeta del proyecto:

```
python analizador_resultados_academicos_app.py
```

Se abrirá la interfaz gráfica.

1. Pulsar **Cargar Excel**
2. Seleccionar el archivo
3. Elegir el **nivel educativo** en el selector
4. Ver resultados y gráficas

---

# Crear ejecutable (.exe)

Para generar una aplicación descargable:

Instalar PyInstaller:

```
pip install pyinstaller
```

Crear ejecutable:

```
pyinstaller --onefile --windowed analizador_resultados_academicos_app.py
```

El archivo final aparecerá en:

```
dist/analizador_resultados_academicos_app.exe
```

Este archivo podrá ejecutarse **sin necesidad de instalar Python**.

---

# Funcionamiento del análisis

1. Se combinan las columnas de nombre y apellidos para identificar cada alumno.
2. Se detectan materias suspensas (nota < 5).
3. Se cuentan suspensos por alumno.
4. Cada alumno se clasifica en una categoría de suspensos.
5. Se agrupan resultados por:

```
Etapa → Unidad → Categoría de suspensos
```

6. Se generan tablas y gráficos comparativos.

---

# Posibles mejoras futuras

- Selección de **evaluación (1ª, 2ª, final)**
- Exportación automática a **Excel o PDF**
- Cálculo de **porcentajes automáticos**
- Dashboard con filtros por materia
- Comparación entre cursos académicos
- Edición manual de resultados

---

# Licencia

Uso educativo libre. Puede modificarse y adaptarse a las necesidades del centro educativo.

