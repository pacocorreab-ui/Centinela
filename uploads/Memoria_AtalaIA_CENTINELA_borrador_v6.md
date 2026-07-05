# MEMORIA DEL PROYECTO

## Premios de la Cátedra de Ciberseguridad a la Innovación en Ciberseguridad e Inteligencia Artificial — Universidad de Málaga

---

# CENTINELA — Seguridad desde el diseño para la IA del licitador

*La capa de confianza del proyecto AtalaIA Licit@: proteger la información que las PYMEs confiarán a una plataforma de análisis de licitaciones públicas con inteligencia artificial*

**Equipo solicitante:**
- **Francisco Andrés Correa Barrera** — fundador del proyecto AtalaIA Licit@, responsable del proyecto y representante del equipo. Ingeniero Civil e Ingeniero de Organización Industrial, Senior Project Engineer & Applied Innovation. Antiguo alumno de la UMA (Máster Interuniversitario RDIA, 2023).
- **Mario Quintana Simonet** — partner estratégico técnico. Estudiante de último curso del Grado en Ingeniería de Telecomunicaciones, especialidad en Sonido e Imagen (UMA, ETSIT), con todas las asignaturas superadas y TFG en curso. Matrícula UMA del curso académico 2025/2026 acreditada en la documentación de la solicitud.

---

## 1. Resumen ejecutivo

Las administraciones públicas españolas ya utilizan inteligencia artificial para evaluar ofertas: la Junta de Andalucía recibió en 2025 el Premio Nacional CíES por ASICÓN, su sistema de IA de apoyo a las Mesas de Contratación. Del lado de quien licita, esa capacidad hoy solo está al alcance de las grandes empresas —Ineco, Acciona, Sener, Indra—, que cuentan con departamentos de análisis propios. Las PYMEs de ingeniería, que compiten por los mismos contratos, siguen leyendo pliegos de 50 a 200 páginas a mano.

**AtalaIA Licit@** nace para cerrar esa brecha: una plataforma de inteligencia para el licitador que analiza los pliegos, ayuda a decidir con criterio si presentarse o no, y convierte la experiencia de cada licitación en conocimiento acumulado de la empresa. El proyecto está en fase de preincubación: existe una metodología validada en entorno profesional real durante 2025–2026 —con reducción del análisis preliminar de 2–4 horas a unos 15 minutos por pliego— y un plan de negocio completo. La plataforma, como software, no existe todavía.

Y ahí está la razón de ser de este proyecto: **antes de construir la plataforma hay que resolver su problema de confianza, que es un problema de ciberseguridad.**

Para funcionar de verdad, una plataforma así necesita que las empresas le confíen su información más sensible: sus ofertas técnicas, sus precios, su historial de contratos ganados y perdidos. Es la información que un competidor pagaría por conocer. Si esa información no está bien protegida —al guardarla, al analizarla con servicios de IA de terceros, al compararla con la de otras empresas—, la plataforma no solo sería insegura: sería inviable como negocio, porque ninguna PYME confiaría en ella. La seguridad no es aquí un requisito técnico añadido; es la condición para que el producto pueda existir.

**CENTINELA es el diseño y la construcción de esa capa de protección, antes de escribir la primera línea de la plataforma.** Durante julio y agosto de 2026, en GSEC Málaga y con la mentoría de profesionales de Google, el equipo construirá un prototipo que demuestre cuatro cosas: (1) que los documentos entran al sistema de forma segura, comprobando que son auténticos y que no traen ficheros dañinos ni contenido oculto; (2) que la información de cada empresa se guarda cifrada y separada, y que solo sale hacia los servicios de IA lo estrictamente necesario, con registro de todo lo que sale; (3) que cuando se compara información entre empresas, nadie puede averiguar de qué empresa procede cada dato —y que eso se comprueba intentando romperlo, no solo prometiéndolo—; y (4) el diseño de cómo dos empresas podrán compartir un análisis para preparar juntas una oferta (UTE) sin ver los datos privados de la otra. Sobre esa base segura, el prototipo ejecuta la función que da valor al negocio: el análisis del pliego y el informe de decisión GO/NO-GO.

