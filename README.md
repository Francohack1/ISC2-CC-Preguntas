# Repaso ISC2 CC

Repaso diario con repetición espaciada sobre el temario de la certificación
ISC2 Certified in Cybersecurity. Una sola página, sin backend, sin build.
El progreso vive en el navegador del teléfono.

## Publicarlo (3 pasos, todo desde el navegador)

1. Creá un repo nuevo en GitHub. Puede ser **privado**.
2. **Add file → Upload files** y subí `index.html` y este `README.md`.
3. **Settings → Pages → Source: Deploy from a branch → main / (root) → Save.**

En un minuto queda en `https://<tu-usuario>.github.io/<tu-repo>/`.
Abrilo en el Pixel y **Chrome → ⋮ → Agregar a pantalla principal**: queda con
ícono propio y se abre a pantalla completa.

> Si el repo es privado, Pages necesita cuenta de pago. Con repo público el
> sitio es accesible para quien tenga el link; no hay datos tuyos adentro salvo
> que cargues tu clave de Gemini, que nunca sale de tu teléfono.

## Qué tiene

- **456 preguntas**: 198 de los dos exámenes oficiales del libro con su clave, y
  258 generadas desde el temario y verificadas contra el texto original. Todas
  clasificadas en los 19 objetivos del temario vigente.
- **276 conceptos clave** del *(ISC)2 CC Exam Guide* (Hemang Doshi, Packt 2026):
  pares pregunta–respuesta para repaso rápido, ordenados por los objetivos donde
  peor venís, y material con el que se escriben las preguntas nuevas.
- **Repetición espaciada (SM-2)** con re-aprendizaje: lo que fallás vuelve en el
  examen siguiente y no sale de rotación hasta que lo acertás.
- **Diez preguntas por día**, priorizadas por los conceptos donde venís fallando.
- Al errar: primero **por qué la opción que elegiste está mal**, después la
  explicación, la cita textual del libro con número de página, y la figura de esa
  página cuando la hay.
- **Simulacro cronometrado**: 100 preguntas en 2 horas, repartidas entre los cinco
  dominios, sin feedback hasta el final.
- **Estimación de aprobado** por dominio, informando cuántos dominios tienen ya
  datos suficientes.
- **Cobertura del temario**: los 19 objetivos oficiales, con cuántas preguntas
  te quedan sin ver en cada uno.
- **Reposición automática**: cuando te quedan pocas preguntas sin ver, se
  escriben nuevas apuntando a los objetivos más flacos.
- **Puntos y niveles**, con penalización por días sin repasar.
- **Recordatorio diario** como evento de calendario (`.ics`).

## El temario vigente

ISC2 cambió el esquema del examen CC el **1 de septiembre de 2026**. Los dominios
ahora son cinco y llevan otros nombres:

| | Dominio | Objetivos |
|---|---|---|
| 1 | Security Principles | 1.1 – 1.5 |
| 2 | Security Governance | 2.1 – 2.4 |
| 3 | Identity and Access Management | 3.1 – 3.2 |
| 4 | Networking and Cloud Security | 4.1 – 4.3 |
| 5 | Security Operations and Incident Response | 5.1 – 5.5 |

El libro de Manning sigue el esquema anterior (Security Principles 26% / Network
Security 24% / Access Controls 22% / Security Operations 18% / BC-DR-IR 10%). Las
preguntas siguen siendo válidas — el contenido del CC casi no cambió, se
reorganizó — así que están reclasificadas una por una en los objetivos nuevos.

**ISC2 no publica el peso de cada dominio en este esquema.** Antes sí. La app no
inventa porcentajes: promedia los cinco dominios por igual y lo aclara en
pantalla.

## Las dos fuentes

| Libro | Qué aporta |
|---|---|
| *Become ISC2 Certified in Cybersecurity* (Manning) | Las 198 preguntas de sus dos exámenes, con clave; las citas y figuras que se muestran al fallar |
| *(ISC)2 CC Exam Guide* (Hemang Doshi, Packt 2026) | 276 pares pregunta–respuesta de los cuadros "Key concepts for the CC exam" |

El Exam Guide **no trae preguntas impresas**: sus 56 quizzes viven online, detrás
del código que se desbloquea con el libro, y no están en el PDF. Sus cuadros de
conceptos clave sí, y son exactamente lo que el examen pregunta.

Los dos libros siguen el **esquema anterior** de dominios, incluido el de Packt
pese a ser de 2026. Las preguntas y los conceptos están reclasificados a los 19
objetivos vigentes.

## Sobre las "preguntas oficiales" de internet

No existe un banco de preguntas oficial publicado por ISC2. Lo único oficial y
gratuito son el temario (los 19 objetivos), las flash cards y el Study Hub. Lo
que circula como "preguntas oficiales del CC" es material de terceros con
derechos de autor, o volcados del examen real (*braindumps*). Usar volcados viola
el acuerdo que firmás como candidato y se sanciona con la pérdida de la
certificación, así que la app no los busca ni los usa.

Lo que sí hace: anclar cada pregunta nueva en **el texto del objetivo oficial**
más tres preguntas reales del examen del libro del mismo dominio como molde de
estilo.

## Gemini

Sin clave, la app funciona completa: el banco ya está generado y todo lo demás
es local. Con clave, Gemini se encarga de:

- escribir preguntas nuevas sobre los conceptos donde estás flojo, usando las
  citas del libro como material y las preguntas del examen oficial como
  referencia de estilo;
- **reponer el banco cuando se acaba**: cuando te quedan menos de 15 preguntas
  sin ver, la app ofrece generar más; por debajo de 7 lo hace sola, una vez por
  día. Elige los objetivos del temario con menos preguntas sin ver y, a
  igualdad, aquellos donde peor venís respondiendo;
- explicar un error de otra manera cuando la explicación escrita no alcanzó;
- el diagnóstico de tus errores;
- **elegir cuáles de las tarjetas vencidas entran en el examen de hoy.**

Ese último punto tiene un reparto deliberado: **SM-2 decide cuándo vence cada
tarjeta** — ahí su matemática de intervalos es insuperable — y **Gemini elige
cuáles de las vencidas van hoy y en qué orden**, que es donde sí aporta: SM-2
razona con estadísticas por tarjeta y no ve relación entre ellas, mientras que un
modelo que lee los enunciados puede juntar las que atacan la misma confusión.
Todo lo que devuelve se valida contra el pool; un id inventado se descarta.

Cargá la clave en **Motor de IA**, abajo de todo. Se pega una vez y queda
guardada en ese teléfono.

### Por qué la clave no está escrita en el código

Porque GitHub Pages sirve `index.html` públicamente, incluso si el repositorio
es privado: cualquiera con el link puede ver el código fuente. Y si el repo es
público, los bots que escanean GitHub la encuentran en minutos — Google también
escanea y revoca automáticamente las claves que aparecen ahí.

Guardada en el navegador, la clave no viaja al repositorio, no está en el HTML
servido y no sale del teléfono. Si querés usarla en otro dispositivo, la pegás
ahí una vez más.

## Notificaciones

Una página web no puede despertarte con la pestaña cerrada: eso necesita un
service worker con push desde un servidor. El botón de recordatorio genera un
evento de calendario que se repite a diario, y de eso se encarga Android con sus
propias notificaciones.

## Actualizar el banco

Las preguntas están embebidas en `index.html` dentro de
`<script id="qdata" type="application/json">`. Reemplazando ese JSON cambiás el
banco sin tocar el resto.
