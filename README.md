# PAIMEF 2023 — Portal de Datos Abiertos
### Atención a Mujeres en Situación de Violencia · Morelos

Pipeline ETL y dashboard de análisis para el procesamiento de informes mensuales de los Centros de Atención Externa (CAE) del programa PAIMEF en el estado de Morelos, periodo Mayo–Diciembre 2023.

---

## 📌 Descripción

Este proyecto transforma **91 archivos Excel** de reporte mensual (13 centros × 8 meses) en una base de datos estructurada y un dashboard interactivo para análisis de política pública.

Los datos incluyen:
- Atenciones a mujeres en situación de violencia
- Tipos y modalidades de violencia registradas
- Servicios brindados por área (Psicología, Trabajo Social, Asesoría Jurídica, Psicología Infantil)
- Perfil sociodemográfico de las usuarias
- Cobertura y desempeño por centro de atención

**Resultados del periodo:**
| Indicador | Total |
|---|---|
| Mujeres atendidas | 7,769 |
| Atenciones totales | 38,392 |
| Servicios de psicología | 15,586 |
| Asesorías jurídicas | 9,588 |
| Trabajo social | 7,366 |
| Psicología infantil | 7,614 |

---

## 🗂️ Estructura del repositorio

```
paimef-portal-datos/
├── ETL_PAIMEF_2023.ipynb       # Pipeline ETL completo
├── dashboard_paimef_2023.html  # Dashboard interactivo
├── README.md                   # Este archivo
├── .gitignore                  # Exclusiones de archivos sensibles
└── data/
    └── README.md               # Nota sobre privacidad de los datos
```

---

## ⚙️ Requisitos

- Python 3.8+
- Anaconda / Jupyter Notebook (recomendado)

Instalar dependencias:
```bash
pip install openpyxl pandas
```
O con conda:
```bash
conda install openpyxl pandas
```

---

## 🚀 Cómo usar

### 1. Clona el repositorio
```bash
git clone https://github.com/tu-usuario/paimef-portal-datos.git
cd paimef-portal-datos
```

### 2. Organiza tus archivos Excel
Coloca los archivos en carpetas por mes dentro de una carpeta raíz:
```
data_raw/
├── 2023-05/   ← archivos Excel de mayo
├── 2023-06/   ← archivos Excel de junio
├── ...
└── 2023-12/
```

### 3. Ejecuta el notebook
Abre `ETL_PAIMEF_2023.ipynb` en Jupyter y en la primera celda cambia la ruta:
```python
CARPETA_RAIZ = r"C:\ruta\a\tu\carpeta\data_raw"
```
Ejecuta todas las celdas. El notebook generará:
- `paimef_2023.db` — base de datos SQLite
- `PowerBI_CSVs/` — archivos CSV listos para Power BI

### 4. Consulta el dashboard
Abre `dashboard_paimef_2023.html` directamente en tu navegador. No requiere servidor.

---

## 📊 Conectar con Power BI

**Opción A — CSV (más simple):**
1. Ejecuta el notebook hasta la última celda
2. En Power BI: `Obtener datos → Texto/CSV`
3. Importa los archivos de la carpeta `PowerBI_CSVs/`

**Opción B — ODBC directo:**
1. Instala [SQLite ODBC Driver](http://www.ch-werner.de/sqliteodbc/)
2. Crea un DSN llamado `PAIMEF2023` apuntando a `paimef_2023.db`
3. En Power BI: `Obtener datos → ODBC → PAIMEF2023`

---

## 🗄️ Estructura de la base de datos

| Tabla / Vista | Descripción |
|---|---|
| `concentrado` | Tabla principal — 725 filas, 86 variables |
| `tipos_modalidades` | Cruce tipo × modalidad de violencia |
| `v_resumen_mensual` | Agregados por mes |
| `v_por_centro` | Agregados por centro |
| `v_violencia_tipo_mes` | Evolución de tipos de violencia |
| `v_perfil_global` | Perfil sociodemográfico acumulado |

---

## 🔒 Privacidad y datos

Los archivos Excel originales **no están incluidos** en este repositorio. Contienen información operativa de las unidades de atención que está sujeta a la **Ley Federal de Protección de Datos Personales en Posesión de los Particulares** y la **Ley General de Acceso de las Mujeres a una Vida Libre de Violencia**.

Este repositorio contiene únicamente el código del pipeline ETL y el dashboard, diseñados para ser reutilizados con datos propios.

---

## 🛠️ Tecnologías

- **Python** — procesamiento y ETL
- **Pandas** — transformación de datos
- **openpyxl** — lectura de archivos Excel
- **SQLite** — base de datos local
- **Chart.js** — visualizaciones del dashboard
- **Power BI** — análisis y reportes institucionales

---

## 📄 Licencia

MIT License — libre para usar, modificar y distribuir con atribución.

---

## ✉️ Contacto

Proyecto desarrollado en el marco del análisis de datos del programa PAIMEF, Morelos 2023.