El resultado mínimo comprometido es un prototipo funcional demostrable de principio a fin, incluyendo la detección en vivo de un fichero malicioso de prueba y la demostración de que el sistema de anonimizado resiste los intentos de reidentificación del propio equipo.

---

## 2. Problema que se pretende resolver

### 2.1 El problema de las PYMEs: competir a ciegas contra quien ve

Cada vez que una PYME de ingeniería decide presentarse a una licitación pública compromete entre 100 y 200 horas de técnicos cualificados en preparar la oferta, tras un análisis preliminar de 2–4 horas por pliego que se pierde por completo si la decisión final es no presentarse. La empresa decide con información incompleta, no mide su tasa real de adjudicación, y el conocimiento generado en cada proceso —ganado o perdido— se archiva sin convertirse en un activo que sirva para la siguiente.

Las grandes empresas tienen departamentos que hacen ese trabajo de forma sistemática. Las administraciones ya evalúan con IA. La PYME está en medio, compitiendo con menos información que ambas. El resultado es una tasa de conversión baja, margen destruido por competir solo en precio, y un reparto de la contratación pública cada vez más concentrado en los grandes actores.

Una plataforma de inteligencia accesible para la PYME —"la IA del licitador"— cambia esa ecuación: democratiza una capacidad que hoy es privilegio de pocos, mejora la calidad de las decisiones y de las ofertas, y con ello la tasa de conversión de las empresas medianas. Más contratos ganados por PYMEs significa más empleo técnico cualificado en esas empresas y un reparto más equilibrado del mercado público. Ese es el impacto que persigue AtalaIA Licit@.

### 2.2 El problema de seguridad: esa plataforma custodiará secretos industriales

Lo que condiciona todo lo anterior es una pregunta que las plataformas emergentes de esta categoría no han puesto en el centro: **¿qué pasa con la información que las empresas confían al sistema?**

Para aprender del historial de cada cliente y ayudarle a mejorar, la plataforma necesita ingerir su documentación privada: ofertas técnicas completas, desgloses económicos, resoluciones, memorias internas. Exactamente la información que la propia normativa de contratos trata como confidencial. De ahí se derivan cuatro riesgos concretos, en lenguaje llano:

1. **Riesgo de robo o filtración.** Reunir el historial de ofertas y precios de decenas de empresas en un mismo sistema crea un objetivo muy atractivo. Una brecha no expondría datos personales corrientes: expondría la estrategia comercial de los clientes, con un daño directo e irreparable.
2. **Riesgo de fuga a través de los servicios de IA.** Analizar documentos con modelos de lenguaje implica enviar contenido a servicios externos. Sin un control deliberado de qué se envía, cuándo y en qué forma, la plataforma estaría dejando salir los secretos de sus clientes hacia sistemas que no controla.
3. **Riesgo al comparar entre empresas.** Parte del valor de la plataforma está en aprender de los patrones del conjunto (qué valora cada órgano evaluador, cómo puntúa). Eso exige mezclar datos de empresas que compiten entre sí. Decir que los datos "están anonimizados" es fácil; garantizarlo es difícil: en un mercado provincial, saber el organismo, el importe y la fecha basta muchas veces para deducir qué empresa presentó qué. La protección tiene que comprobarse, no solo declararse.
4. **Riesgo en la puerta de entrada.** A diferencia de los pliegos —documentos oficiales, firmados, descargados de fuentes verificables—, la documentación privada llega como ficheros subidos por usuarios: la vía clásica de entrada de virus y ficheros manipulados, y también de contenido oculto (texto invisible dentro de un documento) que podría alterar el análisis que hace la IA.

**El problema unificado:** la categoría "IA del licitador" va a existir con o sin seguridad. Si se construye sin ella, las PYMEs —que ya desconfían de las soluciones tecnológicas generalistas— tendrán razón en desconfiar, y la oportunidad de democratización se perderá. Este proyecto invierte el orden habitual: primero diseñar y demostrar la capa de protección; después, construir la plataforma encima.

---

## 3. Solución propuesta

