# Feed Doctor — prueba de demanda

Fase 2 del plan de §11.5. **No se escribe una línea de código hasta pasar la puerta.**

---

## La hipótesis, escrita para poder falsarla

> Existe un segmento de comerciantes de WooCommerce que ya usan Google Shopping, sufren productos rechazados, no saben cuáles ni por qué, y no van a pagar 119 $/año por CTX Feed ni 59 $/mes por DataFeedWatch porque no quieren *generar* feeds — el feed ya lo generan. Quieren **diagnóstico**.

Si es falsa, lo normal es que la respuesta sea "eso ya me lo dice Merchant Center" o silencio absoluto.

## Evidencia que la sostiene (medida el 26-jul-2026)

| Dato | Valor | Fuente |
|---|---|---|
| `google-listings-and-ads`, plugin oficial de Google | 800.000 instalaciones, rating 54/100 | API WordPress.org |
| Valoraciones de una estrella | **49,6 %** (132 de 266) | ídem |
| Causa nº1 de rechazo en Merchant Center | Precio del feed ≠ precio de la página | Productsup, Channable |
| Causa nº2 | GTIN ausente o inválido | ídem |
| Quejas recurrentes del plugin oficial | Configuración que no termina, sincronización que no ocurre, errores PHP críticos | Foro de soporte de WordPress.org |
| Disposición a pagar, probada | CTX Feed Pro 119 $/año · Channable 49-74 $/mes · DataFeedWatch 59-239 $/mes **sin plan gratuito** | Webs de los proveedores |

Cuatro empresas independientes viven de este problema. Esa es la diferencia con las cinco categorías descartadas: en deduplicación **nadie** cobraba nada.

## Por qué diagnóstico y no generación

Los cuatro que cobran **generan** feeds. El plugin oficial genera y sincroniza, y se rompe. Ninguno responde a la pregunta que de verdad hace el comerciante: *"¿por qué me han rechazado 340 productos y cuáles son?"*

Merchant Center informa del síntoma agregado, no de la fila que lo causó.

Ventaja lateral y nada menor: un validador tiene **mucha menos superficie de soporte** que un gestor de feeds. No sube nada, no toca la cuenta de Google, no puede romper una campaña. Dado que 2-4 tickets por cada 1.000 usuarios y semana es lo que hunde a los desarrolladores solos (§11.3), esto importa tanto como el producto.

## Precio y su razonamiento

| Plan | Precio | Qué incluye |
|---|---|---|
| Gratis | 0 € | Escaneo completo, recuento por tipo de problema, 10 productos de ejemplo por tipo |
| Pro | **29 €/año**, una tienda | Todos los productos afectados con el valor que falla, exportación CSV, reescaneos programados |
| Pro 5 | 59 €/año | Cinco tiendas |

- 29 € contra los 119 $ de CTX Feed: hace **menos** —no genera ni sube feeds— y va dirigido a quien no paga 119 $.
- El corte gratis/pago está donde acota el soporte: el plan gratuito da un **número**, no una conversación. Quien quiere la lista, paga.
- Anual, no mensual: a este precio el cobro mensual se come el margen en comisiones.

## Paso 1 ejecutado — lectura del foro de soporte, 31 de julio de 2026

32 hilos leídos en el foro de `google-listings-and-ads`. **Contradice parcialmente la hipótesis de partida.**

**Lo que la gente escribe de verdad, con sus palabras:**

| Frase textual | Frecuencia |
|---|---|
| "Products won't sync — 0 pushed, no sync jobs scheduled" | dominante |
| "0 products successfully submitted to Google" | dominante |
| "Active 0, Pending 0, Disapproved 0, **Not Synced 262**" | dominante |
| "Plugin Broke my Site" / "White Screen After Admin Login" / "fatal error in admin" | muy frecuente |
| "cannot reconnect existing Merchant Center after OAuth" | frecuente |
| "catalogue entier resoumis toutes les heures, 190 598 tâches Action Scheduler" | casos graves |
| Algo sobre productos **rechazados** | **1 hilo de 32** |

