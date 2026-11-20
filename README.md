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

### Qué necesitaría un servidor (no incluido, la web sigue siendo 100 % GitHub Pages)
- Avisos de precio con la app cerrada (notificaciones push): una función programada (p. ej. Firebase Cloud Functions + Cloud Messaging, plan Blaze) que revise los precios cada día.
- Historial de precios compartido entre dispositivos y de todas las cartas: guardar instantáneas diarias en Firestore o en `data/` con la GitHub Action que ya actualiza los precios.
- Precios de eBay / PriceCharting integrados: requieren sus API con clave privada, que no puede ir en el frontend; habría que llamarlas desde un backend.
- Reconocimiento de cartas por imagen (no solo el código): un servicio de visión artificial en servidor.