CENTINELA es la capa de protección sobre la que se construirá AtalaIA Licit@. Se organiza en cuatro componentes; cada uno responde a uno de los cuatro riesgos anteriores. Los describimos en el nivel en el que el equipo los va a trabajar: como problemas concretos con soluciones conocidas en la industria, que el equipo aprenderá a aplicar con el apoyo de la mentoría de GSEC.

### C1 — Entrada segura de documentos (responde al riesgo 4)

Una única puerta de entrada para los dos tipos de documento que manejará la plataforma:

- **Documentos públicos (pliegos de PLACSP):** comprobar que son auténticos, verificando su firma electrónica y su código seguro de verificación (CSV), y dejar registro de cuándo y de dónde se descargó cada uno.
- **Documentos privados (los que sube la empresa):** pasar cada fichero por un análisis antivirus antes de aceptarlo —usando servicios de análisis de ficheros reconocidos, como la API de VirusTotal—, comprobar que el formato es correcto, y revisar que el documento no contenga texto oculto. Para esto último, la idea es sencilla de explicar: se compara lo que una persona vería al abrir el documento con lo que la máquina lee de él; si no coinciden, hay algo escondido y se avisa.
- Cada documento queda etiquetado desde su entrada según lo sensible que es, y esa etiqueta determina cómo se le trata en el resto del sistema.

### C2 — Guardado protegido y control de lo que sale (responde a los riesgos 1 y 2)

El corazón de la propuesta: la información de cada empresa vive en su propio espacio y sale de él lo mínimo imprescindible.

- **Separación total por empresa:** cada cliente tiene su compartimento propio; ningún proceso del sistema puede mezclar la información de una empresa con la de otra.
- **Cifrado:** la información se guarda y se transmite siempre cifrada, de modo que ni siquiera un acceso indebido al almacenamiento la dejaría legible.
- **Control de lo que se envía a los servicios de IA:** antes de mandar cualquier contenido a un modelo de lenguaje externo, el sistema lo revisa y sustituye los datos que identifican a la empresa (nombres, importes delicados, referencias reconocibles) por equivalentes neutros, enviando solo lo necesario para la tarea concreta.
- **Registro de auditoría:** el sistema anota qué información salió, hacia qué servicio, para qué tarea y con qué transformación previa. Si un cliente pregunta "¿qué habéis hecho con mis datos?", la respuesta existe y está documentada.

### C3 — Anonimizado que se pone a prueba (responde al riesgo 3)

Para que las empresas puedan beneficiarse del conocimiento del conjunto sin exponerse individualmente:

- Un proceso que extrae de cada licitación solo los patrones útiles para todos (qué tipo de criterios usa un organismo, cómo reparte los pesos, cómo suele puntuar), eliminando todo aquello que permita deducir de qué empresa procede el dato.
- **Y la parte diferencial: ponerlo a prueba de forma adversarial.** El propio equipo, usando la información pública de PLACSP como ayuda, intentará averiguar qué empresa hay detrás de cada dato anonimizado. Solo si esos intentos fracasan se da por buena la protección. Los resultados de esas pruebas —cuántos intentos, cuántos éxitos, qué se corrigió— forman parte de los entregables del proyecto.

### C4 — Compartir sin exponerse: el caso UTE (diseño; responde al modelo de negocio)

El caso más exigente: dos empresas competidoras que preparan juntas una oferta en UTE necesitan compartir el análisis de esa licitación concreta, sin que ninguna vea el historial privado de la otra. En este proyecto, C4 se aborda como **diseño documentado** —qué puede ver cada parte, qué no, y cómo queda registrado lo compartido—, dejando su construcción completa para la fase de plataforma. Se incluye ahora porque condiciona decisiones del componente C2 que serían muy costosas de cambiar después.

### La función de negocio sobre la base segura

Sobre C1 y C2, el prototipo hace el trabajo que da sentido a todo: lee el pliego, extrae los elementos de decisión (criterios de valoración y sus pesos, requisitos de solvencia, plazos) y genera el **informe ejecutivo GO/NO-GO**, en el que cada dato indica la página del pliego de donde procede, para que el usuario pueda comprobarlo en segundos. Esta parte no parte de cero: automatiza, ahora sobre una base segura, la metodología que el fundador ya aplica manualmente con resultados medidos en su actividad profesional.