**Corrección honesta**: el posicionamiento original —"te han rechazado 340 productos y no sabes cuáles"— se apoyaba en artículos de Productsup y Channable, que son *proveedores de feeds haciendo marketing de contenidos*, no usuarios describiendo su dolor. Eso es evidencia de segunda mano y la traté como si fuera de primera.

**Pero el instrumento está sesgado y no refuta la hipótesis**: quien escribe en el foro de soporte de un plugin escribe sobre el plugin roto. Quien tiene productos rechazados acude a la ayuda de Merchant Center, no al foro de WordPress. La ausencia de hilos sobre rechazos ahí no es prueba de ausencia de dolor.

**Lo que sí aporta**: `Not Synced 262` con `Disapproved 0` es también un fallo de diagnóstico — el comerciante no sabe por qué no ha subido nada. Es el mismo hueco, un paso antes en la tubería. El producto probablemente deba cubrir las dos preguntas:

1. *¿por qué no ha subido nada?*
2. *¿por qué me han rechazado esto y qué es?*

**Decisión**: no reescribir la página basándome en más inferencias mías. La pregunta que se lanza en los canales debe ser lo bastante neutra para capturar ambas, y que respondan ellos. Texto revisado abajo con su vocabulario real.

## Dónde enseñarla

Por orden de esfuerzo. **En ninguna se vende: se pregunta.**

1. **Foro de soporte de `google-listings-and-ads`** — donde la gente está escribiendo el problema ahora mismo. No publicar el enlace en respuestas ajenas: eso es spam y te ganas la expulsión. Leer 30 hilos y anotar qué piden con sus palabras.
2. **r/woocommerce**, r/PPC, r/GoogleAds — post preguntando, no anunciando: *"¿cómo averiguáis qué productos concretos os rechaza Merchant Center?"*
3. **Grupos de Facebook de WooCommerce en español** — es donde están los comerciantes pequeños, y es tu ventaja de idioma.
4. **Agencias españolas de Google Ads** — son quienes gestionan varias tiendas y sufren esto multiplicado por cliente. El plan de 5 tiendas está pensado para ellas.

## La puerta

**Alguien pregunta por precio o por disponibilidad sin que se lo pidas.**

- ✅ Pasa: *"¿cuándo estará?"*, *"¿cuánto costaría para 3 tiendas?"*, *"avísame"*
- ❌ No pasa: "buena idea", "suena útil", pulgares arriba
- ❌ No pasa: silencio

Un "me gusta" no es una compra. Ya nos costó cinco rondas aprenderlo.

**Plazo: 14 días desde publicar.** Sin señal, se vuelve a fase 1 con el siguiente candidato — no se construye igualmente.

## Publicada — coste 0 €

**https://javitax47.github.io/feed-doctor/**

Repositorio `Javitax47/feed-doctor`, servido por GitHub Pages. Coste cero; el dominio de 10 € es opcional y puede esperar a que la puerta pase.

**Integración de Formspree**: endpoint `mwvgjjee`, guía Basic HTML. Se descartó el SDK de AJAX a propósito: es un fichero estático sin bundler, y traer una dependencia por CDN no aporta nada que el `action` no haga ya. El `fetch()` que hay es mejora progresiva sobre ese `action` — con JavaScript desactivado el formulario sigue enviando, solo que navegando fuera.

Campo trampa `_gotcha` incluido: el plan gratuito son 50 envíos al mes y el spam consume cuota.

**Pendiente y no trivial**: Formspree exige confirmar el correo la primera vez. Envía un email de verificación con el primer envío y **no reenvía nada hasta que se confirme**. Hay que rellenar el formulario una vez con el correo propio y confirmarlo, antes de difundir el enlace. En una prueba de 14 días, la primera respuesta puede ser la única.

---

## Texto para los canales en español

**Post en grupo de WooCommerce / Reddit español** — pregunta, no anuncio.

