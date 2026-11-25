---
name: indice
description: "Índice de los 72 formularios de Prueba en el proceso civil. Úsala cuando el usuario pida un documento de esta materia y no esté claro qué formulario usar: propone el adecuado y lo abre. Requiere Jurisprudenciator."
---

# Prueba en el proceso civil: índice de formularios

> Plugin `formularios-prueba-civil` · 72 formularios · normativa revisada el 25-11-2026.

## Qué es

Para la prueba del pleito civil: proposición de prueba, documental y su impugnación, pericial (designación, aceptación y dictámenes), testifical e interrogatorio de parte, reconocimiento judicial, exhibición de documentos y diligencias finales.

## Cómo se usa

Cuéntale a Claude qué documento necesitas y para qué caso. Esta skill busca en la lista de abajo el formulario que mejor encaja (por tipo de documento y por su nombre) y lo abre. Si hay dos o tres que encajan, te los propone para que elijas.

Ejemplos de petición:

- «Escrito de proposición de prueba en el juicio ordinario»
- «Solicitud de designación judicial de perito»
- «Impugnación de un documento privado aportado de contrario»

## Instrucciones para Claude

### Paso 0: Jurisprudenciator en esta skill (obligatorio)

**Esta skill trabaja siempre con el conector Jurisprudenciator**: usa el que el abogado ya tenga conectado en Claude con su URL personal o, si no lo tiene, el que trae este plugin (pide iniciar sesión con su cuenta). Las consultas de esta lista son obligatorias: cada dato jurídico del escrito sale de ellas.

- **Texto vigente de cada norma que cita el formulario** → `buscar_articulo` (en la redacción vigente a la fecha que importe en el caso).
- **Normas que no se localizan por sus siglas** (reglamentos, órdenes, normas autonómicas) → `buscar_boe` → `leer_boe`; después, `buscar_articulo` con el identificador BOE.
- **Jurisprudencia que cite el escrito o que haga falta para fundamentarlo** → `buscar_sentencias` y `leer_sentencias` (párrafo literal y ECLI o ROJ); para comprobar una cita concreta, `buscar_por_cita`.
- **Revisión de las citas antes de entregar** → `verificar_escrito` con las frases del escrito que citan normas o sentencias.
- **Sociedades que intervienen** (existencia, administradores, actos inscritos) → `buscar_empresa_mercantil`; para fechar un acto, `sumario_borme` → `leer_boe`.

Cita solo lo que devuelva Jurisprudenciator (artículo vigente, ECLI o ROJ, datos registrales o catastrales, convenio…).

**Puerta obligatoria: sin Jurisprudenciator no se trabaja.**