---

## 4. Uso previsto de técnicas de ciberseguridad e inteligencia artificial

**Del lado de la ciberseguridad**, el proyecto aplica prácticas establecidas de la industria, aprendiéndolas sobre un caso real y con mentoría especializada:

- Seguridad desde el diseño: empezar por un análisis de riesgos del sistema (qué hay que proteger, de quién, por dónde podrían atacar) y que ese análisis gobierne el desarrollo, en lugar de auditar al final.
- Análisis antivirus de los ficheros que entran (integración con servicios de análisis como la API de VirusTotal).
- Cifrado de la información guardada y transmitida, y separación estricta de los datos de cada cliente.
- Control y registro de la información que sale hacia servicios externos de IA.
- Anonimizado de datos con verificación práctica: pruebas de reidentificación realizadas por el propio equipo, con resultados medidos.
- Detección de contenido oculto en documentos, comparando la versión visible con el texto que lee la máquina.
- Coherencia con la normativa aplicable: protección de datos (RGPD), los principios del Esquema Nacional de Seguridad y el deber de confidencialidad de la normativa de contratación pública.

**Del lado de la inteligencia artificial:**

- Modelos de lenguaje para leer documentos largos, extraer información estructurada (criterios, pesos, requisitos, plazos) y generar informes de decisión.
- Reconocimiento óptico de caracteres (OCR) y tratamiento de imagen para procesar pliegos escaneados o de baja calidad, y para la comparación visual que detecta contenido oculto.
- Detección automática de nombres y datos identificativos en los textos, como paso previo a su sustitución antes de enviar nada a servicios externos.
- Trazabilidad de cada afirmación del informe a la página del documento que la respalda.

**La convergencia entre ambas disciplinas no es una suma, es una dependencia mutua:** la IA es la que hace útil la plataforma, pero solo puede aplicarse a esta información si la ciberseguridad garantiza cómo se guarda, qué sale y qué se comparte. Sin la capa de seguridad, la aplicación de IA sería irresponsable como producto e inviable como negocio. Sin la aplicación de IA, la capa de seguridad no tendría qué proteger.

---

## 5. Estado de desarrollo

Este apartado se redacta con la máxima claridad, porque el punto de partida define el plan de trabajo:

- **Lo que existe y está validado:** una metodología de análisis de licitaciones asistida por IA, desarrollada por Francisco Correa —fundador del proyecto— y aplicada durante 2025–2026 en su actividad profesional en consultoría de ingeniería civil, sobre licitaciones reales. Resultados medidos: reducción del tiempo de análisis preliminar de 2–4 horas a aproximadamente 15 minutos por pliego, con salida estructurada comparable entre expedientes. Existe además un plan de negocio completo de AtalaIA Licit@, con segmento de cliente definido, modelo de ingresos por fases y estrategia de validación en curso.
- **Una preincubación con respaldo institucional, no una idea aislada.** El plan de negocio se desarrolló en el programa Desafío Emprendedor Innovador de EOI (4ª edición, Málaga, completado). El fundador ha completado además el programa de Creación y Consolidación Empresarial con Herramientas de IA Aplicadas al Negocio (Fundación INCYDE – Polo Nacional de Contenidos Digitales, FSE+, abril–junio 2026). Y el proyecto tiene continuidad asegurada tras el verano: en septiembre de 2026 se incorpora al espacio de preincubación **Coworking DeepTech (6ª edición, EOI–PROMÁLAGA, Polo Digital de Málaga)**, un programa de cinco meses con mentorización especializada que culmina en un Demo Day ante inversores.
- **Lo que no existe todavía:** la plataforma como software. AtalaIA Licit@ está en fase de preincubación; el proceso actual requiere la intervención manual del fundador en cada análisis. Y, de forma directamente relevante para esta convocatoria, **la capa de ciberseguridad no ha sido explorada aún**: es el hueco que este proyecto ataca, en el mejor momento posible para hacerlo — antes de que exista código que haya que asegurar a posteriori.
- **Por qué julio–agosto en GSEC es el contexto idóneo:** el salto pendiente (de metodología manual a prototipo automatizado y protegido) requiere exactamente lo que ofrece la convocatoria — tiempo de desarrollo concentrado, recursos de computación e IA, y mentoría de profesionales de Google, que el equipo empleará de forma dirigida donde más la necesita: la revisión del análisis de riesgos y de las decisiones de protección de datos. El calendario, además, encaja con precisión: el prototipo resultante en agosto será el activo con el que el proyecto entre en septiembre en su fase de preincubación en el Polo Digital.

