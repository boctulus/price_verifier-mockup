# Reemplazar Placeholders con Imágenes Reales

Sustituir los 3 elementos SVG/CSS placeholder por referencias a archivos de imagen independientes generados con IA.

---

## Imágenes a generar

| Archivo | Contenido | Fondo | Usado en |
|---|---|---|---|
| `ecuenta-card.png` | Tarjeta de crédito estilo eCuenta (gradiente morado-azul-amarillo, chip dorado, texto "eCuenta" abajo) | Transparente | `before-scanning` — `div.card-placeholder` |
| `acuenta-logo.png` | Logo "SuperBodega aCuenta®" tipografía Nunito, color rojo `#c0392b`, "a" grande en cursiva | Transparente | `after-scanning` — `div.col-logo` |
| `acuenta_logo_black.png` | Mismo logo en **blanco** para el footer rojo | Transparente | Footer de todas las vistas |

Todos los archivos se guardan en:
`D:\Desktop\COTIZACIONES\SOFT POS (POINT OF SALE)\!PRICE-VERIFIER\assets\`

---

## Cambios HTML — 3 archivos

### [MODIFY] index.html
- `div.card-placeholder` → `<img src="./assets/ecuenta-card.png" class="ecuenta-card-img" alt="Tarjeta eCuenta"/>`
- `svg.acuenta-logo-svg` → `<img src="./assets/acuenta-logo.png" class="acuenta-logo-svg" alt="SuperBodega aCuenta"/>`
- Ambos `svg.footer-logo-svg` → `<img src="./assets/acuenta_logo_black.png" class="footer-logo-svg" alt="aCuenta"/>`

### [MODIFY] before-scanning/kiosko.html
- `div.card-placeholder` → `<img src="../assets/ecuenta-card.png" .../>`
- `svg.footer-logo-svg` → `<img src="../assets/acuenta_logo_black.png" .../>`

### [MODIFY] after-scanning/kiosko-precio.html
- `svg.acuenta-logo-svg` → `<img src="../assets/acuenta-logo.png" .../>`
- `svg.footer-logo-svg` → `<img src="../assets/acuenta_logo_black.png" .../>`

---

## CSS ajustado

- `.ecuenta-card-img`: `width:90px; height:58px; border-radius:7px; object-fit:cover; box-shadow:..;`
- `.acuenta-logo-svg` (reutilizada): `width:210px; height:auto; object-fit:contain;`
- `.footer-logo-svg` (reutilizada): `width:110px; height:auto; object-fit:contain;`
- Eliminar reglas de `.card-placeholder`, `.card-chip`, `.card-logo` (ya no hacen falta)

---

## Verificación

1. Abrir [index.html](file:///D:/Desktop/COTIZACIONES/SOFT%20POS%20%28POINT%20OF%20SALE%29/%21PRICE-VERIFIER/index.html) — verificar que aparecen las 3 imágenes (tarjeta, logo principal, footer)
2. Abrir [before-scanning/kiosko.html](file:///D:/Desktop/COTIZACIONES/SOFT%20POS%20%28POINT%20OF%20SALE%29/%21PRICE-VERIFIER/before-scanning/kiosko.html) — tarjeta + footer logo
3. Abrir [after-scanning/kiosko-precio.html](file:///D:/Desktop/COTIZACIONES/SOFT%20POS%20%28POINT%20OF%20SALE%29/%21PRICE-VERIFIER/after-scanning/kiosko-precio.html) — logo principal + footer logo
