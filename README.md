# Análisis de Ventas y Customer Insights con SQL

## Resumen Ejecutivo

Utilizando SQL como herramienta principal de análisis, se exploraron los datos de ventas de una empresa con el objetivo de identificar los principales impulsores de ingresos, patrones de compra y oportunidades de crecimiento.

A través de este análisis, se logró obtener visibilidad sobre el desempeño de productos, ciudades y clientes, así como sobre la evolución mensual de las ventas. Los hallazgos evidencian oportunidades claras para optimizar la retención de clientes, fortalecer mercados clave y mejorar la estabilidad de los ingresos.

Como resultado, se proponen estrategias enfocadas en:

1. Incrementar la fidelización de clientes de alto valor
2. Potenciar productos con mayor demanda
3. Expandir el rendimiento en ciudades clave
4. Reducir la volatilidad en los ingresos mensuales

---

## Problema Empresarial

El crecimiento sostenible de la empresa depende directamente de su capacidad para generar ingresos de manera constante y escalable. Sin embargo, existen señales de ineficiencia en la distribución de ventas, concentración de ingresos en pocos clientes y variabilidad significativa entre periodos.

Los stakeholders enfrentan el siguiente desafío:

- ¿Cómo identificar los principales factores que impulsan las ventas?
- ¿Qué clientes, productos y ciudades generan mayor valor?
- ¿Dónde existen oportunidades de crecimiento o riesgos de dependencia?
- ¿Cómo reducir la variabilidad en los ingresos y mejorar la predictibilidad del negocio?

Este proyecto busca responder estas preguntas mediante un análisis estructurado de datos que permita tomar decisiones estratégicas basadas en evidencia.

---

## Metodología

1. **Extracción y Transformación de Datos (SQL):** Se realizaron consultas SQL para limpiar, transformar y consolidar la información proveniente de múltiples tablas (ventas, clientes y productos), utilizando joins, agregaciones y funciones analíticas.
2. **Análisis Exploratorio de Datos:** Se calcularon métricas clave como:
    - Ventas totales
    - Ticket promedio
    - Ventas por producto
    - Ventas por ciudad
    - Clientes con mayor contribución
3. **Análisis de Tendencias Temporales:** Se evaluó el comportamiento mensual de las ventas mediante funciones de ventana (como `LAG`) para identificar patrones de crecimiento, caídas y volatilidad.
4. **Generación de Insights de Negocio:** A partir de los resultados obtenidos, se identificaron oportunidades estratégicas y se formularon recomendaciones orientadas a mejorar el rendimiento comercial y la toma de decisiones.

---

## Skills

#### **Lenguajes y herramientas:**

- SQL (nivel intermedio)

#### **Técnicas aplicadas:**

- Joins (INNER JOIN)
- Funciones de agregación (SUM, AVG)
- Funciones de ventana (LAG)
- Agrupaciones y ordenamiento de datos
- Transformación y limpieza de datos

#### **Análisis de datos:**

- Análisis de ventas
- Segmentación de clientes
- Identificación de patrones de consumo
- Análisis temporal (time series básico)
- Generación de insights accionables

## Resultados y Recomendaciones Empresariales

La construcción de un análisis en SQL para el seguimiento del rendimiento de ventas permitió obtener una visión clara sobre los principales impulsores de ingresos, el comportamiento de los clientes y los patrones de crecimiento de la empresa. Al centralizar esta información, los encargados pueden comprender mejor de dónde provienen los ingresos, quiénes son los clientes más valiosos y cómo evolucionan las ventas en el tiempo.

![Imagen1.jpg](https://github.com/LDanielaS/SQL-Sales-Analysis-Project/blob/b2042096f4b0224c4f39f5c4d5d7734030e94419/Imagen1.jpg)

Este análisis reveló que la empresa generó un ingreso total de **$77,903**, con un ticket promedio de **$259**, lo que indica un modelo de negocio basado en transacciones de valor medio a gran escala, en lugar de pocas ventas de alto valor.

Desde la perspectiva de productos, las ventas se encuentran relativamente distribuidas entre múltiples artículos, con los productos más vendidos alcanzando entre **8 y 16 unidades**. Esto sugiere un portafolio diversificado, lo que reduce la dependencia de un solo producto, pero también evidencia la ausencia de un “producto estrella” que impulse significativamente los ingresos.

A nivel geográfico, los ingresos están altamente concentrados en unas pocas ciudades clave. **Houston y San Antonio representan la mayor proporción de ventas**, seguidas por ciudades como Los Ángeles y Filadelfia. Esto indica un fuerte desempeño regional, pero también revela una oportunidad importante de expansión en mercados con menor rendimiento.

El análisis de clientes muestra que un grupo reducido concentra una parte significativa de los ingresos. El cliente principal generó más de **$11,000**, lo que confirma una distribución tipo **Pareto**, donde una minoría de clientes aporta la mayor parte de las ventas. Esto representa una oportunidad clara de fidelización, pero también un riesgo por dependencia.

Adicionalmente, el comportamiento mensual de las ventas presenta **alta volatilidad**, con incrementos y caídas pronunciadas entre periodos. Esto sugiere que los ingresos están influenciados por patrones de demanda inconsistentes, posiblemente relacionados con estacionalidad, campañas puntuales o falta de estrategias de retención.

---

### Conocimiento clave del Negocio

Las mayores oportunidades de crecimiento se encuentran en:

- Incrementar la retención de clientes
- Expandir los mercados con alto rendimiento
- Mejorar la estabilidad de los ingresos en el tiempo

---

### Recomendaciones Empresariales

Dado que el mayor impacto en ingresos provendrá de mejorar la retención de clientes, la expansión geográfica y la consistencia en el comportamiento de compra, se recomiendan las siguientes acciones estratégicas:

1. **Fortalecer la Retención de Clientes (Alto Impacto):** Identificar clientes de alto valor e implementar estrategias de fidelización como ofertas personalizadas, descuentos exclusivos o acceso anticipado a productos para aumentar la recurrencia de compra.
2. **Desarrollar una Estrategia de “Producto Estrella”:** Impulsar los productos más vendidos mediante campañas de marketing dirigidas y optimización de precios para convertirlos en los principales generadores de ingresos.
3. **Expandir Mercados de Alto Rendimiento:** Replicar las estrategias exitosas de ciudades como Houston y San Antonio en otras regiones mediante campañas localizadas y segmentación estratégica.
4. **Estabilizar los Ingresos Mensuales:** Implementar campañas mensuales constantes, modelos de suscripción o incentivos de compra recurrente que reduzcan la volatilidad y generen ingresos más predecibles.
5. **Incrementar el Ticket Promedio:** Aplicar estrategias de upselling y cross-selling, como paquetes de productos o descuentos por volumen, para incentivar un mayor gasto por transacción.

---

## Siguientes Pasos

- Crear dashboards para visualizar las ventas y facilitar la toma de decisiones.
- Aplicar estrategias de fidelización para clientes frecuentes.
- Potenciar los productos más vendidos con promociones.
- Implementar campañas para aumentar ventas en ciudades con bajo rendimiento.
