# Demoblaze E2E con Playwright (JS)

**Lenguaje + framework:** JavaScript + Playwright.

## Casos cubiertos
1. Abrir https://www.demoblaze.com
2. Login con usuario de prueba (`ydtester / !YD05`)
3. Validar que aparece `Welcome ydtester` en la barra superior
4. Abrir un producto y agregar al carrito
5. Validar en el carrito que el producto se agregó
6. Cerrar sesión

## Cómo correrlo (local)
1. Instalar Node.js (v18+).
2. Clonar o descargar este repo.
3. Instalar dependencias:
   ```bash
   npm install
   npx playwright install