---

## 6. Plan de trabajo (julio–agosto 2026)

Cuatro quincenas con hitos verificables, computadas de lunes a domingo: los fines de semana forman parte del calendario de trabajo. El desarrollo lo lidera el responsable del proyecto, con dedicación diaria en horario de tarde (desde las 15:00 h de lunes a viernes) y fines de semana. Mario Quintana participa en sesiones de trabajo conjunto en régimen flexible, compatible con su actividad profesional, con foco en la revisión técnica, las pruebas y la validación de cada hito. Las sesiones presenciales en GSEC Málaga y las revisiones con la mentoría se programarán preferentemente en franjas de tarde.

### Quincena 1 (8–19 julio) — Análisis de riesgos y diseño
- Análisis de riesgos del sistema (qué activos se protegen, frente a quién, por qué vías) y diseño de los componentes C1–C4.
- Preparación del material de trabajo: 20–30 expedientes reales descargados de PLACSP + un conjunto de ofertas técnicas ficticias, creadas por el equipo y verosímiles gracias al conocimiento del sector del fundador. **Ningún dato privado real de terceros entra en el proyecto.**
- Preparación del material de prueba: ficheros maliciosos estándar de test (tipo EICAR), documentos con texto oculto y casos preparados para las pruebas de reidentificación.
- **Hito H1**: análisis de riesgos + diseño + material de trabajo listos. Primera revisión con mentoría.

### Quincena 2 (20 julio–2 agosto) — C1: entrada segura
- Construcción de la puerta de entrada: verificación de firma y CSV para documentos públicos; análisis antivirus, validación de formato y detección de texto oculto para documentos subidos.
- Etiquetado por sensibilidad y registro de trazabilidad de cada documento.
- **Hito H2**: entrada de documentos funcionando con ambos tipos, incluyendo el rechazo documentado de los ficheros maliciosos de prueba.

### Quincena 3 (3–16 agosto) — C2 y C3: guardado protegido y anonimizado
- Compartimentos cifrados por empresa y control de lo que sale hacia los servicios de IA (revisión, sustitución de datos identificativos y registro de auditoría).
- Proceso de anonimizado del conocimiento agregado y **pruebas de reidentificación** realizadas por el equipo, con resultados medidos.
- **Hito H3**: demostración de la separación entre clientes, del registro de datos salientes y de los resultados de las pruebas de reidentificación. Segunda revisión con mentoría.

### Quincena 4 (17–30 agosto) — Función de negocio, integración y demo
- Análisis del pliego con IA sobre la base protegida: informe GO/NO-GO con cada dato enlazado a su página de origen.
- Documento de diseño de C4 (compartición controlada, caso UTE).
- Integración de principio a fin, pruebas, vídeo demostrativo, memoria final y preparación de la demostración presencial. Tercera revisión con mentoría.
- **Hito H4**: prototipo integrado + demo en vivo + memoria final.

---

## 7. Hitos, entregables y resultado mínimo esperado

| Hito | Fecha | Entregable verificable |
|---|---|---|
| H1 | 19 jul | Análisis de riesgos + diseño C1–C4 + material de trabajo (real, simulado y de prueba) |
| H2 | 2 ago | Entrada segura operativa; rechazo demostrado de ficheros maliciosos de prueba |
| H3 | 16 ago | Guardado cifrado y separado por empresa + registro de datos salientes + resultados de las pruebas de reidentificación |
| H4 | 30 ago | Prototipo integrado con informe GO/NO-GO trazable + diseño C4 + vídeo demo + memoria final |

