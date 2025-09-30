# Demoblaze E2E – Playwright + TypeScript

**Lenguaje + framework:** TypeScript + [Playwright Test](https://playwright.dev/)

Automatización end-to-end del flujo:
1) Login  
2) Agregar producto al carrito  
3) Validar en carrito  
4) Logout

## Requisitos
- Node.js 18+
- (Opcional) Git

## Instalación
```bash
npm install
npx playwright install

## como ejecutar
npm run test:headed

## codigo base
import { test, expect } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://www.demoblaze.com/');
  await page.getByRole('link', { name: 'Log in' }).click();
  await page.locator('#loginusername').click();
  await page.locator('#loginusername').fill('iydtester');
  await page.locator('#loginpassword').click();
  await page.locator('#loginpassword').fill('IYD05');
  await page.getByRole('button', { name: 'Log in' }).click();
  await page.getByRole('link', { name: 'Welcome iydtester' }).click();
  await page.locator('div:nth-child(2) > .card > a').click();
  page.once('dialog', dialog => {
    console.log(`Dialog message: ${dialog.message()}`);
    dialog.dismiss().catch(() => {});
  });
  await page.getByRole('link', { name: 'Add to cart' }).click();
  await page.getByRole('link', { name: 'Cart', exact: true }).click();
  await page.getByRole('button', { name: 'Place Order' }).click();
  await page.getByLabel('Place order').getByText('Close').click();
  await page.getByRole('link', { name: 'Log out' }).click();
});