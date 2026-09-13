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
  258 generadas desde el temario y verificadas contra el texto original.
- **Repetición espaciada (SM-2)** con re-aprendizaje: lo que fallás vuelve en el
  examen siguiente y no sale de rotación hasta que lo acertás.
- **Diez preguntas por día**, priorizadas por los conceptos donde venís fallando.
- Al errar: primero **por qué la opción que elegiste está mal**, después la
  explicación, la cita textual del libro con número de página, y la figura de esa
  página cuando la hay.
- **Simulacro cronometrado**: 100 preguntas en 2 horas, repartidas con los pesos
  oficiales de ISC2, sin feedback hasta el final.
- **Estimación de aprobado** ponderada por dominio, informando qué parte del
  examen cubren tus datos.
- **Puntos y niveles**, con penalización por días sin repasar.
- **Recordatorio diario** como evento de calendario (`.ics`).

## Gemini

Sin clave, la app funciona completa: el banco ya está generado y todo lo demás
es local. Con clave, Gemini se encarga de:

- escribir preguntas nuevas sobre los conceptos donde estás flojo, usando las
  citas del libro como material y las preguntas del examen oficial como
  referencia de estilo;
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
