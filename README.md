# Speed Laundry Caja

App web para la recaudación semanal de **Speed Laundry Shop**: el efectivo de cada máquina los viernes, la tarjeta, las lecturas mensuales de cada máquina y el informe trimestral para el asesor (Excel).

- `index.html`: la app completa
- `firebase-config.js`: la configuración de tu proyecto Firebase
- `firestore.rules`: las reglas de seguridad (solo tu correo puede ver y cambiar los datos)
- `manifest.json`, `sw.js` e iconos: para instalarla en el móvil y abrirla sin conexión

Los datos **no** están en este repositorio. Se guardan en Firebase, protegidos con tu cuenta.

---

## 1 · Crear el proyecto Firebase (unos 5 minutos)

1. Entra en <https://console.firebase.google.com> → **Crear un proyecto** → nombre `speed-laundry` (Google Analytics: no hace falta).
2. **Authentication** → *Comenzar* → *Método de acceso* → **Correo electrónico/contraseña** → activar → Guardar.
3. **Authentication** → *Usuarios* → **Agregar usuario**: correo `linuxielaxl@gmail.com` y, como contraseña, **tu clave de acceso a la app**. Es la única clave que te pedirá la app al abrirla.
4. **Authentication** → *Configuración* → **Dominios autorizados** → *Agregar dominio*: `linuxielaxljhonn.github.io`
5. **Firestore Database** → *Crear base de datos* → ubicación `europe-west1` (Bélgica) o la más cercana → *Modo de producción*.
6. **Firestore Database** → pestaña **Reglas** → borra lo que haya, pega el contenido de `firestore.rules` → **Publicar**.
7. **Configuración del proyecto** (rueda dentada) → *Tus apps* → icono **`</>`** (Web) → nombre `speed-laundry` → *Registrar app*.
   Te enseña un bloque `const firebaseConfig = { apiKey: ..., authDomain: ..., ... }`. **Copia esos valores** en `firebase-config.js` (o pásaselos a Claude).

> Los valores de `firebaseConfig` no son secretos: identifican el proyecto. Lo que protege los datos son las reglas del paso 6 y tu contraseña.

## 2 · Publicar en GitHub Pages

1. Sube estos archivos a la raíz del repositorio `speed-laundry`.
2. En GitHub: **Settings** → **Pages** → *Source*: **Deploy from a branch** → rama `main`, carpeta `/ (root)` → Save.
3. Al cabo de un minuto la app estará en: **<https://linuxielaxljhonn.github.io/speed-laundry/>**

## 3 · Instalarla en el móvil

- **iPhone (Safari):** abre la dirección → botón Compartir → **Añadir a pantalla de inicio**.
- **Android (Chrome):** abre la dirección → menú ⋮ → **Instalar aplicación**.

## Uso

- **Viernes:** al cerrar, apunta el efectivo de cada máquina y el total de tarjeta de la semana → *Guardar*.
- **Historial:** todos los viernes del año, con el total de cada mes.
- **Máquinas:** cada 3 meses, copia lo que marca la configuración de cada máquina, mes a mes.
- **Asesor:** elige el trimestre → *Descargar Excel* (lecturas por máquina y mes, recaudación y detalle de los viernes).

Cada viernes cuenta en el mes en que cae. Si cambias de correo, cámbialo en `firestore.rules` y vuelve a publicar las reglas en Firebase.
