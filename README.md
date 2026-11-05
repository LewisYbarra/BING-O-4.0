# BING-O 4.0 (alpha 1)
### Banco de Inversión Nacional de GENTES - Organización

> **Modernización web de la legendaria hoja de cálculo compartida BING-O (v1.0 → v3.2).**  
> Diseñado como una Progressive Web App (PWA) móvil para repartir gastos entre amigos, liquidar deudas vía Bizum con transferencias mínimas y mantener indicadores de riesgo macroeconómico en tiempo real.

---

## Historia

Entre julio de 2020 y octubre de 2026, el grupo organizó sus finanzas mediante un libro contable en Google Sheets (`BING-O cp..xlsx`):
* **628 transacciones reales registradas**.
* **Más de 10.000 € de volumen acumulado** adelantado entre miembros.
* Múltiples iteraciones de diseño, desde la disposición horizontal de la v1.0 hasta los controles macroeconómicos y fórmulas de riesgo de la v3.2.

**BING-O 4.0** traslada toda esa contabilidad a una aplicación web moderna, alojada sin coste en **Vercel** y sincronizada en tiempo real mediante **Google Firebase Firestore**, eliminando para siempre las fórmulas rotas, la pérdida de decimales y las complicaciones en móviles iOS/Android.

---

## Características Principales

### 1. Reparto sin descuadres (`D.G. = 0,00 €`)
* **3 modos de registro:**
  * **Partes iguales:** Selecciona pagador, importe y quiénes estaban. El algoritmo distribuye los céntimos indivisibles de forma rotativa y transparente para que la suma de la fila sea siempre exactamente `0,00 €`.
  * **Modo manual:** Entrada libre para gastos desglosados (ej. comidas con importes distintos) con detector de descuadre en vivo.
  * **Bizum:** Liquidaciones directas entre deudor y acreedor.
* **Jurisprudencia Fila 436:** Validación estricta de fechas con homenaje al mítico apunte del *Kibap*.

### 2. Liquidador de Bizums Óptimo
* Algoritmo de minimización de transferencias que calcula el camino más corto para saldar todas las deudas del grupo en el menor número de pagos posible.
* Botón de liquidación rápida en 1 clic.

### 3. Panel Macroeconómico BCE
* **Crédito en Circulación:** Monitoriza la deuda viva total del grupo ($\frac{\sum \vert{}S_i\vert{}}{2}$).
* **Error Cuadrático Medio (ECM):** Mide la dispersión del endeudamiento sin sesgo ($\sqrt{\frac{\sum S_i^2}{N}}$).
* **Riesgo Absoluto (R.A.) y Relativo:** Indicador ponderado frente al máximo histórico registrado.
* **Protocolo MAFTA dinámico:** Botón inteligente que detecta descuadres residuales y limpia milésimas automáticamente entre el núcleo duro.

### 4. Seguridad & Trazabilidad
* **Acceso con cuenta de Google:** Autenticación a nivel de base de datos (`Firestore Rules`).
* **Firma de autoría:** Cada gasto guarda quién lo ha registrado en el grupo.
* **Cero borrados físicos (`Soft Delete`):** Prohibido el borrado destructivo. Los gastos anulados quedan tachados en el historial indicando el autor y la hora de anulación, con opción de restauración.

---

## Stack Tecnológico

* **Frontend:** HTML5 semántico, JavaScript Vanilla (ES6 Modules).
* **Estilos:** [Tailwind CSS](https://tailwindcss.com/) (CDN) en modo oscuro nativo, Google Fonts (`Inter` y `JetBrains Mono`).
* **Iconos:** [FontAwesome 6](https://fontawesome.com/).
* **Base de datos:** [Google Firebase Firestore](https://firebase.google.com/).
* **Despliegue / Hosting:** [Vercel](https://vercel.com/) (estático, gratuito).
