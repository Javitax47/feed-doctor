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

## Publicar, coste 0 €

GitHub Pages sirve HTML estático gratis. El dominio de 10 € es opcional y puede esperar a que la puerta pase.

```
cd C:\Users\Javier\Desktop\Income\feed-doctor
git init
git add -A
git commit -m "landing: feed doctor demand test"
gh repo create feed-doctor --public --source=. --remote=origin --push
gh api -X POST repos/Javitax47/feed-doctor/pages -f "source[branch]=master" -f "source[path]=/"
```

Queda en `https://javitax47.github.io/feed-doctor/`.

**Antes de publicar**: crear cuenta gratuita en formspree.io y sustituir `REEMPLAZAR` en el `action` del formulario. Sin eso el formulario no recoge nada.

---

## Texto para los canales en español

**Post en grupo de WooCommerce / Reddit español** — pregunta, no anuncio:

> ¿Cómo averiguáis **qué productos concretos** os está rechazando Merchant Center?
>
> Google te dice "340 productos desaprobados por datos de producto" y se queda tan ancho. Para encontrar cuáles y por qué he acabado exportando el CSV y revisándolo a mano, y con 2.000 referencias es inviable.
>
> Las dos causas que más veo son el precio del feed sin coincidir con el de la página —normalmente IVA incluido contra IVA excluido— y EAN con el dígito de control mal.
>
> ¿Lo estáis resolviendo con alguna herramienta o también a mano? Estoy pensando en montarme algo y prefiero preguntar antes de perder el tiempo.

**Regla al responder**: si alguien pregunta qué estás montando, entonces sí enlazas. Si no pregunta nadie, el enlace no aparece — y eso es información, no fracaso.

---

## Nota sobre el ejemplo del informe

El EAN de la página, `8412345678901`, tiene dígito de control 1 cuando el correcto es 5. Está puesto a propósito como ejemplo de error, y verificado con el algoritmo EAN-13. Si se cambia el número de ejemplo, hay que recalcularlo: una página que presume de validar checksums no puede fallar el suyo.
