# 📊 INTEGRACIÓN DEL FORMULARIO DE ASISTENCIA

El formulario ya está funcionando en la web, pero las confirmaciones se guardan solo en el navegador del usuario. Acá te explico cómo integrarlo con diferentes opciones para que te lleguen las confirmaciones.

---

## ⚡ OPCIÓN 1: Google Sheets (RECOMENDADO - Gratis y fácil)

### Paso 1: Crear Google Apps Script

1. Andá a [Google Sheets](https://sheets.google.com)
2. Creá una nueva planilla llamada "Confirmaciones Cycling ViaAqua"
3. En la primera fila poné estos encabezados:
   ```
   | Fecha | Nombre | Asistencia | Comentarios |
   ```

4. Click en **Extensiones** → **Apps Script**

5. Pegá este código (borrá todo lo que esté ahí):

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    const data = JSON.parse(e.postData.contents);
    
    sheet.appendRow([
      new Date(),
      data.nombre,
      data.asistencia,
      data.comentarios || ''
    ]);
    
    return ContentService
      .createTextOutput(JSON.stringify({ success: true }))
      .setMimeType(ContentService.MimeType.JSON);
      
  } catch (error) {
    return ContentService
      .createTextOutput(JSON.stringify({ success: false, error: error.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

6. Click en **Implementar** → **Nueva implementación**
7. Tipo: **Aplicación web**
8. Ejecutar como: **Yo**
9. Quién tiene acceso: **Cualquier persona**
10. Click **Implementar**
11. **COPIÁ LA URL** que te dan (parece algo así: `https://script.google.com/macros/s/ABC123.../exec`)

### Paso 2: Actualizar el código HTML

En el archivo `index.html`, buscá esta línea (aprox. línea 920):

```javascript
// Ejemplo: await fetch('TU_ENDPOINT', { method: 'POST', body: formData });
```

Reemplazala con:

```javascript
await fetch('TU_URL_DE_GOOGLE_SCRIPT_AQUI', {
    method: 'POST',
    body: JSON.stringify({
        nombre,
        asistencia,
        acompanante,
        comentarios
    }),
    headers: {
        'Content-Type': 'application/json'
    }
});
```

**Reemplazá `TU_URL_DE_GOOGLE_SCRIPT_AQUI` con la URL que copiaste.**

### Paso 3: ¡Listo!

Ahora cada confirmación se guardará automáticamente en tu Google Sheet.

---

## 📧 OPCIÓN 2: Recibir por Email (Google Script + Email)

Si querés recibir un email cada vez que alguien confirme:

### Modificá el script de Google:

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    const data = JSON.parse(e.postData.contents);
    
    // Guardar en sheet
    sheet.appendRow([
      new Date(),
      data.nombre,
      data.asistencia,
      data.comentarios || ''
    ]);
    
    // Enviar email
    const mensaje = data.asistencia === 'si' 
      ? `✅ ${data.nombre} confirmó asistencia`
      : `❌ ${data.nombre} no puede asistir`;
    
    const detalle = `
Nombre: ${data.nombre}
Asistencia: ${data.asistencia}
Comentarios: ${data.comentarios || 'Sin comentarios'}
    `;
    
    MailApp.sendEmail({
      to: 'TU_EMAIL_AQUI@gmail.com', // ⚠️ CAMBIAR ESTO
      subject: `[Cycling ViaAqua] ${mensaje}`,
      body: detalle
    });
    
    return ContentService
      .createTextOutput(JSON.stringify({ success: true }))
      .setMimeType(ContentService.MimeType.JSON);
      
  } catch (error) {
    return ContentService
      .createTextOutput(JSON.stringify({ success: false, error: error.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

⚠️ **No olvides cambiar `TU_EMAIL_AQUI@gmail.com`**

---

## 🔗 OPCIÓN 3: Airtable (Profesional)

Si querés algo más visual:

1. Creá cuenta en [Airtable.com](https://airtable.com) (gratis)
2. Creá una base con campos: Nombre, Asistencia, Acompañante, Comentarios
3. Generá un API key
4. Usá su API para guardar: https://airtable.com/api

---

## 📊 VER LAS CONFIRMACIONES

### Método 1: Google Sheets
Simplemente abrí tu planilla de Google y vas a ver todas las confirmaciones en tiempo real.

### Método 2: En el navegador (temporal)
Abrí la consola del navegador (F12) y escribí:
```javascript
JSON.parse(localStorage.getItem('confirmaciones'))
```

Esto te muestra todas las confirmaciones guardadas localmente (solo en ese navegador).

---

## 🔒 SEGURIDAD

**Importante:** 
- El endpoint de Google Apps Script es público, pero solo puede recibir datos
- No expongas información sensible
- Google Script tiene límites de uso (pero son generosos para este caso)

---

## 💡 TROUBLESHOOTING

**"No me llegan las confirmaciones"**
1. Verificá que hayas copiado bien la URL del Google Script
2. Asegurate de haber dado permisos en Google Script
3. Revisá la consola del navegador (F12) para ver errores

**"Error de CORS"**
- Asegurate de haber configurado "Cualquier persona" en los permisos del Google Script
- Esperá 1-2 minutos después de hacer cambios en el script

**"No funciona el email"**
- Verificá que pusiste tu email correcto
- Gmail puede bloquearlo si mandás muchos emails rápido (está limitado)

---

## 🎯 RESUMEN RÁPIDO

**Recomendado:** Google Sheets (gratis, automático, organizado)
**Profesional:** Airtable o backend propio

---

¿Necesitás ayuda para configurar alguna opción? Avisame y te guío paso a paso.
