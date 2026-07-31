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

**Post en grupo de WooCommerce / Reddit español** — pregunta, no anuncio. Reescrito tras el paso 1 con el vocabulario que usa la gente de verdad, y deliberadamente abierto a los dos problemas para no inducir la respuesta:

> Cuando Merchant Center no os sube los productos, ¿cómo averiguáis por qué?
>
> Me refiero a los dos casos. El panel que pone **Active 0, Pending 0, Disapproved 0, Not Synced 262** y ninguna pista de qué pasa. Y el otro, cuando sí suben pero te desaprueban una parte y solo te dicen "problemas de datos de producto", sin decirte cuáles.
>
> Yo he acabado exportando el CSV y mirándolo a mano. Con 200 referencias es tedioso; con 2.000 es inviable.
>
> ¿Lo resolvéis con alguna herramienta, con la agencia, o a mano como yo? Pregunto antes de ponerme a montar nada.

**Por qué está redactado así**: menciona los dos síntomas con las palabras exactas del foro —`Not Synced`, `Disapproved 0`— sin decidir cuál duele más. Si responden mayoritariamente sobre uno, eso decide el producto. Si el post afirmara cuál es el problema, la respuesta ya no sería información.

**Regla al responder**: si alguien pregunta qué estás montando, entonces sí enlazas. Si no pregunta nadie, el enlace no aparece — y eso es información, no fracaso.

---

## Nota sobre el ejemplo del informe

El EAN de la página, `8412345678901`, tiene dígito de control 1 cuando el correcto es 5. Está puesto a propósito como ejemplo de error, y verificado con el algoritmo EAN-13. Si se cambia el número de ejemplo, hay que recalcularlo: una página que presume de validar checksums no puede fallar el suyo.