> Estoy valorando montar una herramienta pequeña y prefiero preguntar antes de escribir código, por si ya está resuelto y me ahorro el trabajo.
>
> Leyendo el foro de soporte del plugin de Google me encuentro mucho esto: paneles con **Active 0, Pending 0, Disapproved 0, Not Synced 262** y ninguna pista de qué falla. Y por otro lado, gente a la que sí le suben los productos pero le desaprueban una parte con un "problemas de datos de producto" sin decir cuáles.
>
> Los que vendéis en Shopping: ¿cómo averiguáis qué producto concreto falla y por qué? ¿Lo dice Merchant Center directamente y me estoy perdiendo algo, lo lleva la agencia, o acabáis exportando el CSV y mirándolo a mano?
>
> Pregunto en serio: si Merchant Center ya lo dice claro, no tiene sentido que monte nada.

**Por qué está redactado así.** Tres decisiones, cada una por un motivo:

1. **Dice la verdad sobre quién escribe.** Un estudiante valorando construir algo, no un comerciante con tienda. Cualquier versión encubierta —"hago como que soy principiante", "pregunto qué analizador es más barato"— se cae en la primera respuesta que pregunte de vuelta *qué versión del plugin usas* o *cuántas referencias tienes*, y desaparecer del hilo es el patrón que delata a un bot. Una cuenta antigua sin comentarios que abre con una pregunta dirigida sobre una categoría de producto es, además, el perfil exacto del marketero infiltrado: si un moderador lo marca, el canal se pierde entero.
2. **Se puede falsar.** *"Eso ya te lo dice Merchant Center, no montes nada"* es una respuesta válida y es información de primera. La versión encubierta —"¿cuál es el mejor analizador?"— no puede recibirla: devuelve recomendaciones de herramientas, que es competencia ya medida arriba, y presupone que la categoría es correcta. Ese formato fabrica su propio resultado.
3. **Nombra los dos síntomas con las palabras exactas del foro** —`Not Synced`, `Disapproved 0`— sin decidir cuál duele más. Si responden mayoritariamente sobre uno, eso decide el producto. Si el post afirmara cuál es el problema, la respuesta ya no sería información.

**Regla al responder**: si alguien pregunta qué estás montando, entonces sí enlazas. Si no pregunta nadie, el enlace no aparece — y eso es información, no fracaso.

**Corrección de la versión anterior de este borrador**: incluía la frase *"yo he acabado exportando el CSV y mirándolo a mano, con 200 referencias es tedioso"*. Escrita dando por supuesto un perfil de comerciante en activo. No aplica —no hay tienda, no hay CSV— y convertía el post en la impostura que este apartado descarta. Eliminada.

## Variantes por canal

Los subs de WooCommerce, PPC y Google Ads son **anglófonos**. El texto de arriba solo vale para los grupos de Facebook en español.

### A · r/woocommerce (inglés) — aportar el dato, no pedirlo

**Normas leídas el 31-jul-2026.** Condicionan el formato:

| Norma | Efecto |
|---|---|
| **1 · Sin material promocional en posts** | Ni nombre, ni enlace, ni producto. En comentarios sí se permiten recomendaciones. |
| **2 · Nada fuera de tema** | Anclar en el plugin `google-listings-and-ads`, que es extensión de Woo. Hablar de "Merchant Center" en abstracto deriva a comercio electrónico general y es retirable. |
| **3 · Buen rollo, y respeto al ecosistema** | El dato es duro —49,6 % de valoraciones de una estrella—. Se presenta como *lo que la gente reporta*, no como *este plugin es basura*. |
| **6 · Sin encuestas ni investigación** | **Prohíbe el formato "estoy valorando montar algo, ¿existe el problema?"**. Salvo excepción: *directly tied to Woo with clear Woo-specific data*. |

La primera versión de este borrador —"I'm a student thinking about building a small tool, I'd rather ask first"— **infringe la norma 6 de frente**. Es investigación de mercado con otro nombre.

La excepción de la 6 no se aprovecha disimulando la pregunta, sino **invirtiendo el post: aportar el dato en lugar de pedirlo.** Los 32 hilos leídos son dato específico de Woo y hacen del post una contribución. La pregunta va detrás.

