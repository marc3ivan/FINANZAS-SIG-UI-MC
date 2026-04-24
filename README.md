FINANZAS-SIG-UI-MC — Gestión financiera profesional para maperos SIG. Control de clientes, proyectos, pendientes, pagos a maperos, estadísticas y backup local. Diseñado para Paraguay.

# 💰 FINANZAS-SIG-UI-MC

![Versión](https://img.shields.io/badge/versión-6.0-blue)
![Plataforma](https://img.shields.io/badge/platform-web%20%7C%20local-darkgreen)
![País](https://img.shields.io/badge/Paraguay-🇵🇾-red)

Sistema financiero profesional para **cartógrafos SIG, topógrafos y maperos independientes**. Controla clientes, proyectos, pendientes de cobro, pagos a maperos y estadísticas en tiempo real. Todo funciona **100% offline** en tu navegador — tus datos viven en tu disco.

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
   - `Documentos / FINANZAS-SIG / backups /`
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

> 📍 **Ubicación recomendada para el archivo vinculado:**

| Sistema | Ruta sugerida |
|---------|---------------|
| **Windows** | `C:\Users\TuUsuario\Documents\FINANZAS-SIG\datos.json` |
| **Mac** | `~/Documentos/FINANZAS-SIG/datos.json` |
| **Linux** | `~/Documentos/FINANZAS-SIG/datos.json` |

**¿Por qué vincular?** Porque así tienes doble respaldo: si borras el navegador, el archivo sigue en tus Documentos.

---

## 📥 Cómo usar la app

### Opción A: Usar el HTML directamente (sin internet)

1. Descarga el archivo `FSIG-UIMC.html`
2. Guárdalo en tu computadora, por ejemplo en `Documentos / FINANZAS-SIG /`
3. Haz doble clic para abrirlo con tu navegador (Chrome, Edge, Firefox)
4. **Los datos se guardan solos** — no necesitas instalar nada

### Opción B: Publicar en GitHub Pages (acceso desde cualquier lado)

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Esquema de Maperos</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
        }
        .arrow-down {
            width: 0; 
            height: 0; 
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            border-top: 10px solid #9ca3af;
            margin: 10px auto;
        }
    </style>
</head>
<body class="flex flex-col items-center py-10 px-4 min-h-screen">

    <!-- Controles -->
    <div class="mb-8 text-center">
        <h1 class="text-2xl font-bold text-gray-800 mb-2">Herramienta de Exportación</h1>
        <p class="text-gray-600 mb-4">Haz clic en el botón de abajo para generar y descargar la imagen.</p>
        <button onclick="descargarJPG()" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-6 rounded-lg shadow-lg transition transform hover:scale-105 flex items-center gap-2 mx-auto">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
            </svg>
            Descargar como JPG
        </button>
    </div>

    <!-- Área a exportar (El Esquema) -->
    <div id="esquema-exportar" class="bg-white p-10 rounded-2xl shadow-xl w-full max-w-3xl relative border border-gray-100">
        
        <!-- Título del Esquema -->
        <div class="text-center mb-10">
            <h2 class="text-3xl font-extrabold text-gray-900">🗺️ Sistema de Gestión de Maperos</h2>
            <p class="text-gray-500 mt-2">Flujo de Trabajo y Ciclo de Vida del Proyecto</p>
        </div>

        <!-- Flujo -->
        <div class="flex flex-col items-center w-full">

            <!-- Paso 1 -->
            <div class="bg-indigo-50 border-2 border-indigo-200 text-indigo-800 w-full md:w-2/3 p-4 rounded-xl text-center shadow-sm">
                <span class="block text-sm font-bold text-indigo-500 mb-1">PASO 1</span>
                <span class="font-bold text-lg">🏢 Agregar Consultora</span>
                <p class="text-sm mt-1">Botón <span class="bg-indigo-200 px-2 py-0.5 rounded font-mono">+ Consultora</span></p>
            </div>

            <div class="arrow-down"></div>

            <!-- Paso 2 -->
            <div class="bg-blue-50 border-2 border-blue-200 text-blue-800 w-full md:w-2/3 p-4 rounded-xl text-center shadow-sm">
                <span class="block text-sm font-bold text-blue-500 mb-1">PASO 2</span>
                <span class="font-bold text-lg">📁 Agregar Proyecto</span>
                <p class="text-sm mt-1">Dentro del cliente, botón <span class="bg-blue-200 px-2 py-0.5 rounded font-mono">+ Trabajo</span></p>
            </div>

            <div class="arrow-down"></div>

            <!-- Paso 3 -->
            <div class="bg-yellow-50 border-2 border-yellow-200 text-yellow-800 w-full md:w-2/3 p-4 rounded-xl text-center shadow-sm">
                <span class="block text-sm font-bold text-yellow-600 mb-1">PASO 3</span>
                <span class="font-bold text-lg">✍️ Asignación</span>
                <p class="text-sm mt-1">Definir <strong>Mapero</strong> y <strong>Cantidad de Láminas</strong></p>
            </div>

            <div class="arrow-down"></div>

            <!-- Bifurcación Pagos -->
            <div class="flex flex-col md:flex-row w-full gap-4 md:w-5/6 justify-center">
                
                <!-- Cobro al Cliente -->
                <div class="bg-green-50 border-2 border-green-200 text-green-800 w-full p-4 rounded-xl text-center shadow-sm">
                    <span class="block text-sm font-bold text-green-600 mb-1">PASO 4: INGRESO</span>
                    <span class="font-bold text-lg">💸 El Cliente Paga</span>
                    <p class="text-sm mt-1">Presionar botón <span class="bg-green-200 px-2 py-0.5 rounded font-mono">💰 Cobrar</span></p>
                </div>

                <!-- Pago al Mapero -->
                <div class="bg-emerald-50 border-2 border-emerald-200 text-emerald-800 w-full p-4 rounded-xl text-center shadow-sm mt-4 md:mt-0">
                    <span class="block text-sm font-bold text-emerald-600 mb-1">PASO 5: EGRESO</span>
                    <span class="font-bold text-lg">👤 Pagar al Mapero</span>
                    <p class="text-sm mt-1">El ícono se pone <span class="text-green-600 font-bold">Verde 🟢</span></p>
                </div>
            </div>

            <div class="flex w-full md:w-5/6 justify-center gap-4 mt-2">
                <div class="arrow-down"></div>
            </div>

            <!-- Monitoreo -->
            <div class="flex flex-col md:flex-row w-full gap-4 md:w-5/6 justify-center mt-2">
                
                <!-- Pendientes -->
                <div class="bg-red-50 border-2 border-red-200 text-red-800 w-full p-4 rounded-xl text-center shadow-sm">
                    <span class="block text-sm font-bold text-red-600 mb-1">PASO 6: REVISIÓN</span>
                    <span class="font-bold text-lg">⏳ Ver Pendientes</span>
                    <p class="text-sm mt-1">Pestaña para tareas sin cobrar/pagar</p>
                </div>

                <!-- Estadísticas -->
                <div class="bg-purple-50 border-2 border-purple-200 text-purple-800 w-full p-4 rounded-xl text-center shadow-sm mt-4 md:mt-0">
                    <span class="block text-sm font-bold text-purple-600 mb-1">PASO 7: CONTROL</span>
                    <span class="font-bold text-lg">📊 Ver Estadísticas</span>
                    <p class="text-sm mt-1">Análisis de rendimiento y ganancias</p>
                </div>
            </div>

        </div>
    </div>

    <!-- Script para exportar a JPG -->
    <script>
        function descargarJPG() {
            const elemento = document.getElementById('esquema-exportar');
            
            // Cambiamos temporalmente el estilo para asegurar una captura perfecta
            elemento.style.borderRadius = "0";
            
            html2canvas(elemento, {
                scale: 2, // Alta resolución
                useCORS: true,
                backgroundColor: "#ffffff"
            }).then(canvas => {
                // Restauramos el estilo
                elemento.style.borderRadius = "1rem";
                
                // Creamos la imagen JPG
                const imgData = canvas.toDataURL('image/jpeg', 0.95);
                
                // Forzamos la descarga
                const enlace = document.createElement('a');
                enlace.download = 'Esquema-Maperos.jpg';
                enlace.href = imgData;
                enlace.click();
            }).catch(err => {
                console.error("Error al generar la imagen: ", err);
                alert("Hubo un error al generar la imagen.");
            });
        }
    </script>
</body>
</html>




```bash
# 1. Crea un repositorio en GitHub llamado "FINANZAS-SIG-UI-MC"
# 2. Sube el archivo renombrándolo como index.html
# 3. Ve a Settings > Pages > Branch: main
# 4. En minutos estará online en:
#    https://tuusuario.github.io/FINANZAS-SIG-UI-MC/

finanzas-sig, mapero, paraguay, gestion-financiera, cartografia, sig, gis, proyectos, cobros, backup-local, uphold, donaciones-crypto

