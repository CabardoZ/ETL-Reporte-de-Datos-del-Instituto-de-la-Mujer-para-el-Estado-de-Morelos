# Nota sobre los datos

Los archivos de datos originales (Excel, CSV y base de datos SQLite) **no están incluidos** en este repositorio por las siguientes razones:

1. **Privacidad** — Los archivos contienen información operativa de profesionistas de atención, sujeta a la Ley Federal de Protección de Datos Personales en Posesión de los Particulares.

2. **Confidencialidad institucional** — Los datos pertenecen al programa PAIMEF y son de uso interno de las unidades de atención.

## ¿Cómo usar este repositorio con tus propios datos?

Coloca tus archivos Excel en esta carpeta organizados por mes:

```
data/
└── raw/
    ├── 2023-05/
    │   ├── centro_1.xlsx
    │   └── centro_2.xlsx
    ├── 2023-06/
    └── ...
```

Luego actualiza la variable `CARPETA_RAIZ` en el notebook `ETL_PAIMEF_2023.ipynb` con la ruta a esta carpeta y ejecuta todas las celdas.