> **Title:** Went down a rabbit hole in the Google Listings & Ads support forum — what people complain about most isn't what I expected
>
> A few days ago I fell into the support threads for the official Google Listings & Ads plugin and ended up reading far more of them than I meant to. Around 32 in the end. I don't run a store myself, I just got curious about how Woo stores actually connect to Shopping, and there's a lot more friction in that pipeline than I'd assumed.
>
> What I expected going in was that most of the pain would be disapprovals — Google rejecting products over data issues. That's what every article about feeds is about.
>
> It's basically not that. Out of the 32 threads, exactly one was about disapprovals.
>
> What people are actually frustrated about:
>
> - Products just… not syncing. By far the most common. Dashboard sitting at `Active 0, Pending 0, Disapproved 0, Not Synced 262` with nothing explaining why.
> - "0 products successfully submitted to Google", over and over, with no error to go on
> - Fatal errors or a white screen in wp-admin after activating or updating
> - OAuth failing to reconnect an existing Merchant Center account
> - One person had the whole catalogue resubmitting every hour with ~190,000 Action Scheduler tasks stacked up
>
> The thing that stuck with me is that most of them aren't stuck on a hard problem. They're stuck on not knowing *which* thing is broken. The dashboard hands them a number and no thread to pull.
>
> My guess for why disapprovals barely show up is that those people go to Merchant Center help instead of the plugin forum. But that's a guess — could just be that I read a skewed sample.
>
> So, for people actually running Woo on Shopping: when the sync silently does nothing, how do you work out which product or which field is behind it? Is there something in the plugin logs I missed, or is exporting the CSV and eyeballing it genuinely the normal answer?

**Flair**: `Troubleshooting`. El cuerpo son problemas de diagnóstico y la pregunta final es de método, así que encaja — y aleja el post del olor a investigación que penaliza la norma 6. `How do I…?` es la segunda opción, aunque presupone tienda propia y el post dice que no la hay. **`Plugin recommendation` no**: sería falso y es el flair donde vive la autopromoción de la norma 5, así que pinta al autor buscando contra qué posicionarse. `Resolved` es flair de estado: se pone al final si alguien da la respuesta definitiva.

**Requisito antes de publicarlo**: los números hay que poder defenderlos. Si alguien pide los hilos, hay que tenerlos. Recorrer el foro personalmente antes de publicar y quedarse con los enlaces.

**Qué se obtiene y qué no**: valida **el problema**, no **la demanda**. La norma 1 impide decir que estás construyendo algo, así que nadie preguntará precio y **la puerta de los 14 días no se pasa aquí**. La señal de demanda tiene que salir de los grupos de Facebook y de las agencias.

**Hallazgo lateral, para después del test**: la norma 5 permite recomendar herramientas propias **en comentarios**, si responden a la pregunta concreta de alguien. Es un canal de distribución legítimo y permanente el día que el producto exista.

### B · r/PPC · r/GoogleAds (inglés) — ángulo agencia

> **Title:** Agencies — how do you handle Merchant Center disapprovals across multiple clients?
>
> Student here, considering building a small diagnostic tool. Asking before I write any code in case this is already a solved problem.
>
> What I keep seeing described: Merchant Center reports a chunk of the catalogue disapproved for "product data issues", and finding which SKUs and which field is the actual work. Tedious for one store. I'd assume it compounds across 5-10 client accounts.
>
> How do you do it today — a feed platform you already pay for (Channable, DataFeedWatch, Feedonomics), the Content API, spreadsheets, or just the Merchant Center UI?
>
> And the honest version of the question: is this a real time sink for you, or does the tooling you already have handle it fine?

### C · Grupo de Facebook de WooCommerce en español — corto

