# 🗺️ Mapa de Parcelas — Guía de publicación en GitHub Pages

## Archivos del proyecto

```
mapa-parcelas/
├── index.html        ← mapa web interactivo
└── parcelas.geojson  ← tus datos (reemplazar con datos reales)
```

---

## PASO 1 — Reemplazar parcelas.geojson con tus datos reales

### Opción A: Exportar desde QGIS directamente a GeoJSON
1. Clic derecho en tu capa de parcelas → `Exportar → Guardar objetos como`
2. Formato: **GeoJSON**
3. CRS: **EPSG:4326** (WGS 84) — obligatorio para web
4. Nombre: `parcelas.geojson`
5. Reemplaza el archivo de ejemplo con el tuyo

### Opción B: Convertir SHP a GeoJSON online
- Sube tu .shp en: https://mapshaper.org
- Exporta como GeoJSON

---

## PASO 2 — Ajustar nombres de campos en index.html

Abre `index.html` y busca esta sección (línea ~130):

```javascript
const CAMPO_CLASE   = "CLASE_PEND";   // campo con clase de pendiente
const CAMPO_ID      = "ID";           // campo identificador
const CAMPO_OWNER   = "PROPIETARIO";  // campo propietario
const CAMPO_AREA    = "AREA_M2";      // campo área en m²
const CAMPO_USO     = "USO_SUELO";    // campo uso de suelo
const CAMPO_PEND    = "PENDIENTE";    // campo descripción pendiente
const CAMPO_MUN     = "MUNICIPIO";    // campo municipio (opcional)
```

Reemplaza cada valor con el nombre exacto de tus campos
(tal como aparecen en la tabla de atributos de QGIS).

---

## PASO 3 — Crear repositorio en GitHub

1. Ve a https://github.com y entra a tu cuenta
2. Clic en **"New repository"** (botón verde)
3. Configura:
   - Repository name: `mapa-parcelas` (o el nombre que quieras)
   - Visibility: **Public** (obligatorio para GitHub Pages gratis)
   - NO marques "Add README"
4. Clic en **"Create repository"**

---

## PASO 4 — Subir los archivos

### Opción A: Desde el navegador (más fácil)
1. En tu repositorio vacío, clic en **"uploading an existing file"**
2. Arrastra `index.html` y `parcelas.geojson`
3. Escribe un mensaje: `Primer commit — mapa de parcelas`
4. Clic en **"Commit changes"**

### Opción B: Con Git (si lo tienes instalado)
```bash
cd mapa-parcelas
git init
git add .
git commit -m "Mapa de parcelas inicial"
git remote add origin https://github.com/TU_USUARIO/mapa-parcelas.git
git push -u origin main
```

---

## PASO 5 — Activar GitHub Pages

1. En tu repositorio, ve a **Settings** (pestaña superior)
2. En el menú izquierdo, clic en **Pages**
3. En "Branch", selecciona **main** y carpeta **/ (root)**
4. Clic en **Save**
5. Espera 1-2 minutos
6. Tu mapa estará en:
   ```
   https://TU_USUARIO.github.io/mapa-parcelas/
   ```

---

## Funcionalidades del mapa

| Función | Descripción |
|---|---|
| 🎨 Colores por pendiente | Cada parcela tiene color según clase de pendiente |
| 🔍 Búsqueda | Filtra por ID, propietario, uso de suelo |
| 🏷️ Leyenda interactiva | Clic en cada clase para mostrar/ocultar |
| 📋 Panel lateral | Lista de todas las parcelas con atributos |
| 🖱️ Popup al clic | Muestra todos los atributos de la parcela |
| 🛰️ Cambiar mapa base | Alterna entre OpenStreetMap y satélite Esri |
| 📱 Responsive | Funciona en móvil y escritorio |

---

## Actualizar datos en el futuro

Solo reemplaza `parcelas.geojson` con una nueva versión
y súbelo nuevamente a GitHub. El mapa se actualiza solo.
