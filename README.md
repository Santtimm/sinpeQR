# SinpeQR — Cobros y pagos por QR vía SINPE Móvil (SMS) :)

App Android súper simple para **cobrar** y **pagar** con SINPE Móvil usando **QR + SMS**, pensada para personas mayores y comercios de bajo volumen.  
- Botones grandes y contraste alto.  
- Flujo de **Cobrar**: monto → QR → compartir / nuevo / inicio.  
- Flujo de **Pagar**: escanear → confirmar → **enviar SINPE** (SMS) → éxito.  
- Seguridad: PIN local, bloqueo de doble toque/escaneo, datos cifrados en el dispositivo, historial local.

> **Privacidad:** nada sale del teléfono salvo el SMS del banco.

---

## ✨ Funcionalidades
- **Generación de QR** con formato `pase <monto> <tel> <desc>` (desc opcional, sin espacios).
- **Escaneo de QR** (ZXing) con **antidoble-disparo** (AtomicBoolean).
- **Envío de SINPE por SMS** directo (BNCR 2627 por defecto; Davivienda 7070-7474 disponible).
- **Historial local** (Room) con monto, destino, fecha/hora, estado y descripción.
- **PIN de acceso** (EncryptedSharedPreferences + hash) con flujo de “Olvidé mi PIN” que **resetea** datos locales.
- **UI accesible**: tipografías grandes, botones 64dp+, colores de alto contraste, modo claro forzado.

---

## 🧭 Flujo de uso
**Cobrar**
1. Inicio → **Cobrar**  
2. Digita monto (enter abre teclado numérico, sin decimales) y descripción (máx 10, sin espacios).  
3. **Generar QR** → mostrar QR → **Compartir / Nuevo / Volver al inicio**.

**Pagar**
1. Inicio → **Pagar** → abre cámara (por defecto).  
2. Lee QR → **Confirmar pago** (monto, destino, descripción).  
3. **Enviar SINPE** (SMS) → pantalla de **éxito** → volver al inicio.

---

## 📸 Capturas (en orden)

| Pantalla | Captura |
|---|---|
| 01. Inicio | ![Inicio](/01_home.jpg) |
| 02. Menú (⋮) | ![Menú](/02_overflow.jpg) |
| 03. PIN | ![PIN](/03_pin.jpg) |
| 04. Olvidé mi PIN | ![Olvidé PIN](04_forgot_pin.jpg) |
| 05. Configuración | ![Configuración](/05_config.jpg) |
| 06. Historial | ![Historial](/06_history.jpg) |
| 07. Cobrar (monto) | ![Cobrar Monto](/07_cobrar_input.jpg) |
| 08. Importar de galeria | ![QR](/08_qr.jpg) |
| 09. Scanner | ![Scanner](/09_scanner.jpg) |
| 10. Confirmar pago | ![Confirmar](/10_confirm.jpg) |
| 11. Éxito | ![Exito](/11_success.jpg) |
| 12. QR |  [Compartir](/12_share.jpg) |


---

## 🏗️ Stack técnico
- **Kotlin + AndroidX + Material3**
- **ZXing (JourneyApps)** para QR
- **Room** para historial
- **EncryptedSharedPreferences** (+ MasterKey) para PIN y config
- **ViewBinding / findViewById** simple
- **Permisos**: Cámara y, opcional, SMS

---

## ⚙️ Compilar y ejecutar
1. Android Studio Giraffe / Jellyfish+ (API 34 recomendado).  
2. Abre el proyecto y sincroniza Gradle.  
3. Ejecuta en un dispositivo Android 7.0+ (API 24+).  
4. En el primer uso, ve a **⋮ → Configuración** y guarda:  
   - **Teléfono** del que cobra  
   - **Banco del pagador** (BNCR 2627 o Davivienda 7070-7474)  
5. Otorga permisos cuando los pida (Cámara y **Enviar SMS** si vas a pagar).

---

## 🔐 Seguridad
- **PIN** requerido para entrar a Configuración.  
- **Olvidé mi PIN** → borra PIN, configuración e historial local (recuperable reconfigurando).  
- **Antidoble-clic** en *Enviar SINPE* y **antidoble-escaneo**.  
- **Sin backend**: minimiza superficie de ataque.  
- **Cifrado de preferencias**: MasterKey AES256 + EncryptedSharedPreferences.

---

## 🏦 Bancos soportados (SMS corto)
- **BNCR** — `2627` (por defecto)  
- **Davivienda** — `7070-7474`  

---

## 🚧 Limitaciones actuales
- Pago por **SMS** (no API bancaria).  
- No valida respuesta del banco (se registra como **SENT** o **FAILED** por envío).  
- Descripción sin espacios (máx. 10 chars) por compatibilidad de formato.

---

## 🗺️ Roadmap
- Confirmación de entrega (lectura de SMS del banco, si el usuario lo permite).  
- Múltiples bancos con autodetección.  
- Exportar historial (CSV/WhatsApp/Correo).  
- Modo **cajero** (PIN sólo para configuración).  
- Versión iOS (lector QR + deeplink a app de SMS).

---

## 📦 Entrega para hackathon
- **APK de demo** (`/release/SinpeQR-demo.apk`)  
- **Video 60 s** mostrando flujos Cobrar y Pagar  
- **Pitch Deck** (`/docs/pitch_deck.md`)  
- **Guion 60 s** (`/docs/pitch_60s.md`)

---

## 📝 Licencia
MIT — úsalo, modifícalo y contribuye.
