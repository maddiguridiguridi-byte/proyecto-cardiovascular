# Factores de Riesgo en la Enfermedad Cardiovascular
**Autora:** Maddi Guridi  
**Herramienta:** Google Sheets  
**Módulo:** Dashboard & Análisis de Datos

---

## 📋 Descripción del proyecto

Análisis exploratorio de un conjunto de datos de pacientes con el objetivo de identificar los principales factores de riesgo asociados a la enfermedad cardiovascular (ECV). El análisis cubre las fases de limpieza de datos, análisis descriptivo y visualización mediante dashboard.

---

## 📂 Estructura del repositorio

```
├── README.md
├── data/
│   └── cardio_train.csv        # Dataset original
└── links.md                    # URLs de Google Sheets y Kaggle
```

---

## 🗃️ Fuente de datos

- **Dataset:** Cardiovascular Disease Dataset
- **Origen:** [Kaggle - sulianova/cardiovascular-disease-dataset](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset)
- **Google Sheets:** [Enlace al proyecto](https://docs.google.com/spreadsheets/d/16LFHKPfh4PmMe6BukslBVJuBvovpvySM8XG6_6e7kaQ/edit?gid=1922681534#gid=1922681534)
- **Registros originales:** 70.000 filas
- **Variables:** 13 columnas

### Variables del dataset

| Variable | Descripción |
|---|---|
| id | Identificador del paciente |
| age | Edad en días (convertida a años) |
| gender | Género (1=Mujer, 2=Hombre) |
| height | Altura en cm |
| weight | Peso en kg |
| ap_hi | Presión arterial sistólica (mmHg) |
| ap_lo | Presión arterial diastólica (mmHg) |
| cholesterol | Colesterol (1=Normal, 2=Alto, 3=Muy alto) |
| gluc | Glucosa (1=Normal, 2=Alta, 3=Muy alta) |
| smoke | Fumador (0=No, 1=Sí) |
| alco | Consumo de alcohol (0=No, 1=Sí) |
| active | Actividad física (0=No, 1=Sí) |
| cardio | Enfermedad cardiovascular (0=No, 1=Sí) |

---

## 🧹 Limpieza y transformación de datos

Se eliminaron un total de **1.009 registros con valores fisiológicamente imposibles**:

| Criterio | Filas eliminadas |
|---|---|
| Presión sistólica > 300 mmHg | 40 |
| Presión diastólica > 200 mmHg | 953 |
| Presión sistólica < 0 mmHg | 1 |
| Presión diastólica < 5 mmHg | 15 |
| Altura < 110 cm o > 220 cm | 40 |
| **Total eliminadas** | **1.069** |
| **Dataset final** | **68.932 registros** |

### Transformaciones realizadas

- Edad convertida de días a años mediante la fórmula `=REDONDEAR(age/365;0)`
- Variables categóricas numéricas traducidas a etiquetas legibles en español (género, colesterol, glucosa, tabaquismo, alcohol, actividad física y ECV)
- Columnas renombradas para mayor claridad (ap_hi → presion_sis, ap_lo → presion_dias, etc.)

---

## 📊 Análisis descriptivo

El dataset presenta un equilibrio casi perfecto entre pacientes con ECV (49,5%) y sin ECV (50,5%).

### ECV por género
- El dataset está compuesto por un 65% de mujeres y un 35% de hombres
- Los hombres presentan una prevalencia de ECV ligeramente mayor (50,02%) frente a las mujeres (49,21%)
- En números absolutos, las mujeres representan el 64,76% de los casos de ECV

### ECV por edad

| Rango de edad | Prevalencia de ECV |
|---|---|
| 30-34 años | 0% |
| 35-39 años | 21,3% |
| 40-44 años | 29,5% |
| 45-49 años | 43,0% |
| 50-54 años | 45,2% |
| 55-59 años | 54,9% |
| 60-65 años | 65,7% |

### ECV por colesterol

| Nivel | Prevalencia de ECV |
|---|---|
| Normal | 43,6% |
| Alto | 59,7% |
| Muy alto | 76,3% |

### ECV por glucosa

| Nivel | Prevalencia de ECV |
|---|---|
| Normal | 47,6% |
| Alta | 58,9% |
| Muy alta | 61,8% |

### Presión arterial media

| Grupo | Presión sistólica | Presión diastólica |
|---|---|---|
| Sin ECV | 119,3 mmHg | 78,2 mmHg |
| Con ECV | 133,5 mmHg | 84,6 mmHg |

### ECV por actividad física
- Pacientes sedentarios: 53,3% con ECV
- Pacientes activos: 48,6% con ECV

---

## 📈 Dashboard

El dashboard incluye:
- **2 KPIs:** Total pacientes analizados (68.932) y % pacientes con ECV (49,5%)
- **6 gráficos:** ECV por género, ECV por edad, ECV por colesterol, ECV por glucosa, ECV por actividad física y Presión arterial media con/sin ECV

🔗 [Ver dashboard en Google Sheets](https://docs.google.com/spreadsheets/d/16LFHKPfh4PmMe6BukslBVJuBvovpvySM8XG6_6e7kaQ/edit?gid=1922681534#gid=1922681534)

---

## 🏁 Conclusiones

Los factores de riesgo con mayor asociación a la enfermedad cardiovascular identificados en este análisis son:

✅ **Edad avanzada** — factor más determinante. A partir de los 55 años más de la mitad de los pacientes presenta ECV  
✅ **Colesterol elevado** — relación dosis-respuesta clara: a mayor colesterol, mayor riesgo  
✅ **Glucosa elevada** — misma tendencia que el colesterol  
✅ **Hipertensión arterial** — los pacientes con ECV presentan una presión media en rango de hipertensión grado 1  
✅ **Sedentarismo** — los pacientes inactivos presentan mayor prevalencia de ECV  

Los resultados relacionados con el tabaco y el alcohol no son coherentes con la evidencia clínica, lo que sugiere un sesgo en la recogida de estos datos en el dataset original.

Este análisis demuestra el valor de las herramientas de análisis de datos para identificar patrones clínicos relevantes, aportando información útil tanto para la prevención como para la gestión de la enfermedad cardiovascular.
