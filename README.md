SIG-Gestion-Electrica-HN: Inteligencia de Negocios y Analítica Avanzada para el Sector Energético

[![GitHub License](https://img.shields.io/badge/License-Academic-blue.svg)]()
[![Power BI](https://img.shields.io/badge/Platform-Power%20BI%20Pro-yellow.svg)]()
[![Academic Level](https://img.shields.io/badge/Nivel-Maestría%20en%20Economía%20y%20Finanzas-darkblue.svg)]()

Este repositorio alberga el desarrollo completo del **Sistema de Información Gerencial (SIG)** enfocado en la Gestión Eléctrica Nacional de Honduras para el periodo quinquenal **2019-2023**. El proyecto ha sido estructurado como la entrega final para la asignatura *Sistemas de Información Gerencial* de la Vicerrectoría de Posgrados de la Universidad Metropolitana de Honduras (UMH).

---

🏛️ Contexto e Integración de Fuentes

La toma de decisiones en el subsector eléctrico nacional requiere la unificación de variables operativas puras con la realidad sociodemográfica del país. Este SIG rompe los silos de información tradicionales al consolidar una **Versión Única de la Verdad** mediante la integración de tres fuentes institucionales críticas:

1. **Comisión Reguladora de Energía Eléctrica (CREE):** Registros comerciales de abonados e infraestructura física a través del *Índice de Cobertura Eléctrica (ICE)*.
2. **Centro Nacional de Despacho (CND-ENEE) & EOR:** Flujos físicos masivos de inyección de carga y transacciones transfronterizas en el Mercado Eléctrico Regional (MER).
3. **Instituto Nacional de Estadística (INE):** Microdatos de servicios básicos residenciales procedentes de la *Encuesta Permanente de Hogares de Propósitos Múltiples (EPHPM)* y proyecciones poblacionales censales oficiales.

---

 ⚙️ Arquitectura del Modelo y Proceso ETL (Power Query)

Antes del despliegue visual, los datos en bruto fueron sometidos a una rigurosa auditoría de consistencia en Power Query. Un hallazgo crítico del proceso fue la detección de un falso positivo analítico en sistemas heredados denominado "brecha acumulada del sistema" (~11,820 unidades), ocasionado por un error metodológico de unidades cruzadas (operaciones aritméticas directas entre tasas porcentuales en escala `0-1` y volúmenes de carga en miles de `GWh`). Esta variable fue totalmente removida para asegurar la fiabilidad directiva.

 📈 Matriz Histórica Validada
El modelo semántico consolidado presenta las siguientes métricas clave homogeneizadas:

| Año | Demanda Total (GWh) | Importaciones MER (GWh) | Consumo Per Cápita (MWh/hab) | Acceso (IAE) [INE] | Cobertura (ICE) [CREE] | Coef. Dependencia |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **2019** | 10,154.90 | 100.02 | 0.47 | 0.87 | 0.85 | 0.56 |
| **2020** | 10,913.77 | 292.00 | 0.41 | 0.87 | 0.85 | 0.53 |
| **2021** | 11,118.25 | 204.48 | 0.46 | 0.88 | 0.86 | 0.55 |
| **2022** | 11,280.45 | 195.20 | 0.45 | 0.87 | 0.86 | 0.57 |
| **2023** | 11,969.08 | 148.64 | 0.46 | 0.88 | 0.86 | 0.61 |
| *Prom.* | *11,087.29* | *188.07* | *0.45* | *0.87* | *0.86* | *0.56* |

---

Cuadro de Mando Corporativo: 4 KPIs Estratégicos

Bajo principios de diseño de Business Intelligence (**UX/UI y patrón de lectura visual en "F"**), la interfaz gráfica prioriza la visualización de **exactamente 4 KPIs en tarjetas de alto formato**, evitando la saturación del usuario gerencial. Las variables sociodemográficas restantes (IAE e ICE) se integran directamente dentro de gráficos analíticos complejos de anillo y líneas dinámicas interactuando con Inteligencia Artificial.

 1. Demanda Total Anual (GWh)
* **Objetivo:** Monitorear la suficiencia y expansión física de la carga del sistema interconectado nacional.
* **Fórmula DAX:** `Demanda_Total = SUM(Historico[Demanda_GWh])`

2. Importaciones MER (GWh)
* **Objetivo:** Cuantificar la adquisición transfronteriza táctica de energía y optimizar costos marginales en el mercado mayorista.
* **Fórmula DAX:** `Importaciones_MER = SUM(Historico[Importaciones_GWh])`

 3. Consumo Eléctrico Per Cápita (MWh/hab)
* **Objetivo:** Evaluar la intensidad del uso del recurso energético promediado por habitante utilizando denominadores poblacionales oficiales del INE.
* **Fórmula DAX:** `Consumo_Per_Capita = [Demanda_Total] / MAX(Poblacion[Proyeccion_INE])`
 4. Coeficiente de Dependencia Externa (Adimensional)
* **Objetivo:** Salvaguardar la soberanía y seguridad energética regulando el nivel de exposición geopolítica ante fluctuaciones de precios externos.
* **Fórmula DAX:** `Dependencia_Externa = DIVIDE([Importaciones_MER], [Demanda_Total], 0)`

---

 🤖 Capa de Inteligencia Artificial Generativa

En alineación con las competencias de vanguardia de la maestría, se incorporaron capas operativas de **IA Generativa y Prompt Engineering** aplicadas a dos frentes de analítica avanzada:
* **Auditoría y consistencia física:** Modelos entrenados bajo rol de *Ingeniero de Datos Senior* para la detección temprana de anomalías en escalas numéricas.
* **Módulo narrativo inteligente:** Integración de cuadros de texto dinámicos nativos en Power BI que autogeneran conclusiones ejecutivas automatizadas (ej. *la identificación del comportamiento en forma de "U" del Consumo Per Cápita producto de la contracción industrial del 13.64% durante los confinamientos del 2020 y su posterior recuperación en 2023*).

---

📁 Estructura del Repositorio

El entorno técnico de soporte está indexado de la siguiente manera:
* 📁 `data/`: Matriz histórica de datos unificada en formato plano plano e interoperable (`.csv`).
* 📁 `src/`: Scripts y catálogo completo de medidas calculadas y fórmulas en lenguaje DAX.
* 📁 `dashboard/`: Plantilla del lienzo de visualización ejecutivo optimizado de Power BI (`.pbit`).
* 📄 `docs/`: Informe Técnico de Caso en formato académico bajo estrictas Normas APA 7ma Edición.

---

👤 Autoría y Soporte
**Desarrollador:** Lizdeny Amariliz Ruiz Estrada — *Maestranda en Economía y Finanzas, Universidad Metropolitana de Honduras.*
* **Asesor Académico:** Dr. Roy Arturo Mendieta Zúniga.
* **Fecha de Entrega:** Junio, 2026.
* **Desarrollador:** Lizdeny Amariliz Ruiz Estrada — *Maestranda en Economía y Finanzas, Universidad Metropolitana de Honduras.*
* **Asesor Académico:** Dr. Roy Arturo Mendieta Zúniga.
* **Fecha de Entrega:** Junio, 2026.
