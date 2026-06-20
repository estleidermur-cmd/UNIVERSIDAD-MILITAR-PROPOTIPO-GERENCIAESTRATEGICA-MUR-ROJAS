## Tablero de Priorización de Causas

| Campo | Guía de diligenciamiento | Valor registrado |
|---|---|---|
| Causa | ¿Qué crees que está pasando 'detrás' del síntoma? Debe sonar a mecanismo, no a queja. | Falta de preparación para comprender el riesgo financiero y emocional antes de operar. |
| Fase DT origen (E/D/I) | ¿De qué momento de Design Thinking salió? | D + I |
| Insight de empatía | Una observación/cita corta que te inspiró la causa. | El usuario teme perder su capital, opera por impulso y reconoce que no cuenta con herramientas claras de gestión de riesgo ni control emocional. |
| Supuesto central | ¿Qué crees que une la causa con el resultado? Es la 'apuesta'. | Asumimos que si los traders novatos reciben formación estructurada en gestión de riesgo y psicología del trading antes de operar, disminuirán las pérdidas severas, el sobreapalancamiento y las decisiones impulsivas. |
| Pregunta analítica | Forma neutra y medible de la causa. Debe admitir 'Sí/No' o 'Mayor/Menor'. | ¿Los traders novatos que no reciben formación estructurada en gestión de riesgo presentan una mayor tasa de pérdida severa y mayor frecuencia de decisiones impulsivas que quienes sí reciben dicha formación? |
| Variables (nombres exactos) | Columnas que usarás tal cual aparecen en la base (no inventes nombres). | `formacion_riesgo_estructurada; drawdown_maximo; operaciones_impulsivas; episodios_sobreapalancamiento; tiempo_experiencia; capital_inicial` |
| Tipo (Outcome / Explic / Control / Segmento) | Etiqueta cada variable. 1. Outcome: lo que quieres explicar. 2. Explic (explicativa): lo que crees que causa. 3. Control: cosas que pueden distorsionar. 4. Segmento: variable para cortar resultados. | 1. Outcome: drawdown_maximo, operaciones_impulsivas, episodios_sobreapalancamiento.<br>2. Explic: formacion_riesgo_estructurada.<br>3. Control: tiempo_experiencia, capital_inicial.<br>4. Segmento: trader_novato (<12 meses). |
| Cálculo / Transformación | Operaciones necesarias antes de la métrica final. | 1) Codificar formacion_riesgo_estructurada (1=Sí, 0=No).<br>2) Crear variable perdida_severa = 1 si drawdown_maximo > 20%.<br>3) Calcular tasa de operaciones impulsivas por mes.<br>4) Segmentar solo traders novatos. |
| Métrica (nombre + fórmula) | Nombre corto +
