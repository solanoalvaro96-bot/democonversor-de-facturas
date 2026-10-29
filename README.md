🧾 Facturas (PDF / Fotos) a Excel con Formato ARCA
Script automatizado diseñado para procesar facturas digitales (PDFs) y comprobantes en imagen, extraer sus datos clave utilizando Inteligencia Artificial (Gemini o Claude) y estructurarlos en un archivo de Excel con el formato oficial de "Comprobantes de Compras" de ARCA (ex AFIP), evitando duplicados.
El script está optimizado para ejecutarse fácilmente en Google Colab, aprovechando herramientas de lectura de texto inteligente como MarkItDown.
---
✨ Características Principales
Lectura Inteligente Dual: Utiliza MarkItDown para extraer texto de PDFs nativos y capacidades de visión por IA para PDFs escaneados o imágenes (`.jpg`, `.png`, `.webp`)[cite: 1].
Soporte Multi-IA: Permite elegir entre Google Gemini (por defecto con modelos como `gemini-3.1-flash-lite`) o Anthropic Claude como motores de extracción[cite: 1].
Validación contra Duplicados:
Detecta archivos idénticos mediante huellas digitales (`SHA-256`)[cite: 1].
Evita duplicados de comprobantes ya procesados usando las claves fiscales (CUIT, Tipo, Punto de Venta y Número)[cite: 1].
Formato Oficial ARCA: Genera un archivo `.xlsx` listo con las columnas oficiales de Comprobantes de Compras, ordenadas cronológicamente y con formato numérico correcto[cite: 1].
Hojas de Auditoría Integradas: El Excel generado incluye solapas adicionales de control (`Control`, `Duplicadas` y `Errores`) para revisar observaciones y discrepancias de manera sencilla[cite: 1].
---
🚀 Cómo usarlo (Paso a Paso en Google Colab)
Subí el notebook a tu entorno de Google Colab o creá uno nuevo pegando el código.
Subí tus facturas de prueba a una carpeta en tu Google Drive (por ejemplo: `Mi unidad/facturas_demo`)[cite: 1].
Configura tus credenciales de API de forma segura:
En el panel lateral izquierdo de Colab, hacé clic en el ícono de llave (🔑) (Secretos).
Agregá tu clave con el nombre `GEMINI_API_KEY` (o `ANTHROPIC_API_KEY` según el proveedor que elijas) asegurándote de activar la opción Acceso desde el notebook[cite: 1].
Modificá los parámetros en la celda de configuración del script (proveedor, modelo, rutas de carpetas)[cite: 1].
Ejecutá las celdas en orden[cite: 1].
---
📋 Requisitos y Dependencias
El script instala automáticamente sus dependencias al ejecutarse, pero utiliza principalmente:
`markitdown[pdf]`[cite: 1]
`google-genai` (o `anthropic`)[cite: 1]
`pandas`[cite: 1]
`openpyxl`[cite: 1]
`Pillow`[cite: 1]
---
🛠️ Configuración (`# 2) CONFIGURACIÓN`)
En el bloque de configuración del script podés ajustar los siguientes parámetros según tus necesidades:
```python
PROVEEDOR = "gemini"                      # "gemini" o "claude"
MODELO = "gemini-3.1-flash-lite"          # Modelo de IA a utilizar
CARPETA = "/content/drive/MyDrive/facturas_demo"  # Carpeta de origen en Google Drive
SALIDA = "/content/drive/MyDrive/comprobantes_compras.xlsx" # Archivo Excel de salida
CUIT_PROPIO = None                        # Tu CUIT (si es None, se autodetecta)
MAX_ARCHIVOS = 10                         # Límite de archivos para pruebas (None para procesar todos)
PAUSA_SEG = 1                             # Pausa entre llamadas para cuidar cuotas de la API# democonversor-de-facturas
es un conversor con ia de facturas en pdf e imagen
