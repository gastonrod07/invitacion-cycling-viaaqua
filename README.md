# 🚴‍♂️ Invitación Cycling ViaAqua - Primera Juntada 2026

Invitación web para la primera juntada del año del grupo de Cycling ViaAqua con el instructor Lucas Rovira.

## 🚀 Deploy en Vercel

### Opción 1: Deploy desde la terminal (Recomendado)

1. **Instalá Vercel CLI** (si no lo tenés):
```bash
npm i -g vercel
```

2. **Logueate en Vercel**:
```bash
vercel login
```

3. **Deployá el proyecto**:
```bash
cd invitacion-cycling-viaaqua
vercel --prod
```

4. Seguí las instrucciones en la terminal:
   - Set up and deploy? **Y**
   - Which scope? Elegí tu cuenta
   - Link to existing project? **N**
   - Project name? `invitacion-cycling-viaaqua` (o el que quieras)
   - In which directory? **.**
   - Override settings? **N**

5. ¡Listo! Te va a dar una URL tipo: `https://invitacion-cycling-viaaqua.vercel.app`

---

### Opción 2: Deploy desde el Dashboard de Vercel

1. Andá a [vercel.com](https://vercel.com)
2. Click en **"Add New Project"**
3. Click en **"Import Third-Party Git Repository"** o directamente **"Upload"**
4. Arrastrá la carpeta `invitacion-cycling-viaaqua`
5. Click en **"Deploy"**
6. ¡Listo! En segundos va a estar online

---

### Opción 3: Deploy desde GitHub (Más profesional)

1. **Creá un repo en GitHub:**
   - Andá a github.com
   - New repository → `invitacion-cycling-viaaqua`

2. **Subí el código:**
```bash
cd invitacion-cycling-viaaqua
git init
git add .
git commit -m "Primera juntada Cycling ViaAqua 2026"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/invitacion-cycling-viaaqua.git
git push -u origin main
```

3. **Conectá con Vercel:**
   - Andá a [vercel.com/new](https://vercel.com/new)
   - Import Git Repository
   - Elegí tu repo
   - Deploy

---

## 📱 Compartir la invitación

Una vez deployada, vas a tener una URL como:
```
https://invitacion-cycling-viaaqua.vercel.app
```

### Para compartir en WhatsApp:

**Opción A: Link directo**
```
🚴‍♂️ PRIMERA JUNTADA 2026 - CYCLING VIAAQUA 🎉

Mirá la invitación acá:
👉 https://tu-url.vercel.app

📅 Miércoles 15 de abril - 20:00 hs
🍽️ Cena + el permitido de la semana 🍺🍷

Por favor CONFIRMEN ASISTENCIA:
✅ VOY
❌ NO PUEDO
```

**Opción B: Link acortado**

Usá [bit.ly](https://bitly.com) o [tinyurl.com](https://tinyurl.com) para acortar la URL:
```
https://invitacion-cycling-viaaqua.vercel.app
→ https://bit.ly/cycling-viaaqua-2026
```

---

## 🔄 Actualizar la invitación

Si necesitás cambiar algo (ej: lugar, hora):

1. Editá `index.html`
2. Volvé a deployar:
```bash
vercel --prod
```

La URL se mantiene, solo se actualiza el contenido.

---

## ⚙️ Configuración del proyecto

- **Framework:** HTML estático
- **Archivos:**
  - `index.html` - Invitación principal
  - `vercel.json` - Configuración de Vercel
  - `package.json` - Metadata del proyecto

---

## 🎨 Características de la invitación

- ✅ Caricatura personalizada de Lucas
- ✅ Diseño responsive (mobile/tablet/desktop)
- ✅ Animaciones fluidas
- ✅ Info de clases semanales
- ✅ Link a Instagram de Lucas
- ✅ **Formulario de confirmación de asistencia**
- ✅ Optimizada para compartir

---

## 📝 Configurar el Formulario de Asistencia

El formulario está listo para usar. Para que las confirmaciones se guarden automáticamente:

1. Seguí la guía en `INTEGRACION_FORMULARIO.md`
2. Creá un Google Sheet
3. Configurá Apps Script
4. Actualizá la URL en el código

**Sin integración:** Las confirmaciones se guardan solo en el navegador del usuario (localStorage).

**Con integración:** Recibís todas las confirmaciones en una planilla automáticamente (+ emails opcionales).

Ver `INTEGRACION_FORMULARIO.md` para guía completa paso a paso.

---

## 💡 Tips

1. **Dominio custom:** Podés configurar un dominio propio en Vercel (ej: `cycling-viaaqua.com`)
2. **Analytics:** Activá Vercel Analytics para ver cuánta gente vio la invitación
3. **Preview:** Cada deploy te genera un preview link para testear antes de publicar

---

¡Que sea una juntada increíble! 🚴‍♂️🔥

#CyclingViaAqua2026
# invitacion-cycling-viaaqua