**Resultado mínimo esperado (compromiso):** un prototipo funcional que, de principio a fin, (1) recibe de forma segura un pliego público real y una oferta técnica simulada —detectando y rechazando en vivo un fichero malicioso de prueba—, (2) guarda la documentación cifrada y separada por empresa, con registro comprobable de todo lo enviado a servicios externos, (3) supera las pruebas de reidentificación sobre los datos anonimizados, y (4) produce un informe GO/NO-GO estructurado en el que cada dato remite a su página de origen. Repositorio de código documentado y vídeo demostrativo.

**Resultado ambicioso (si el ritmo lo permite):** una primera versión del componente C4 (vista compartida de una licitación entre dos clientes de prueba, sin acceso cruzado a sus historiales) y un panel web básico de resultados.

---

## 8. Recursos necesarios

- **Espacio de trabajo en GSEC Málaga** (previsto en la convocatoria): sede del desarrollo y de las sesiones de mentoría.
- **Recursos de computación e IA** (previstos en la convocatoria): créditos de uso de modelos de lenguaje y capacidad de cómputo para el procesamiento de documentos y las pruebas.
- **Mentoría de profesionales de Google**: de especial valor en el análisis de riesgos, las decisiones de protección de datos y las buenas prácticas de anonimizado.
- **Acceso a la API de VirusTotal** (o servicio equivalente de análisis de ficheros) para el componente de entrada segura.
- **Datos**: expedientes públicos de PLACSP y documentos privados simulados creados por el equipo. El proyecto no utiliza ningún dato privado real de terceros.
- **Aportados por el equipo**: metodología de análisis validada, conocimiento experto del sector de la contratación pública, plan de negocio de AtalaIA Licit@ y equipos personales de desarrollo.

---

## 9. Equipo: capacidades y complementariedad

**Francisco Andrés Correa Barrera — fundador de AtalaIA Licit@, responsable del proyecto y representante del equipo.**
Ingeniero Civil e Ingeniero de Organización Industrial, Máster Interuniversitario en Representación y Diseño en Ingeniería y Arquitectura (UMA, 2023), con **Matrícula de Honor en el Trabajo Fin de Máster**. Su vinculación con la Universidad de Málaga es de largo recorrido: estudiante de movilidad internacional en la UMA (curso 2017/2018, beca Santander), becario de apoyo y miembro de la Unidad de Garantía de Calidad del Máster RDIA (2022), y titulado de máster por esta universidad. Más de 10 años en obra pública, los últimos 3 como Senior Project Engineer en consultoría de ingeniería civil en Málaga, con responsabilidad directa en el análisis de pliegos y la preparación de ofertas a administraciones de todos los niveles. Cuenta con formación certificada en Transformación Digital (IA y Big Data) y en dirección de proyectos (PMBOK), trayectoria en programas de innovación (Vodafone Campus Lab: metodologías design thinking, lean y agile), y preparación específica para la gestión empresarial del proyecto: programa Desafío Emprendedor Innovador (EOI, 4ª ed. Málaga) y programa de Creación y Consolidación Empresarial con Herramientas de IA (Fundación INCYDE, 2026), ambos completados. Desde 2024 desarrolla y aplica la metodología de análisis de licitaciones con IA que este proyecto automatiza y protege. Su aportación es triple: el conocimiento del dominio —sabe de primera mano qué información considera crítica una empresa licitadora y por qué desconfiaría de entregarla, y ese conocimiento define los requisitos de protección del sistema—; la metodología validada, el desarrollo del prototipo y la evaluación de la calidad de los resultados; y la dirección del proyecto como fundador de la iniciativa empresarial a la que este prototipo da cimiento. Dedicación diaria en horario de tarde y fines de semana durante todo el periodo.