> Pregunta para quien venda en Google Shopping.
>
> Soy estudiante y estoy valorando montar una herramienta pequeña, pero prefiero preguntar antes de ponerme, por si ya está resuelto.
>
> Cuando Merchant Center os desaprueba productos, o directamente no sube nada y solo veis "Not Synced", ¿cómo averiguáis qué producto concreto falla y por qué?
>
> ¿Se ve claro en Merchant Center, lo lleva la agencia, o acabáis con el CSV a mano?
>
> Si Merchant Center ya lo dice bien, decídmelo y me ahorro el trabajo.

### D · Agencias españolas de Google Ads — correo o DM, uno a uno

> **Asunto:** Pregunta rápida sobre Merchant Center (no vendo nada)
>
> Hola [nombre]:
>
> Soy estudiante y estoy valorando montar una herramienta de diagnóstico de feeds de Shopping. Antes de escribir código quiero saber si el problema existe de verdad, y vosotros lo veis multiplicado por cliente.
>
> Una sola pregunta: cuando a un cliente le desaprueban parte del catálogo, o el feed no sube y solo aparece "Not Synced", ¿cómo localizáis el producto y el campo concreto que falla? ¿Con la plataforma de feeds que ya uséis, con la Content API, o a mano?
>
> Si la respuesta es "se resuelve en dos minutos y no es un problema", también me sirve y os dejo en paz.
>
> Gracias,
> Javier

### E · Comentario en un hilo ajeno — ayudar primero, preguntar después

No abre hilo. Se usa cuando alguien **ya está describiendo el problema**.

> [Primero, responder de verdad a lo que preguntan, si se sabe.]
>
> Out of curiosity — once you found which product was causing it, how did you track it down? I'm looking at building something small in this area and I'm trying to work out whether that step is actually painful or whether Merchant Center makes it obvious.

**Nunca en el foro de soporte de WordPress.org.** Ahí los hilos son peticiones de ayuda; colar una pregunta propia es secuestrar el hilo y se sanciona. Ese foro es solo de lectura.

### Qué respuesta mata el proyecto

| Respuesta dominante | Lectura |
|---|---|
| "Merchant Center ya te lo dice, mira en Diagnostics" | Hipótesis falsa. Fase 1. |
| "Lo hace la plataforma de feeds que ya pago" | Falsa para el segmento que paga. Queda mirar si hay uno que no paga. |
| "Exporto el CSV y lo miro a mano" | Hipótesis viva. |
| "Es un infierno y no encuentro nada" | Hipótesis viva y con urgencia. |
| Silencio con impresiones altas | Sin dolor. Fase 1. |
| Silencio con impresiones bajas | Sin medir. Otro canal. |

## Requisito previo de la cuenta

Cuenta de Reddit antigua pero con cero interacción. La mayoría de subs de nicho filtran por **karma de comentarios**, no por antigüedad: con 0, el post puede no llegar a publicarse y el silencio resultante no significaría nada.

Antes de publicar, una semana comentando de verdad. Perfil de programador: en r/woocommerce hay preguntas de PHP, hooks, rendimiento y errores de plugins que se pueden responder con conocimiento real. Cinco o seis respuestas útiles bastan.

Normas de cada sub: leerlas en la barra lateral antes de publicar. Varios prohíben investigación de mercado o encuestas incluso sin enlace. Si r/woocommerce lo prohíbe, el canal es directamente los grupos de Facebook en español.

## Distinguir "no hay demanda" de "no lo vio nadie"

El silencio solo concluye algo si el post se vio. Anotar las **impresiones** (Reddit las da en las estadísticas del post; los grupos de Facebook dan alcance):

| Observación | Lectura |
|---|---|
| ~400 vistas, 0 respuestas | Señal real. La puerta no pasa. Fase 1. |
| ~12 vistas, 0 respuestas | No se ha medido nada. Republicar en otro canal. |

Sin ese número, los 14 días no concluyen.

---

## Nota sobre el ejemplo del informe

El EAN de la página, `8412345678901`, tiene dígito de control 1 cuando el correcto es 5. Está puesto a propósito como ejemplo de error, y verificado con el algoritmo EAN-13. Si se cambia el número de ejemplo, hay que recalcularlo: una página que presume de validar checksums no puede fallar el suyo.
