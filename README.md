# SinpeQR

App Android para cobrar/pagar vía SINPE Móvil con QR y envío por SMS.

## Características
- Generar QR con formato `pase <monto> <telefono> [descripcion]`.
- Escaneo con ZXing (JourneyApps).
- Envío SMS directo (shortcode configurable, por defecto 2627 / BNCR y 7070-7474 / Davivienda).
- Historial local (Room).
- PIN de protección (EncryptedSharedPreferences).
- Botón “Compartir QR”.

## Requisitos
- Android Studio (Giraffe/Koala o más reciente).
- JDK 17 (o el que pida tu AGP).
- `compileSdk=34`, `minSdk=24`.

## Cómo compilar
1. Clona o descomprime el proyecto.
2. Abre en Android Studio.
3. **Build > Make Project** o `./gradlew assembleDebug`.
4. APK: `app/build/outputs/apk/debug/app-debug.apk`.

## Permisos
- `CAMERA` para el escáner.
- `SEND_SMS` para enviar SINPE por SMS.

## Pruebas rápidas
- Configura teléfono receptor en **Menú (⋮) > Configuración**.
- “Cobrar”: ingresa monto y (opcional) descripción → genera QR.
- “Pagar”: escanea ese QR → confirma → “ENVIAR SINPE”.
- Verifica en **Historial**.

## Librerías
- ZXing Android Embedded (JourneyApps)
- Room (AndroidX)
- Material Components
- Security Crypto (EncryptedSharedPreferences)

## Nota
No se incluye ningún keystore de firma ni credenciales sensibles.
