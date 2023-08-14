# Model card para NLPAuditRisk

### NLPAuditRisk - Modelo de Riesgo para Auditoría Médica

- **Nombre del Modelo**: NLPAuditRisk (Fine-tuned de 'roberta-base-biomedical-clinical-es')
- **Versión**: 1.0.0
- **Tipo de Modelo**: Modelo de lenguaje pre-entrenado y fine-tuneado para tareas de procesamiento de lenguaje natural.
- **Fecha de Creación**: Junio 2023.
- **Autores**: Valdazo,A; Gargano,P; Bartellini,N; Bernal,M; Bunge,M; Daquarti,G 
- **Modelo Base de Hugging Face**: 'roberta-base-biomedical-clinical-es'
- **URL del Modelo Base de Hugging Face**: https://huggingface.co/PlanTL-GOB-ES/roberta-base-biomedical-clinical-es

## Descripción

NLPAuditRisk es un modelo de inteligencia artificial que ha sido desarrollado mediante fine-tuning del modelo 'roberta-base-biomedical-clinical-es', el cual ha sido pre-entrenado específicamente en lenguaje biomédico y clínico en español. El propósito principal de este modelo fine-tuning es predecir el riesgo asociado a teleconsultas médicas a partir de texto ingresado, incluyendo epicrisis y detalles de tratamientos médicos.


## Arquitectura del Modelo:
El modelo NLPAuditRisk se basa en la arquitectura del modelo 'roberta-base-biomedical-clinical-es', que incluye capas de atención y otras técnicas avanzadas de procesamiento de lenguaje natural específicamente diseñadas para lenguaje biomédico y clínico en español.

## Datos y Metodología de Entrenamiento:

- **Conjunto de datos de entrenamiento**: El modelo ha sido fine-tuneado utilizando un conjunto de datos de teleconsultas médicas que incluye epicrisis y detalles de tratamientos médicos, previamente etiquetados con el riesgo asociado.
- **Tamaño del conjunto de datos**: Más de 100.000 registros de teleconsultas médicas.
- **Técnicas de preprocesamiento**: Se aplicaron técnicas de limpieza y preprocesamiento de texto específicas para la tarea de predicción de riesgo.
Método de Fine-tuning: Se utilizó la técnica de fine-tuning proporcionada por Hugging Face para ajustar los parámetros del modelo 'roberta-base-biomedical-clinical-es' a la tarea de predicción de riesgo en teleconsultas médicas.

## Funcionalidades Principales

- **Clasificación de Riesgo**: NLPAuditRisk clasifica el texto ingresado en dos categorías, "0" y "1", con sus respectivos scores, para indicar el nivel de riesgo asociado.

### Resultado de Clasificación

- Clase "0": La persona puede recibir asistencia remota.
- Clase "1": La persona es de riesgo y requiere atención presencial.

Primero, el modelo hace una predicción sobre el riesgo de la consulta. Luego, esa predicción se compara con lo que el médico decidió sobre el riesgo. Si no coinciden, significa que podría haber un problema y la consulta es marcada como sospechosa para una revisión manual por parte del auditor.

## Beneficios

NLPAuditRisk ayuda a los profesionales de la salud a identificar y categorizar registros y reclamaciones médicas, lo que les permite priorizar y realizar auditorías médicas de manera eficiente. Al automatizar la evaluación de riesgo, optimiza la asignación de recursos y mejora la eficacia general de las auditorías.

## Clasificación

NLPAuditRisk es un modelo de clasificación de texto y no realiza ninguna interpretación médica ni toma de decisiones clínicas. No debe utilizarse como sustituto de la atención médica directa. Por eso, no es considerado un dispositivo médico según FDA y The Medical Device Regulation (MDR).

## Principios de Operación

### Comunicación

El modelo utiliza una API REST para interactuar con otros sistemas de información. Se comunica a través de solicitudes HTTP POST enviadas al punto final "https://apis.umasalud.com/ai/risk_audit".

### Autenticación y Autorización

NLPAuditRisk implementa mecanismos de autenticación y autorización mediante claves generadas específicamente para cada usuario. Estas claves aseguran que solo los usuarios autorizados puedan acceder a la API REST y realizar operaciones.

### Puntos finales y Métodos HTTP

El modelo define puntos finales específicos a los que se accede mediante diferentes métodos HTTP. En el caso de NLPAuditRisk, se utiliza el método POST para enviar datos al punto final mencionado anteriormente.

### Manejo de Errores y Excepciones

El modelo gestiona los errores y excepciones que puedan surgir durante la interacción con la API REST de manera efectiva. Informa errores mediante códigos de estado HTTP estándar, lo que proporciona información adicional para depuración y resolución de problemas.

### Seguridad

Se implementan medidas de seguridad para proteger la integridad y confidencialidad de los datos. Esto incluye el uso de conexiones seguras con protocolos HTTPS y el monitoreo constante para detectar posibles vulnerabilidades.

### Documentación y Mantenimiento

NLPAuditRisk viene con una documentación completa que describe su funcionamiento y los principios de operación mencionados anteriormente. Se realiza un mantenimiento regular para garantizar su correcto funcionamiento y actualizaciones de acuerdo con las necesidades cambiantes del entorno de auditoría médica.

## Propósito Previsto

