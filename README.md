[Ver bloque de código 2] — Experimento analítico mínimo

Prueba piloto con traders novatos segmentados por presencia de revenge_trading (no por formación), comparando perdida_severa entre ambos grupos.

```sql
SELECT trader_id, COUNT(*) AS operaciones_perdida_severa FROM operaciones WHERE drawdown > 0.20 AND segmento = 'novato' GROUP BY trader_id, revenge_trading;
```

Visual: barras comparativas (% perdida_severa por grupo revenge_trading) + tabla de riesgo relativo.

---

## Contexto y Objetivo del Indicador

| Supuesto central | ¿QUÉ HAGO? (Acción) | ¿CÓMO LO HAGO? (Método) | ¿PARA QUÉ LO HAGO? (Propósito) | Aspecto específico a medir |
|---|---|---|---|---|
| Asumimos que el mecanismo de sesgo cognitivo post-pérdida (aversión a la pérdida y frustración acumulada) explica una parte significativa de las pérdidas severas en traders novatos, y que interrumpir ese mecanismo -mediante formación estructurada, alertas de fricción en tiempo real u otras intervenciones- disminuiría dichas pérdidas, el sobreapalancamiento y las decisiones impulsivas. No se asume de antemano cuál intervención es la correcta (Principio 1 del Pentálogo: no enamorarse de la solución). | Medir y monitorear la tasa de pérdida severa en traders novatos, segmentando por presencia del mecanismo de sesgo (revenge trading, variación del lotaje bajo estrés) y por formación recibida. | Mediante el cálculo mensual de drawdown máximo, tiempo entre operaciones tras una pérdida y variación del lotaje, cruzando el historial de operaciones de la plataforma/broker con el journal del trader como fuente complementaria -no única-, dado su carácter voluntario. | Para determinar si el mecanismo de sesgo cognitivo post-pérdida explica la pérdida severa y la impulsividad operativa (definida operacionalmente en el Paso 3 como revenge trading y variación del lotaje bajo estrés) en traders novatos, y así orientar con evidencia el diseño de intervenciones -formativas o de interfaz-, sin asumir de antemano cuál es la correcta. | La proporción de traders novatos que presentan pérdida severa (drawdown máximo >20%) en el periodo, segmentada por presencia de revenge trading y por formación recibida. |

## Construcción Técnica del Indicador

| Público objetivo (Para quién) | Dimensión (Marca una) | Nombre del indicador | Numerador (Variable Y) | Denominador (Población) | Fórmula (Matemática) | Prueba de estrés | Tipo (Marca una) | Frecuencia de medición |
|---|---|---|---|---|---|---|---|---|
| Traders novatos con menos de 12 meses de experiencia en trading digital. | Eficacia (¿logra el resultado?) | **Tasa de pérdida severa en traders novatos** | Número de traders novatos con drawdown máximo superior al 20% en el periodo (perdida_severa = 1). | Total de traders novatos evaluados en el mismo periodo; puede segmentarse por formación recibida o por presencia de revenge trading sin cambiar la definición del indicador. | [Ver bloque de código 3] | Si no hay registro confiable de drawdown, el indicador pierde validez. Si el número de traders observados es muy pequeño, el resultado puede sesgarse. También falla si no se distingue entre cuenta demo y cuenta real. Adicionalmente: el journal del trader es un registro voluntario y suele subregistrar operaciones perdedoras por vergüenza o frustración, por lo que no debe usarse como fuente única -debe cruzarse con el historial de la plataforma/broker-; y la volatilidad del mercado durante el piloto y el capital inicial de la cuenta deben registrarse como variables de control, pues distorsionan el drawdown observado (las cuentas pequeñas se queman más rápido). | Tasa (%) | Mensual, con corte consolidado trimestral. |



[Ver bloque de código 3] — Fórmula (Matemática)
