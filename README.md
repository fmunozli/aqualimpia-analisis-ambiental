# Auditoría Analítica de Desempeño Operacional y Calidad de Efluentes — AquaLimpia S.A.

## 1. Definición del Problema
La empresa AquaLimpia S.A. opera tres plantas de tratamiento de aguas residuales (Planta Centro, Planta Norte y Planta Sur), encargadas de depurar efluentes domésticos e industriales antes de su vertido a cuerpos receptores. Durante el último trimestre, se han registrado superaciones intermitentes en la Demanda Biológica de Oxígeno del efluente tratado ($\text{DBO}_{\text{salida}}$), poniendo en riesgo el cumplimiento del estándar legal establecido (límite máximo permitido de 30 mg/L) y generando vulnerabilidad regulatoria ante sanciones ambientales.

## 2. Objetivos del Proyecto

### 2.1 Objetivo General
Desarrollar un flujo analítico reproducible, modular y colaborativo para diagnosticar el comportamiento de los procesos depurativos en las tres plantas de tratamiento, identificar las causas de incumplimiento normativo y proveer reportes desacoplados para la toma de decisiones operacionales y ambientales.

### 2.2 Objetivos Específicos
1. Determinar el nivel de cumplimiento normativo global y desagregado por planta sobre un horizonte de 200 registros diarios.
2. Formular estimaciones inferenciales robustas mediante el cálculo de Intervalos de Confianza al 95% para la $\text{DBO}_{\text{salida}}$ empleando distribuciones t-Student.
3. Evaluar la influencia de las sobrecargas de caudal de entrada y carga orgánica ($\text{DBO}_{\text{entrada}}$, $\text{SST}_{\text{entrada}}$) sobre la pérdida de estabilidad biológica del efluente.
4. Cuantificar la relación lineal entre el suministro energético en aireación (kWh) y la tasa de generación de biomasa celular (lodos en kg/día).
5. Automatizar la exportación segmentada de métricas operativas y ambientales mediante artefactos tabulares en Excel y persistencia serializada en Joblib.

## 3. Preguntas de Investigación
* **PI-1:** ¿Presentan las plantas diferencias estadísticamente significativas en sus concentraciones medias de DBO de descarga, o el incumplimiento normativo es una condición transversal del sistema?
* **PI-2:** ¿Existe un umbral crítico de caudal hidráulico diario ($m^3/\text{día}$) por sobre el cual se desestabiliza la eficiencia depurativa y se transgrede la cota de 30 mg/L de DBO?
* **PI-3:** ¿El requerimiento de energía en los sopladores de aireación responde proporcionalmente a la producción de lodos decantados, o se observan ineficiencias de consumo en recintos particulares?
* **PI-4:** ¿La variable binaria de cumplimiento normativo está determinada exclusivamente por la DBO de salida o existen otros parámetros de control influyentes en el registro?

## 4. Metodología y Flujo del Proceso
El proyecto se ejecuta en cinco etapas trazables y reproducibles:
1. **Ingesta Inmutable:** Carga del archivo fuente `dataset_set_A_aguas_residuales.xlsx` (200 registros y 10 variables físico-químicas e ingenieriles).
2. **Auditoría de Calidad:** Verificación de 0 datos nulos, 0 duplicados y validación de rangos lógicos admisibles (pH entre 6.0 y 9.0).
3. **Cómputo Modular Externo:** Cálculo de descriptores y contrastes inferenciales (NumPy y SciPy) desacoplados en `funciones_analisis_aguas.py`.
4. **Visualización Integrada:** Creación de un dashboard exploratorio de cuatro paneles con Seaborn y Matplotlib.
5. **Reportabilidad Diferenciada y Persistencia:** Generación de `reporte_area_operaciones.xlsx`, `reporte_area_gestion_ambiental.xlsx` y serialización de indicadores con `Joblib`.

## 5. Síntesis de Resultados Obtenidos
* **Tasa de Cumplimiento Global:** Solamente un 22.5% de los días auditados se encuentran en estricto cumplimiento normativo (45 de 200 jornadas).
* **Desempeño Comparativo por Planta:**
  * **Planta Sur:** 29.63% de cumplimiento (16/54 días), DBO media de salida: 36.06 mg/L (IC 95%: [32.57, 39.55] mg/L).
  * **Planta Centro:** 22.67% de cumplimiento (17/75 días), DBO media de salida: 35.90 mg/L (IC 95%: [32.87, 38.93] mg/L).
  * **Planta Norte:** 16.90% de cumplimiento (12/71 días), DBO media de salida: 36.56 mg/L (IC 95%: [33.27, 39.85] mg/L).
* **Inferencia Estadística:** En todas las plantas, el límite inferior del intervalo de confianza al 95% supera los 30 mg/L, concluyendo que la transgresión ambiental es sistemática y estadísticamente significativa.
* **Correlación de Biomasa:** Se verificó una correlación directa y positiva entre la energía de aireación suministrada y la biomasa de lodos purgada.



# aqualimpia-analisis-ambiental
Proyecto analítico de desempeño operacional y ambiental en plantas de tratamiento de aguas residuales - AquaLimpia S.A.
