# Simulador EGEL Plus Derecho — estudio independiente

Aplicación estática sin backend, desarrollada con HTML5, Vanilla JavaScript y Tailwind CSS mediante CDN. Incluye tablero, prácticas, simulador cronometrado, banco de repaso, historial y exportación/importación del historial.

## Publicar en GitHub Pages
1. Descomprime el ZIP y sube **todo el contenido de la carpeta** al directorio raíz de tu repositorio (o a `/docs` si seleccionas esa carpeta como origen de Pages).
2. En GitHub abre **Settings → Pages**, elige **Deploy from a branch**, selecciona `main` y `/ (root)`.
3. Abre la URL publicada. `fetch('preguntas.json')` necesita HTTP(S): abrir `index.html` desde el explorador con `file://` no funcionará en la mayoría de los navegadores.
4. Para probar en local, abre una terminal en la carpeta y ejecuta `python -m http.server 8000`; entra en `http://localhost:8000`.

## Contenido
- `index.html`: interfaz, TailwindCSS y Chart.js (CDN).
- `app.js`: navegación, evaluación, temporizador, métricas, persistencia e importación/exportación.
- `preguntas.json`: **453 reactivos**: **24** con respuesta y fundamento de repaso (IDs 10001–10024) y **429** extraídos del archivo `AHORA SI.pdf` con clave de respuesta atribuida al material o confirmada por el usuario. **Los 453 están habilitados para calificación**, aunque las claves del banco histórico no equivalen a validación jurídica vigente.
- `assets/marca-estudio.svg`: gráfico original de estudio con referencia cromática IBERO. No es el logotipo oficial.

## Nota sobre la marca
El portal de imagen institucional IBERO `https://imageninstitucional.ibero.mx/` ofrece logotipos oficiales, pero indica que el uso de materiales institucionales debe contar con aprobación y que la promoción externa requiere coordinación. Si dispones de autorización, reemplaza `assets/marca-estudio.svg` por el recurso institucional autorizado y actualiza el texto de créditos. La app incluye explícitamente una declaración de no afiliación.

## Sobre los datos jurídicos
Los 429 reactivos históricos pueden contener extracción imperfecta, errores y referencias a legislación anterior. Están habilitados para calificación conforme a las respuestas aportadas, pero requieren revisión jurídica independiente. Los 24 reactivos añadidos son ejercicios originales con explicación pedagógica; no sustituyen revisión jurídica formal ni constituyen reactivos oficiales. Los resultados son un indicador de práctica, no una predicción del resultado oficial EGEL Plus.

## Persistencia
Historial local mediante `localStorage`, clave `egelResults_v1`. `saveResults(score, subject, mode, details)` recibe adicionalmente los totales y el desglose; `loadDashboardData()` presenta indicadores. Exportar JSON permite respaldar el historial; Importar fusiona por ID. Si borras los datos del navegador sin exportar, perderás el historial. No hay sincronización entre dispositivos.

## Dependencias
El HTML utiliza `cdn.tailwindcss.com` y Chart.js CDN; se requiere conexión a internet. No se necesita npm ni proceso de compilación.

## Próximos pasos recomendados
Validar jurídicamente cada reactivo original con normas vigentes, registrar fuente y fecha de comprobación, y añadir los reactivos ya revisados a `preguntas.json` con `correct` A/B/C y `feedback` específico. El simulador los incluirá automáticamente.


## Claves recuperadas del PDF de respuestas

Se extrajeron 286 claves mediante la identificación de resaltados verdes y magenta de `AHORA SI.pdf`, emparejadas exclusivamente en páginas con conteos inequívocos. El resto permanece sin calificación hasta emparejamiento seguro. Estas claves reproducen lo señalado por el documento, sin afirmar una validación normativa independiente de 2026.

Actualización por correspondencia textual: 169 reactivos tienen clave extraída con alto grado de confianza del PDF. Los restantes no se califican.


## Versión con auditoría y repaso de errores
- `auditoria-preguntas.json` identifica los reactivos sin correspondencia segura de clave y su página de origen; no se califican.
- Los intentos nuevos conservan la respuesta seleccionada por reactivo. `Repasar mis errores` permite reintentar respuestas equivocadas. Historiales previos siguen funcionando, pero no contienen detalle individual y no pueden reconstruirse.
- Las claves recuperadas del PDF no son una comprobación normativa actualizada a 2026.
- Las marcas visuales deben revisarse manualmente para resolver los reactivos restantes.


## Actualización de respuestas aportadas (24 de octubre de 2026)
Se integraron **77** selecciones de `respuestas_78_egel.json`. Ahora existen **452 preguntas calificables de 453** (375 anteriores más 77 nuevas). La **pregunta #61 (Laboral, página 16 de `AHORA SI.pdf`)** quedó sin respuesta en el archivo enviado y sigue fuera del modo calificable. `auditoria-preguntas.json` contiene únicamente ese registro. Las 77 nuevas claves tienen `answerSource: seleccion_usuario_2026_10_24` y `legalVerified: false` para no confundir la selección del documento con una revisión jurídica. No se borran ni alteran datos locales al publicar esta actualización.

## Cierre de auditoría de claves — pregunta 61
Se integró la respuesta **C (Ordinaria)** confirmada por el usuario para la pregunta 61 (Laboral, página 16 de `AHORA SI.pdf`). La auditoría ahora indica **453 de 453 con clave** y **0 pendientes de emparejamiento**. Esto NO significa que los 453 reactivos estén verificados jurídicamente ni que todas sus explicaciones sean completas. `localStorage` permanece intacto.


## Guía de estudio integrada

La nueva sección **Guía de estudio** se sirve desde `estudio.js` y `guia-estudio.json`. Ambos archivos son necesarios en la raíz del repositorio, junto con `app.js`, `index.html` y `preguntas.json`. Incluye resúmenes educativos originales con referencias a las páginas de `egel-derecho 2026.pdf` y capítulos de `guía estudio ceneval .docx`; **no distribuye los documentos originales**. Tiene búsquedas, filtros, progreso de lectura independiente en `localStorage` y enlaces de práctica por materia. No contiene el texto completo de la guía comercial. Revisar vigencia normativa antes de tomar el contenido como asesoría jurídica o respuesta definitiva.
