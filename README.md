# FC27 Trader — prototipo PWA

## Incluye
- Interfaz adaptable a móvil con diseño claro.
- Radar de cartas con señales orientativas.
- Calculadora de rentabilidad con impuesto EA del 5%.
- Registro de operaciones y cartera.
- Exportación de respaldo JSON.
- Instalación PWA y caché offline básica.
- Solicitud de permiso de notificaciones del navegador.

## Limitaciones importantes
Esta entrega **no está conectada a una API de precios**. Las cartas de ejemplo son datos editables y no deben tratarse como cotizaciones actuales. La señal Comprar/Mantener/Evitar es una regla heurística sencilla, no asesoramiento ni garantía de rentabilidad.

La app guarda datos en `localStorage` del navegador. Eso la hace local al dispositivo, pero no equivale a autenticación ni a cifrado: no es adecuada para guardar secretos. No hay backend, cuenta de usuario ni sincronización.

Las notificaciones locales funcionan cuando el navegador/app puede ejecutar el código; no hay un servicio push de fondo. Para notificaciones push fiables se necesita backend, suscripción Push y VAPID.

## Ejecutar localmente
Se requiere servir la carpeta desde `localhost` (no abrir `index.html` directamente), por ejemplo:

```bash
python -m http.server 8000
```

Abrir `http://localhost:8000`.

## Instalar en Android
1. Publica el sitio mediante HTTPS (por ejemplo, Vercel).
2. Abre la URL en Chrome Android.
3. Menú ⋮ → Instalar aplicación / Añadir a pantalla de inicio.

## Siguiente fase: datos automáticos y privacidad real
1. Elegir un proveedor de datos que permita expresamente uso de API y uso comercial/personal deseado.
2. Crear un backend privado (por ejemplo, Supabase Edge Function o servidor propio) que guarde la clave del proveedor en variables secretas.
3. Proteger acceso con autenticación y políticas RLS.
4. Normalizar plataforma, carta, versión, precio, timestamp y fuente.
5. Programar actualizaciones y validar retrasos, cobertura y límites.
6. Implementar Web Push real con VAPID y guardar suscripciones por usuario.

No pongas claves API en `app.js`, `index.html` ni en el navegador.
