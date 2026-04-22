# LinkedIn Analyzer — R'Evolution Group

Herramienta de inteligencia competitiva para analizar posts de LinkedIn de hasta 5 marcas simultáneamente.

## Stack

- Frontend: HTML/CSS/JS vanilla (sin frameworks)
- Backend: Vercel Serverless Functions (Node.js)
- APIs: Anthropic Claude (análisis IA) + Outscraper (scraping LinkedIn)

## Estructura

```
linkedin-analyzer/
├── index.html          # App completa
├── api/
│   └── analyze.js      # Proxy seguro hacia Anthropic API
├── vercel.json         # Configuración Vercel
└── README.md
```

## Deploy en Vercel

### 1. Subir a GitHub

```bash
git init
git add .
git commit -m "Initial commit — LinkedIn Analyzer"
git remote add origin https://github.com/TU_USUARIO/linkedin-analyzer.git
git push -u origin main
```

### 2. Conectar con Vercel

1. Ir a [vercel.com](https://vercel.com) → New Project
2. Importar el repositorio de GitHub
3. Click en **Deploy** (sin cambiar nada)

### 3. Configurar la API key de Anthropic

En Vercel → Settings → Environment Variables:

| Variable | Valor |
|----------|-------|
| `ANTHROPIC_API_KEY` | `sk-ant-...` |

4. Hacer **Redeploy** para que tome la variable.

## Variables de entorno

| Variable | Descripción | Requerida |
|----------|-------------|-----------|
| `ANTHROPIC_API_KEY` | API key de Anthropic para análisis con Claude | Sí |

> La API key de Outscraper se ingresa directamente en la interfaz (modo API en tiempo real). No se almacena en el servidor.

## Uso

### Modo xlsx
1. Exportar posts desde [Outscraper](https://app.outscraper.cloud/linkedin-posts)
2. Subir hasta 5 archivos xlsx (1 por marca o varias en el mismo)
3. Hacer click en "Analizar archivos"

### Modo API en tiempo real
1. Ingresar API key de Outscraper
2. Agregar URLs de LinkedIn de cada marca (hasta 5)
3. Hacer click en "Traer posts desde Outscraper"

### Análisis con IA
- Con datos cargados, ir a la sección "Insights con Claude"
- Seleccionar tipo de análisis (general, temas, engagement, benchmark, oportunidades)
- La API key de Anthropic la toma automáticamente del servidor (no hace falta ingresarla)

## Desarrollo local

Podés abrir `index.html` directamente en el browser para desarrollo.
Para que el análisis con Claude funcione en local, necesitás la [Vercel CLI](https://vercel.com/docs/cli):

```bash
npm i -g vercel
vercel dev
```

Esto levanta el servidor local con las serverless functions en `http://localhost:3000`.