**Mario Quintana Simonet — partner estratégico técnico.**
Estudiante de último curso del Grado en Ingeniería de Telecomunicaciones, especialidad en Sonido e Imagen (UMA, ETSIT), con la totalidad de las asignaturas superadas y el Trabajo Fin de Grado en curso (presentación prevista: septiembre de 2026): *"Desarrollo e implementación de un sistema predictor de ubicación mediante señales 4G, 5G y WiFi, usando algoritmos basados en Machine Learning"* — experiencia práctica directa en la aplicación de aprendizaje automático, la otra mitad de la convergencia que persigue esta convocatoria. Programa en Python (aplicado en comunicaciones digitales y en su TFG), C++ y C. Trabaja actualmente en el laboratorio de Radiofrecuencia de Dekra Testing and Certification, un entorno profesional de ensayo, medición y certificación cuya cultura de "probar antes de dar por bueno" es exactamente la que CENTINELA aplica a la seguridad. Certificación Cambridge English B2, útil para las sesiones de mentoría. Su incorporación responde a una decisión deliberada del fundador: complementar el dominio del negocio con capacidad de ingeniería TIC. En el proyecto asume la revisión técnica del prototipo, el diseño y ejecución de las pruebas (ficheros de test, detección de contenido oculto, validación de hitos) y la producción audiovisual de la demostración, con dedicación flexible compatible con su actividad profesional.

**La complementariedad es la tesis del equipo:** el fundador aporta el problema real, la metodología validada y el criterio del sector; el partner técnico aporta formación TIC, experiencia práctica en Machine Learning y cultura profesional de ensayo y certificación. El equipo declara con honestidad que no cuenta con especialización formal previa en ciberseguridad: precisamente por eso el proyecto la aborda como su objeto central, acotada a prácticas concretas y bien establecidas de la industria, y con la mentoría de GSEC aplicada exactamente donde más valor aporta. Aprender ciberseguridad aplicada construyendo un sistema real que la necesita —y del que depende la viabilidad de una iniciativa empresarial en marcha— es, entendemos, el espíritu de esta convocatoria.

---

## 10. Impacto potencial, escalabilidad y transferencia

- **Democratización de una capacidad hoy reservada a las grandes empresas.** El mercado español de contratación pública en consultoría e ingeniería supera los 30.000 M€ anuales. Las grandes compañías analizan ese mercado con equipos y sistemas propios; las PYMEs, no. AtalaIA Licit@ pone esa inteligencia al alcance de la empresa mediana, y CENTINELA es lo que la hace confiable. El prototipo de este premio no termina en agosto: es el cimiento tecnológico de una iniciativa empresarial con plan de negocio completo, segmento objetivo definido (PYMEs andaluzas de ingeniería civil) y continuidad inmediata — en septiembre de 2026 el proyecto entra en el programa de preincubación Coworking DeepTech (EOI–PROMÁLAGA, Polo Digital de Málaga), de cinco meses de duración y con cierre en un Demo Day ante inversores. El proyecto queda así arraigado de principio a fin en el ecosistema tecnológico malagueño: GSEC en verano, Polo Digital desde septiembre.
- **Impacto económico y social en cadena.** Mejores decisiones de presentación y mejores ofertas elevan la tasa de conversión de las PYMEs; más contratos adjudicados a empresas medianas significan más empleo técnico cualificado en el tejido productivo local y un reparto más equilibrado de la contratación pública entre grandes empresas y PYMEs — más competencia real, en beneficio también de la propia administración contratante.
- **La seguridad como ventaja competitiva, no como coste.** En un sector cuya principal barrera de adopción tecnológica es la desconfianza, poder demostrar a un cliente cómo se guarda su información, qué sale del sistema y cómo se ha puesto a prueba el anonimizado convierte la ciberseguridad en el argumento comercial diferencial frente a los actores generalistas.
- **Transferencia directa a otros sectores.** El patrón de CENTINELA —entrada segura de documentos, guardado separado y cifrado, control de lo que se envía a servicios de IA, anonimizado verificado— es el que necesita cualquier plataforma vertical de IA que trabaje con información confidencial de empresas: asesoría legal, financiera, sanitaria, industrial. El problema que resuelve es general; la licitación pública es el caso concreto que lo demuestra.

---

*Málaga, julio de 2026*

**Representante del equipo a efectos de comunicaciones:** Francisco Andrés Correa Barrera — fco.andrescorrea@gmail.com · [PENDIENTE: teléfono]