NLPAuditRisk tiene como objetivo asistir en los procesos de auditoría médica en el contexto de telemedicina, al predecir el riesgo asociado a partir de texto ingresado, como epicrisis y tratamientos. Esta herramienta de inteligencia artificial ayuda a los profesionales de la salud a priorizar y enfocar las auditorías de manera más eficiente y efectiva, automatizando la revisión de atenciones de teleconsulta y destacando las consultas sospechosas que requieren revisión manual.

## Indicaciones Médicas Exactas

NLPAuditRisk está indicado para su uso en situaciones donde se necesite predecir el riesgo a partir del texto ingresado, como epicrisis y tratamientos.

## Entorno de Uso Previsto

NLPAuditRisk está diseñado para su uso en diversos entornos de auditoría médica, incluyendo hospitales, clínicas y centros de atención médica. También es adecuado para su integración en soluciones de auditoría médica digital.

## Usuarios Previstos

NLPAuditRisk está diseñado para ser utilizado por profesionales de la salud involucrados en los procesos de auditoría médica.

## Riesgos del Uso

El uso de NLPAuditRisk conlleva ciertos riesgos que deben tenerse en cuenta. Estos incluyen:

1. Interpretación incorrecta de resultados: Los resultados de clasificación de NLPAuditRisk son predicciones basadas en el texto ingresado y pueden no ser completamente precisos. Se recomienda que los profesionales de la salud utilicen su juicio clínico y experiencia para tomar decisiones médicas adecuadas.

2. Privacidad y seguridad de los datos: NLPAuditRisk no proporciona anonimización de datos. Por lo tanto, se deben tomar medidas adecuadas para proteger la confidencialidad de la información médica ingresada.

## Limitaciones de los Resultados Esperados

Es importante tener en cuenta las limitaciones en cuanto a los resultados esperados al utilizar NLPAuditRisk. Estas limitaciones incluyen:

1. Complejidad de las condiciones médicas: Las condiciones médicas pueden ser complejas y diversas, y NLPAuditRisk puede no abordar todos los aspectos o matices de cada situación clínica única. Puede haber casos en los que la información ingresada no sea suficiente y se requieran evaluaciones adicionales.

2. Precisión y confiabilidad de la Predicción: Aunque se hacen esfuerzos para garantizar la precisión y confiabilidad de la predicción proporcionada por NLPAuditRisk, existen limitaciones inherentes en los modelos de lenguaje y el procesamiento del lenguaje natural.

## Condiciones de Uso Normales

Las condiciones de uso normales de NLPAuditRisk incluyen:

1. Acceso a una conexión a Internet estable: NLPAuditRisk requiere acceso a una conexión a Internet estable, ya que es un servicio basado en la nube.

2. Dispositivo compatible: NLPAuditRisk puede ser accedido a través de computadoras de escritorio, laptops, tablets o teléfonos inteligentes compatibles con la plataforma o aplicación utilizada para acceder al servicio.

3. Uso en un entorno privado y seguro: Para garantizar la confidencialidad de los datos del paciente, se recomienda utilizar NLPAuditRisk en un entorno privado y seguro.

4. Seguir las instrucciones y recomendaciones: Se deben seguir las instrucciones y recomendaciones proporcionadas por el proveedor de NLPAuditRisk para un uso seguro y óptimo del servicio.

Es esencial utilizar NLPAuditRisk de acuerdo con las condiciones establecidas para garantizar una experiencia de uso segura y efectiva.

## Datos de Prueba

Se utilizó el 30% del conjunto de datos de teleconsultas médicas, aproximadamente 30.000 registros, como datos de prueba para evaluar el modelo NLPAuditRisk. Estos datos incluyen epicrisis y detalles de tratamientos médicos y fueron cuidadosamente seleccionados para representar una muestra representativa del conjunto completo.

## Factores

Durante la evaluación del modelo NLPAuditRisk, se tuvieron en cuenta diversos factores para determinar su rendimiento en la predicción de riesgo en teleconsultas médicas. Estos factores incluyen la precisión, que mide la proporción de resultados verdaderos positivos respecto a los resultados positivos totales; el recall, que indica la proporción de resultados verdaderos positivos respecto a todos los casos positivos reales; y el F1-score, que es una medida armónica entre la precisión y el recall.

## Métricas

Las métricas de rendimiento utilizadas para evaluar el modelo NLPAuditRisk incluyen precisión, MCC y F1-score. Estas métricas proporcionan una visión integral del desempeño del modelo y permiten comprender su capacidad para clasificar correctamente las teleconsultas en las categorías de riesgo "0" y "1".

## Resultados

Durante la evaluación del modelo NLPAuditRisk con el conjunto de datos de prueba, se obtuvieron las siguientes métricas:

- Coeficiente de Correlación de Matthews (MCC): 0.9058
- Área bajo la Curva ROC (AUROC): 0.9853
- Área bajo la Curva PR (AUPRC): 0.9974
- Puntuación F1: 0.9842
- Precisión (ACC): 0.9842

## Nota

NLPAuditRisk es una herramienta de apoyo para los profesionales de la salud en el proceso de auditoría médica. Las predicciones de riesgo deben ser evaluadas y confirmadas por un profesional médico antes de determinar su categoría real.