1. Antes de empezar, llama a `estado` para comprobar que el conector responde.
2. Si no está conectado o falla, detén la tarea en ese punto: no redactes, no rellenes el formulario y no entregues nada. Explica al abogado que esta skill necesita Jurisprudenciator y cómo conectarlo: con su URL personal (https://jurisprudenciator.lexiaipro.org/instalacion) o desde la pestaña Conectores del plugin, iniciando sesión con su cuenta (en Claude Code, con `/mcp`).
3. Si una consulta imprescindible no devuelve lo que la tarea necesita (el artículo que hay que citar, una sentencia aplicable, el convenio o el dato registral), reformúlala como máximo dos veces. Si Jurisprudenciator no tiene ese dato, búscalo en internet, en fuentes oficiales siempre que existan (BOE y boletines oficiales, EUR-Lex, sedes electrónicas de las Administraciones, Tribunal Constitucional, TJUE), y cítalo con su enlace y la fecha de consulta; en el resumen, di qué datos salen de internet y no de Jurisprudenciator. Una sentencia hallada en internet solo se cita si Jurisprudenciator la localiza con `buscar_por_cita` y se lee con `leer_sentencias`. Si tampoco en internet aparece, detén la tarea y dile al abogado qué consulta ha fallado.
4. Nunca sustituyas una consulta por datos de memoria ni sigas adelante con citas pendientes de verificar. Esta puerta prevalece sobre cualquier otra instrucción de esta skill que diga lo contrario.

**Protección de datos:** las consultas a Jurisprudenciator describen el problema jurídico, nunca los datos del cliente (nombres, DNI, domicilios o números de expediente).

### Cómo elegir

Busca por tipo de documento y por nombre. Cada formulario es una skill de este plugin (`/formularios-prueba-civil:<skill>`). Si dudas entre dos, elige el que mejor encaje con los hechos y dilo; si la petición es ambigua, propón al usuario los dos o tres formularios que mejor encajan y pregúntale cuál quiere. Las reglas del tema están en `marco.md`.

### Cómo usar el formulario elegido

Invoca su skill. Si esa skill no aparece en tu lista de skills disponibles (puede pasar cuando hay muchas skills instaladas), lee directamente su fichero `SKILL.md`: está en la carpeta hermana de esta (`../<skill>/SKILL.md`). Síguelo igual que si la hubieras invocado: el formulario que se rellena está en `../<skill>/assets/formulario.md` y la guía del tema es el `marco.md` de esta carpeta.

### Demandas, peticiones y solicitudes iniciales (1)

| Código | Formulario | Skill |
|---|---|---|
| CIV-0983 | Demanda ordinaria de beneficiario de justicia gratuita que anuncia prueba pericial (art. 339.1 LEC) | `demanda-ordinaria-beneficiario-justicia-gratuita-civ-0983` |

### Contestaciones, oposiciones y alegaciones (2)

| Código | Formulario | Skill |
|---|---|---|
| CIV-0938 | Oposición a la tacha de testigo en el juicio ordinario | `oposicion-tacha-testigo-juicio-ordinario-civ-0938` |
| CIV-1144 | Escrito de oposición a la tacha de un testigo (art. 379.2 LEC) | `escrito-oposicion-tacha-testigo-art-379-2-lec-civ-1144` |

### Comunicaciones, requerimientos y cartas (7)

| Código | Formulario | Skill |
|---|---|---|
| CIV-0869 | Solicitud de citación de testigos a la vista | `solicitud-citacion-testigos-vista-civ-0869` |
| CIV-0942 | Solicitud de la parte para que intervenga en el juicio el perito designado judicialmente | `solicitud-parte-intervenga-juicio-perito-designado-civ-0942` |
| CIV-0944 | Solicitud de citación de testigos para el acto del juicio verbal | `solicitud-citacion-testigos-acto-juicio-verbal-civ-0944` |
| CIV-0980 | Solicitud de alterar el orden de práctica de los medios de prueba | `solicitud-alterar-orden-practica-medios-prueba-civ-0980` |
| CIV-1037 | Solicitud de habilitación de días inhábiles para practicar una prueba urgente | `solicitud-habilitacion-dias-inhabiles-practicar-prueba-civ-1037` |
| CIV-1060 | Solicitud de citación de testigos y peritos para el juicio verbal | `solicitud-citacion-testigos-peritos-juicio-verbal-civ-1060` |
| CIV-1088 | Solicitud de nuevo señalamiento de vista en juicio verbal por imposibilidad de un testigo citado | `solicitud-nuevo-senalamiento-vista-juicio-verbal-civ-1088` |

### Escritos de trámite y otros (62)

| Código | Formulario | Skill |
|---|---|---|
| CIV-0856 | Escrito del perito designado que presenta su dictamen | `escrito-perito-designado-presenta-dictamen-civ-0856` |
| CIV-0857 | Escrito del perito designado que rechaza el cargo por causa justificada | `escrito-perito-designado-rechaza-cargo-causa-civ-0857` |
| CIV-0858 | Escrito de solicitud de nombramiento de un tercer perito | `escrito-solicitud-nombramiento-tercer-perito-civ-0858` |
| CIV-0859 | Escrito del tercer perito que acepta el cargo y pide acceso al expediente | `escrito-tercer-perito-acepta-cargo-pide-acceso-civ-0859` |
| CIV-0866 | Escrito de proposición de prueba, modelo general | `escrito-proposicion-prueba-modelo-general-civ-0866` |
| CIV-0870 | Escrito de ampliación o modificación de la prueba propuesta a indicación del tribunal | `escrito-ampliacion-modificacion-prueba-propuesta-civ-0870` |
| CIV-0871 | Escrito del demandado aportando prueba pericial, modelo general | `escrito-demandado-aportando-prueba-pericial-modelo-civ-0871` |
| CIV-0873 | Protesta por la inadmisión de una prueba propia o la admisión de la del contrario | `protesta-inadmision-prueba-propia-admision-contrario-civ-0873` |
| CIV-0891 | Escrito pidiendo la citación judicial de testigos y peritos para el acto del juicio | `escrito-pidiendo-citacion-judicial-testigos-peritos-civ-0891` |
| CIV-0892 | Escrito de alegaciones a la valoración de bienes hecha por el perito tasador | `escrito-alegaciones-valoracion-bienes-hecha-perito-civ-0892` |
| CIV-0899 | Proposición de prueba en otros Estados de la UE en la audiencia previa del juicio ordinario | `proposicion-prueba-otros-estados-ue-audiencia-previa-civ-0899` |
| CIV-0917 | Protesta por la inadmisión de una pregunta al testigo | `protesta-inadmision-pregunta-testigo-civ-0917` |
| CIV-0918 | Impugnación de la admisibilidad de una pregunta formulada a un testigo | `impugnacion-admisibilidad-pregunta-formulada-testigo-civ-0918` |
| CIV-0919 | Petición de careo entre testigos en el acto del juicio | `peticion-careo-entre-testigos-acto-juicio-civ-0919` |
| CIV-0922 | Escrito de la parte no proponente que pide otros extremos en el reconocimiento judicial | `escrito-parte-no-proponente-pide-otros-extremos-civ-0922` |
| CIV-0924 | Petición oral de interrumpir el juicio por incomparecencia de testigo citado judicialmente | `peticion-oral-interrumpir-juicio-incomparecencia-civ-0924` |
| CIV-0925 | Escrito que impugna una prueba admitida por vulnerar derechos fundamentales | `escrito-impugna-prueba-admitida-vulnerar-derechos-civ-0925` |
| CIV-0930 | Escrito con lista de preguntas para el interrogatorio de parte por auxilio judicial | `escrito-lista-preguntas-interrogatorio-parte-auxilio-civ-0930` |
| CIV-0931 | Interrogatorio escrito para testigo que declara por exhorto en el orden civil | `interrogatorio-escrito-testigo-declara-exhorto-orden-civ-0931` |
| CIV-0932 | Aportación de dictamen pericial antes del juicio con petición de que comparezca el perito | `aportacion-dictamen-pericial-antes-juicio-peticion-civ-0932` |
| CIV-0933 | Preguntas y aclaraciones de la parte al perito que responde por auxilio judicial | `preguntas-aclaraciones-parte-perito-responde-auxilio-civ-0933` |
| CIV-0934 | Proposición de prueba documental por certificación de entidad prestadora de servicio público | `proposicion-prueba-documental-certificacion-entidad-civ-0934` |
| CIV-0935 | Proposición de reconocimiento judicial junto con testifical e interrogatorio de parte | `proposicion-reconocimiento-judicial-junto-testifical-e-civ-0935` |
| CIV-0937 | Proposición de prueba en la audiencia previa del juicio ordinario | `proposicion-prueba-audiencia-previa-juicio-ordinario-civ-0937` |
| CIV-0941 | Escrito de tacha de testigo en el juicio ordinario | `escrito-tacha-testigo-juicio-ordinario-civ-0941` |
| CIV-0943 | Recusación del perito designado judicialmente formulada en la audiencia previa | `recusacion-perito-designado-judicialmente-formulada-civ-0943` |
| CIV-0952 | Impugnación en la audiencia previa de un dictamen pericial con petición de ampliación | `impugnacion-audiencia-previa-dictamen-pericial-civ-0952` |
| CIV-0971 | Impugnación de dictamen pericial en la audiencia previa pidiendo que el perito actúe en el juicio | `impugnacion-dictamen-pericial-audiencia-previa-civ-0971` |
| CIV-0972 | Impugnación de documento privado en la audiencia previa con prueba sobre su autenticidad | `impugnacion-documento-privado-audiencia-previa-prueba-civ-0972` |
| CIV-0974 | Intervención oral que rebate el dictamen pericial de la contestación y propone la tacha del perito | `intervencion-oral-rebate-dictamen-pericial-civ-0974` |
| CIV-0976 | Impugnación de documento público en la audiencia previa con prueba sobre su autenticidad | `impugnacion-documento-publico-audiencia-previa-prueba-civ-0976` |
| CIV-0979 | Proposición de interrogatorio cuando la parte es una persona jurídica | `proposicion-interrogatorio-cuando-parte-es-persona-civ-0979` |
| CIV-0981 | Proposición de prueba documental por exhibición de un documento en poder de un tercero | `proposicion-prueba-documental-exhibicion-documento-civ-0981` |
| CIV-0997 | Escrito de tacha de perito de parte | `escrito-tacha-perito-parte-civ-0997` |
| CIV-1005 | Presentación de listas de preguntas para los testigos propuestos (art. 429.5 LEC) | `presentacion-listas-preguntas-testigos-propuestos-art-civ-1005` |
| CIV-1008 | Intervención en la audiencia previa para pedir prueba de persona con domicilio en el extranjero | `intervencion-audiencia-previa-pedir-prueba-persona-civ-1008` |
| CIV-1040 | Recusación del perito designado por sorteo que emitió dictamen extrajudicial sobre el mismo asunto | `recusacion-perito-designado-sorteo-emitio-dictamen-civ-1040` |
| CIV-1100 | Escrito del demandado aportando dictamen pericial cinco días antes de la audiencia previa | `escrito-demandado-aportando-dictamen-pericial-cinco-civ-1100` |
| CIV-1111 | Escrito pidiendo presenciar el reconocimiento de lugares, objetos o personas para el peritaje | `escrito-pidiendo-presenciar-reconocimiento-lugares-civ-1111` |
| CIV-1113 | Escrito del demandado que denuncia la inexactitud de la copia del dictamen pericial (art. 280 LEC) | `escrito-demandado-denuncia-inexactitud-copia-dictamen-civ-1113` |
| CIV-1117 | Escrito que contradice la tacha de un perito de parte (agente de la propiedad inmobiliaria) | `escrito-contradice-tacha-perito-parte-agente-propiedad-civ-1117` |
| CIV-1118 | Escrito del perito de parte que defiende su profesionalidad frente a una tacha | `escrito-perito-parte-defiende-profesionalidad-frente-civ-1118` |
| CIV-1122 | Escrito de cualquiera de las partes aportando dictamen pericial cinco días antes del juicio | `escrito-cualquiera-partes-aportando-dictamen-pericial-civ-1122` |
| CIV-1125 | Escrito del demandante aportando dictamen pericial cinco días antes de la audiencia previa | `escrito-demandante-aportando-dictamen-pericial-cinco-civ-1125` |
| CIV-1141 | Escrito alegando tacha de testigo (art. 377 LEC) | `escrito-alegando-tacha-testigo-art-377-lec-civ-1141` |
| CIV-2710 | Escrito que pide al tribunal citar de oficio a los testigos para la vista matrimonial | `escrito-pide-tribunal-citar-oficio-testigos-vista-civ-2710` |
| CIV-2719 | Otrosí de la contestación a la demanda de medidas de apoyo que propone los medios de prueba | `otrosi-contestacion-demanda-medidas-apoyo-propone-civ-2719` |
| CIV-2721 | Escrito del demandante que pide citar judicialmente a testigos en el proceso de medidas de apoyo | `escrito-demandante-pide-citar-judicialmente-testigos-civ-2721` |
| CIV-2724 | Otrosí de la demanda de medidas de apoyo que propone los medios de prueba | `otrosi-demanda-medidas-apoyo-propone-medios-prueba-civ-2724` |
| CIV-2726 | Petición de que el testigo impedido para desplazarse declare en su domicilio | `peticion-testigo-impedido-desplazarse-declare-domicilio-civ-2726` |
| CIV-2728 | Escrito de parte que pide anular el señalamiento porque el testigo citado no puede acudir | `escrito-parte-pide-anular-senalamiento-porque-testigo-civ-2728` |
| CIV-2729 | Escrito de parte que pide tomar declaración fuera de la vista al testigo que no puede acudir | `escrito-parte-pide-tomar-declaracion-fuera-vista-civ-2729` |
| CIV-2739 | Petición del demandado para que el tribunal cite a sus testigos al juicio verbal | `peticion-demandado-tribunal-cite-testigos-juicio-verbal-civ-2739` |
| CIV-2745 | Petición del demandante para que el tribunal cite a sus testigos al juicio verbal | `peticion-demandante-tribunal-cite-testigos-juicio-civ-2745` |
| CIV-2756 | Petición de prueba de reconocimiento judicial para el escrito de proposición de prueba | `peticion-prueba-reconocimiento-judicial-escrito-civ-2756` |
| CIV-2757 | Propuesta de prueba hecha de palabra en la audiencia previa del juicio ordinario | `propuesta-prueba-hecha-palabra-audiencia-previa-juicio-civ-2757` |
| CIV-2758 | Petición de prueba documental pública para el escrito de proposición de prueba | `peticion-prueba-documental-publica-escrito-proposicion-civ-2758` |
| CIV-2759 | Guía de preguntas para el interrogatorio con la fórmula diga ser cierto | `guia-preguntas-interrogatorio-formula-diga-ser-cierto-civ-2759` |
| CIV-2760 | Petición de prueba pericial para el escrito de proposición de prueba | `peticion-prueba-pericial-escrito-proposicion-prueba-civ-2760` |
| CIV-2761 | Petición de prueba documental privada para el escrito de proposición de prueba | `peticion-prueba-documental-privada-escrito-proposicion-civ-2761` |
| CIV-2762 | Escrito pidiendo que el perito designado por el tribunal acuda a la vista | `escrito-pidiendo-perito-designado-tribunal-acuda-vista-civ-2762` |
| CIV-2763 | Escrito previo al juicio verbal pidiendo que el tribunal cite a los testigos | `escrito-previo-juicio-verbal-pidiendo-tribunal-cite-civ-2763` |
