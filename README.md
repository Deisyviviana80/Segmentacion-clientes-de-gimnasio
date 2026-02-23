# 🏋️ Análisis de Cancelación de Clientes - Model Fitness

## Descripción del Proyecto

La cadena de gimnasios **Model Fitness** necesita desarrollar una estrategia de retención basada en datos. Este proyecto analiza los perfiles digitalizados de los clientes para predecir qué usuarios tienen mayor probabilidad de cancelar su membresía (*churn*) y proponer acciones concretas para retenerlos.

El proyecto fue desarrollado como parte del programa de formación en análisis de datos de **TripleTen**.

---

## 🎯 Objetivos

- Predecir la probabilidad de cancelación para el próximo mes para cada cliente.
- Segmentar clientes en grupos con comportamientos similares mediante clustering.
- Identificar los factores que más influyen en la cancelación.
- Proponer recomendaciones accionables por segmento para mejorar la retención.

---

## 🗂️ Dataset

| Archivo | Descripción |
|---------|-------------|
| `gym_churn_us.csv` | 4,000 registros con 14 variables de comportamiento y perfil de clientes |

**Variable objetivo:** `Churn` (1 = canceló, 0 = permaneció)

**Variables predictoras principales:** `Contract_period`, `Lifetime`, `Avg_class_frequency_current_month`, `Avg_class_frequency_total`, `Group_visits`, `Partner`, `Promo_friends`, entre otras.

---

## 🔍 Hallazgos Principales

### Factores más asociados a la cancelación

| Factor | Correlación con Churn | Interpretación |
|--------|-----------------------|----------------|
| Frecuencia de clases (último mes) | -0.44 | La caída reciente en asistencia es el predictor más fuerte |
| Frecuencia histórica de clases | -0.41 | Baja asistencia acumulada = mayor riesgo |
| Antigüedad del cliente | -0.41 | Los clientes nuevos son los más vulnerables |
| Duración del contrato | -0.39 | Contratos cortos se asocian con mayor cancelación |

### Modelos de Predicción

| Modelo | Exactitud | Precisión | Recall |
|--------|:---------:|:---------:|:------:|
| Regresión Logística | **0.92** | **0.87** | 0.78 |
| Bosque Aleatorio | 0.91 | 0.85 | 0.78 |

**Modelo seleccionado: Regresión Logística** — mejor desempeño y mayor interpretabilidad.

### Segmentación de Clientes (K-Means, 5 clústeres)

| Clúster | Perfil | Tasa de cancelación |
|---------|--------|:-------------------:|
| 0 | Contratos cortos, baja asistencia, poca antigüedad | 🔴 ~59% |
| 1 | Contratos medios, participación moderada | 🟠 Alta |
| 2 | Contratos largos, alta frecuencia, mayor gasto adicional | 🟢 Baja |
| 3 | El grupo más leal — contratos largos y mayor antigüedad | 🟢 Muy baja |
| 4 | Contratos cortos, bajo uso de promociones | 🟡 Moderada |

---

## 💡 Recomendaciones Estratégicas

**Para grupos de alto riesgo (Clústeres 0 y 1):**
- Ofrecer descuentos para migrar de contratos mensuales a trimestrales o anuales.
- Implementar alertas automáticas cuando la asistencia cae en el último mes.
- Reforzar el acompañamiento durante los primeros 3 meses de membresía.

**Para clientes estables (Clústeres 2 y 3):**
- Programas de lealtad con beneficios exclusivos por permanencia.
- Incentivar la promoción "trae a un amigo" (`Promo_friends`), que se asocia positivamente con la retención.

**Estrategias transversales:**
- Ampliar la oferta de clases grupales — `Group_visits` reduce la probabilidad de cancelación.
- Usar el canal telefónico para campañas de retención (90% de clientes tienen teléfono registrado).

---

## 🛠️ Tecnologías Utilizadas

- **Python 3**
- **pandas** — manipulación y análisis de datos
- **scikit-learn** — modelos de clasificación (Regresión Logística, Bosque Aleatorio) y clustering (K-Means)
- **scipy** — clustering jerárquico y dendrograma
- **matplotlib / seaborn** — visualización de datos
- **Jupyter Notebook** — entorno de desarrollo

---

## 📁 Archivos del Repositorio

```
📦 gym-churn-model-fitness
 ┣ 📓 Gym_Churn.ipynb          # Notebook principal con el análisis completo
 ┣ 📄 gym_churn_us.csv         # Dataset de clientes
 ┗ 📄 README.md                # Este archivo
```

---

## ▶️ ¿Cómo ejecutar el proyecto?

```bash
# Instalar dependencias
pip install pandas scikit-learn scipy matplotlib seaborn jupyter

# Abrir el notebook
jupyter notebook Gym_Churn.ipynb
```

---

## 👩‍💻 Autora

Proyecto desarrollado como parte del programa de **Análisis de Datos — TripleTen**.

**Deisy Viviana Hurtado Vega**
deisyviviana80@gmail.com

---

*Este repositorio forma parte de mi portafolio de proyectos de análisis de datos.*
