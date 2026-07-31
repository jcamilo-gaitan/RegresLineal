# 🏘️ Análisis del Precio de Vivienda en Bogotá (2023)

**Pontificia Universidad Javeriana — Ciencia de Datos**

> Modelo de regresión lineal múltiple para predecir el precio de venta de inmuebles en Bogotá a partir de sus características socio demográficas.

**Autor:** Julian Camilo Gaitán Contreras

---

##  Objetivo del proyecto

Predecir el precio de un inmueble en venta en Bogotá con un modelo de regresión lineal múltiple que cumpla los supuestos clásicos del modelo.

## Proceso

1. **Análisis exploratorio:** limpieza de datos, tratamiento de nulos, revisión de correlaciones y colinealidad.
2. **Modelado iterativo:** modelo completo → transformaciónes en variables → modelo final con pesos (WLS), corrigiendo en cada paso los supuestos que fallaban.
3. **Exploración final:** análisis de variables confusoras, interacciones, observaciones influyentes y validación con datos de prueba.

##  Modelo final (Resultado)

```
log(precio) ~ estrato + log(área) + baños + garajes +
              elevadores + esCasa + zona_de_lavandería
```

(con pesos `1/log(área)²` para corregir heterocedasticidad)

- **R² ajustado:** 0.898
- ✅ Cumpliendo linealidad, homocedasticidad, independencia, normalidad y no presenta colinealidad problemática (VIF < 5).

## 💡 Principales hallazgos

- El **estrato** y el **área** son los factores más determinantes del precio.
- Baños, garajes y elevadores adicionales incrementan el precio de forma significativa.
- Tratar `estrato` como variable categórica (no numérica) fue clave para cumplir los supuestos.
- El modelo predice con un error promedio (MAPE) de ~12% en escala de precio real, sin evidencia de sobreajuste.
- Rango de predicción confiable: $85M – $1.530M COP.

##  Recomendaciones futuras para trabajos futuros con estos datos

- Recolectar más datos para mejorar significancia de variables marginales.
- Explorar interacciones adicionales (área × estrato).
- Acotar la región de predicción dada la concentración de precios en rangos bajos-medios.
