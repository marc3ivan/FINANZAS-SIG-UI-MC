# 🗺️ Cartografía PRO · Gestión para Maperos SIG

![Versión](https://img.shields.io/badge/versión-6.0-blue)
![Plataforma](https://img.shields.io/badge/platform-web%20%7C%20local-darkgreen)
![País](https://img.shields.io/badge/Paraguay-🇵🇾-red)

Sistema financiero profesional para **cartógrafos SIG, topógrafos y maperos independientes**. Controla clientes, proyectos, pendientes de cobro, pagos a maperos y estadísticas en tiempo real. Todo funciona **100% offline** en tu navegador — tus datos viven en tu disco.

<p align="center">
  <img src="https://via.placeholder.com/800x450?text=Cartografía+PRO+-+Dashboard+de+finanzas+para+Maperos+SIG" alt="Vista previa del dashboard" width="800">
</p>

---

## 🚀 Características

| Módulo | Función |
|--------|---------|
| **Clientes** | Registro de consultoras con WhatsApp directo |
| **Proyectos** | Cada proyecto tiene: nombre, mapero asignado, láminas, costo por lámina |
| **Cobros** | Marcar/desmarcar pagos recibidos, resumen por cliente |
| **Pagos a Maperos** | Control de quién ya fue pagado y quién no |
| **Estadísticas** | Total bruto, pendiente de cobro, ya cobrado |
| **Multilenguaje** | 🇵🇾 Español · 🇺🇸 English · 🇹🇼 中文 |
| **Backup / Restore** | Exporta/importa JSON, vincula archivo del sistema |

---

## 💾 RESPALDO DE DATOS — LEE ESTO PRIMERO

> ⚠️ **IMPORTANTE:** El navegador guarda los datos automáticamente, pero si borras caché o cookies, **los perderás**. Siempre haz backup.

### 📁 Cómo hacer backup manual (recomendado)

1. Dentro de la app, haz clic en **`💾 Backup`** (arriba a la derecha)
2. Se descargará un archivo `carto_v6.json`
3. Guárdalo en una carpeta segura, por ejemplo:
   - `Documentos / CartografiaPRO / backups /`
   - O en tu nube (Google Drive, Dropbox, OneDrive)

### 📂 Cómo restaurar un backup

1. Presiona **`📂 Importar`** en la app
2. Selecciona tu archivo `carto_v6.json`
3. Los datos se cargarán automáticamente

### 🔗 Vincular archivo del sistema (funcionalidad avanzada)

Si quieres que la app **auto-guarde** directamente sobre un archivo en tu computadora:

1. Haz clic en **`🔗 Vincular`**
2. Elige un archivo `.json` existente o crea uno nuevo
3. A partir de ese momento, cada cambio se guarda **simultáneamente** en:
   - LocalStorage del navegador
   - El archivo vinculado en tu disco

> 📍 **Ejemplo de carpeta recomendada:** `C:\Users\TuNombre\Documentos\CartografiaPRO\datos.json` (Windows)  
> o `~/Documentos/CartografiaPRO/datos.json` (Mac/Linux)

**¿Por qué vincular?** Porque así tienes doble respaldo: si borras el navegador, el archivo sigue en tus Documentos.

---

## 📥 Cómo usar la app

### Opción A: Usar el HTML directamente (sin internet)

1. Descarga el archivo `1212.html`
2. Guárdalo en tu computadora, por ejemplo en `Documentos / CartografiaPRO /`
3. Haz doble clic para abrirlo con tu navegador (Chrome, Edge, Firefox)
4. **Los datos se guardan solos** — no necesitas instalar nada

### Opción B: Publicar en GitHub Pages (acceso desde cualquier lado)

```bash
# 1. Crea un repositorio en GitHub llamado "cartografia-pro"
# 2. Sube el archivo renombrándolo como index.html
# 3. Ve a Settings > Pages > Branch: main
# 4. En minutos estará online en:
#    https://tuusuario.github.io/cartografia-pro/
