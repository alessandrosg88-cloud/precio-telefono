# 📱 Precio Telefono

Plataforma para coleccionistas TCG (versión app) de [Precio Cartas](https://alessandrosg88-cloud.github.io/precio-cartas/), con una barra de navegación abajo:
🏠 Inicio · 🔎 Buscar · 📦 Selladas · 📐 Centrado PSA · 📚 Colección · 👤 Perfil (Favoritos y Estadísticas desde Inicio y Perfil).

Tiene la misma información que la web original: usa sus datos de precios, traducciones y la misma cuenta (Firebase), así que se actualiza sola cada día.

En el móvil puedes usar «Añadir a pantalla de inicio» para abrirla como una app.

## ✨ Rediseño 2026

- Nueva identidad visual (violeta y oro), **tema claro / oscuro / automático** (botón arriba).
- **Gamificación opcional**: XP, niveles, misiones diarias y semanales, rachas, logros y objetivos de colección (se puede desactivar en Perfil).
- **Ficha de carta**: gráfica de evolución del precio y comparador por plataforma (Cardmarket, TCGplayer, eBay, PriceCharting). No se inventan precios.
- **Mi colección**: valor total, inversión, beneficio/pérdida, cartas más valiosas, evolución del valor, precio y fecha de compra, estado, idioma, listas, filtros y orden.
- **Favoritos con precio objetivo** y aviso al abrir la app.
- **Inicio tipo dashboard**: saludo, valor de la colección y su evolución, progreso, misiones, cartas destacadas, vistas recientemente, evolución del mercado (cartas que sigues) y accesos rápidos.
- **Estadísticas**: cartas y valor por juego, rareza, estado y expansión; las cartas que más suben y bajan.
- **Sellados**: nuevas categorías Tins y Cajas de colección; historial de precio también para productos sellados.

## ⚡ Más dinámica (noviembre 2026)

- **Precios que se actualizan solos**: una vez al día, al abrir la app con la sesión iniciada, una copia invisible de la app vuelve a consultar cada carta de tu colección y favoritos (máx. 60 al día, las más antiguas primero). También desde Perfil → «Actualizar precios ahora» o deslizando hacia abajo en Inicio.
- **Historial en tu cuenta**: cada carta guardada apunta un precio al día en Firestore (`hist`), así la evolución se ve en todos tus dispositivos.
- **Mini gráficas** (sparklines) en cartas destacadas, vistas recientemente y Mi colección.
- **Animaciones**: contador del valor de la colección, barra de XP y nivel, efecto holográfico 3D al mover la carta, esqueletos de carga, confeti al completar misiones, últimos logros en Inicio.
- **App instalable (PWA)**: `manifest.webmanifest`, `sw.js` e iconos. Avisos de precio objetivo como notificación del móvil (Perfil → «Avisos de precio en el móvil»).
- **Deslizar hacia abajo para refrescar** en el móvil.
- **Nombre de usuario único** (Perfil → ✏️): no puede haber dos iguales. Necesita las reglas de `firestore.rules` publicadas en Firebase Console → Firestore → Reglas.

### Qué necesitaría un servidor (no incluido, la web sigue siendo 100 % GitHub Pages)
- Avisos de precio y actualización de precios con la app cerrada (notificaciones push): una función programada (p. ej. Firebase Cloud Functions + Cloud Messaging, plan Blaze) que revise los precios cada día.
- Historial de precios compartido entre dispositivos y de todas las cartas: guardar instantáneas diarias en Firestore o en `data/` con la GitHub Action que ya actualiza los precios.
- Precios de eBay / PriceCharting integrados: requieren sus API con clave privada, que no puede ir en el frontend; habría que llamarlas desde un backend.
- Reconocimiento de cartas por imagen (no solo el código): un servicio de visión artificial en servidor.

## 🃏 Yu-Gi-Oh! (noviembre 2026, igual que la web)

- **Overframe, Starlight, Grand Master Rare y cartas con sello del World Championship** («Emblazoned») como versiones aparte, con su etiqueta, su foto y su precio; botones grandes en la ficha para cambiar entre las versiones del mismo código. En la colección, filtros y «Agrupar: Especiales aparte».
- **Códigos japoneses y de Asia** (LOSP-JP004…), códigos con letra (LDK2-ENK01), con un cero de más (LEDD-ENA001) o con la O cambiada por 0 (EG01-EN001); **expansiones y mazos por código o nombre** (EGO1, LDK2-ENY, «legendary decks 2»), completadas con Yugipedia; botón «Añadir todas a mi colección».
- **Mazos** (en Reglas): «¿Qué mazo puedo hacer?» con tu colección (mazos completos, por arquetipo y de torneo, con las cartas que te faltan), constructor con tus cartas y buscador de mazos de torneo. Usa `mazos.js` y `data/decks.json` de la web.
