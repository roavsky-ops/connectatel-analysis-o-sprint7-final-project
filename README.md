[README (1).md](https://github.com/user-attachments/files/31501918/README.1.md)
# Análisis ConnectaTel

## Objetivo del proyecto

Evaluar el comportamiento de los clientes de ConnectaTel, una empresa de telecomunicaciones en Latinoamérica, a partir de información registrada hasta el año 2024. El análisis busca construir un perfil estadístico de los clientes, detectar comportamientos atípicos y crear segmentos de clientes que permitan diseñar estrategias de retención y sugerir mejoras en los planes ofrecidos.

## Datasets utilizados

- **plans.csv**: información de los planes actuales (precio, minutos incluidos, GB incluidos, costo por extra).
- **users_latam.csv**: información de los clientes (edad, ciudad, fecha de registro, plan, fecha de baja/churn).
- **usage.csv**: detalle del uso real de los servicios (llamadas y mensajes, duración, longitud, fecha).

## Etapas del análisis

1. **Carga y exploración**: lectura de los tres datasets y revisión de su estructura (`.shape`, `.info()`).
2. **Identificación de problemas de calidad de datos**: revisión de valores nulos, detección de sentinels (`-999` en `age`, `"?"` en `city`) y estandarización de fechas (identificación de años imposibles).
3. **Limpieza básica de datos**: corrección de sentinels (imputación con mediana / `pd.NA`), corrección de fechas imposibles, y verificación de que los nulos en `duration`/`length` son MAR (dependen de la columna `type`).
4. **Summary statistics de uso por usuario**: agregación de `usage` por `user_id` (mensajes, llamadas, minutos) y combinación con la tabla de usuarios (`user_profile`).
5. **Visualización de distribuciones y outliers**: histogramas por plan y boxplots para identificar y evaluar valores atípicos mediante el método IQR.
6. **Segmentación de clientes**: creación de los segmentos `grupo_uso` (Bajo/Medio/Alto uso) y `grupo_edad` (Joven/Adulto/Adulto Mayor).
7. **Insight ejecutivo**: conclusiones accionables sobre problemas de datos, segmentos identificados y recomendaciones de negocio para ConnectaTel.

## Cómo ejecutar el notebook

1. Abre el archivo `.ipynb` en [Google Colab](https://colab.research.google.com/) o en un entorno Jupyter local.
2. Asegúrate de tener instaladas las librerías `pandas`, `seaborn` y `matplotlib`.
3. Coloca los archivos `plans.csv`, `users_latam.csv` y `usage.csv` en una carpeta `/datasets/` (o ajusta las rutas de carga en la primera celda de código según donde los tengas guardados).
4. Ejecuta las celdas en orden (`Run All` o celda por celda) desde el inicio del notebook.

## Guía de reproducción

Para reproducir el análisis completo desde cero:

```bash
# Clona este repositorio
git clone <URL_DE_ESTE_REPO>
cd <nombre-del-repo>

# Instala las dependencias necesarias
pip install pandas seaborn matplotlib jupyter

# Abre el notebook
jupyter notebook Analisis_ConnectaTel.ipynb
```

Luego, en el notebook, ajusta las rutas de los tres archivos CSV a la ubicación donde los hayas guardado y ejecuta todas las celdas en orden.
