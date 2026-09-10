# Compendio de Casos Prácticos en Diseño de Experimentos: DCA, Factoriales Fraccionados y ANCOVA

## 1. Título y Resumen
Implementación analítica y computacional en R para la resolución de diseños experimentales aplicados a la ingeniería, biotecnología y optimización de procesos (ANOVA, DBCA y ANCOVA).

## 2. Contexto y Pregunta de Investigación
¿Cómo aislar el efecto real de variables de tratamiento frente al ruido experimental o variables intervinientes (covariables) en contextos industriales y biológicos?

## 3. Casos de Estudio Incluidos
1. **Ejercicio 9.4:** DCA Unifactorial en Canales de Flujo (4 tratamientos, 4 repeticiones).
2. **Ejercicio 5.20:** DCA Unifactorial aplicado a Métodos de Extracción Química.
3. **Ejercicio 5.32:** Diseño Factorial Fraccionado ($2^{7-4}$) para analizar contracción en materiales elastómeros.
4. **Ejercicio 17.2:** DBCA con Covariable (ANCOVA) para contenido de Ácido Ascórbico en variedades de Haba.
5. **Ejercicio 17.7:** Diseño Factorial 3x2 en DBCA con ANCOVA en nutrición animal.

## 4. Metodología
- Planteamiento de pruebas de hipótesis ($H_0$ vs $H_1$).
- Construcción de Tablas ANOVA y modelos lineal generalizado con ajuste por covariable (`aov`).
- Análisis de residuos y validación de supuestos normativos.

## 5. Código y Demostración en R
```r
# Ejemplo de Ajuste ANCOVA (Ejercicio 17.2)
habas <- data.frame(
  Ascorbico = c(22.1, 24.3, 21.8, 25.0, 23.5, 26.1, 24.8, 25.5),
  Covariable = c(10.1, 11.2, 9.8, 12.0, 10.5, 11.8, 11.0, 11.5),
  Variedad = factor(rep(c("V1", "V2"), each = 4)),
  Bloque = factor(rep(1:4, times = 2))
)

modelo_172 <- aov(Ascorbico ~ Bloque + Variedad + Covariable, data = habas)
summary(modelo_172)
