# SPEC — Refactor "El ingeniero que necesitas" (Stitch → index.html)

## Objetivo
Refactorizar el portafolio para que la primera impresión sea "este es el ingeniero que necesito en mi equipo", adoptando la dirección visual generada en Google Stitch (estudio `projects/8398024866874220177`) pero **con los datos reales** del portafolio.

## Requisitos exactos
1. Adoptar el layout/copy de Stitch: nav flotante, hero 7/5 con terminal de producción, marquesina tech, franja de impacto de 4 métricas, proyectos como casos de estudio (bento asimétrico), experiencia editorial, stack en 6 módulos, cierre de alta conversión, footer tipo sistema.
2. **Prohibido inventar datos.** Se mantiene contenido verificado: email `hannejosebayehvillarreal@gmail.com`, tel `+57 310 540 4522`, roles y fechas reales (MOVii L2 jun 2025–presente; MOVii Monitoreo oct 2023–jun 2025; Grupo IT ago 2022–feb 2023; Ferrum/DANE 2018–2020), métricas reales (-92%, 85%→97%, -30%, -40%, +25%, 8h/sem), stack real, 51 repos, 5+ años, Mongo/MySQL/Oracle/SQL.js/Tesseract (no Redis/AWS/Prometheus/LangChain/Postgres).
3. Mantener SEO y social: `canonical`, `robots`, Open Graph, Twitter Card, `theme-color`, favicon, JSON-LD `Person`/`WebSite`.
4. Mantener accesibilidad: skip link, landmarks, `aria-label`, `focus-visible`, `prefers-reduced-motion`, decorativos `aria-hidden`, contraste.
5. Mantener UX: scrollspy, botón subir, copiar email, menú móvil (Esc/clic fuera/scroll-lock), contadores animados, año dinámico, formulario `mailto:`.
6. Sin dependencias nuevas ni Tailwind CDN: HTML+CSS+JS único, CSS propio (como el repo actual).

## No-objetivos
- No se usa `mailto` real nuevo ni backend.
- No se implementa la sección "consultor independiente 2020–2022" (no verificable).
- No se publica/commitea.

## Criterios de aceptación (verificables)
1. `index.html` sin etiquetas desbalanceadas ni IDs duplicados (script `html.parser`).
2. JSON-LD parsea como JSON válido.
3. Todo `href="#..."` resuelve a un `id` existente.
4. Presentes `rel="canonical"`, `og:title`, `og:image`, `twitter:card`, `theme-color`.
5. Secciones con id: `impacto`, `trabajo`, `experiencia`, `stack`, `contacto`.
6. Sin cadenas inventadas por Stitch: `engineering.ops`, `Redis`, `AWS`, `Prometheus`, `LangChain`, `400+`, `250+`, `SLA 99.9`, `42 microservicios`, `2020 — 2022`.
7. Bloque `@media (prefers-reduced-motion:reduce)` presente y respetado en JS.
8. Sin `console.log` de debug ni `TODO`.

## Asunciones
- El email y datos de contacto se mantienen del sitio previo (única fuente real).
- El hero dice "5+ años" (no "6+" que inventó Stitch).
- Los repos se enlazan a GitHub; no hay URLs de demo inventadas.

## Riesgos y rollback
- Riesgo: archivo único grande. Mitigación: verificación estática + prueba en navegador.
- Rollback: `git restore index.html SPEC.md`.
