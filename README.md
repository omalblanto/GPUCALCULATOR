# GPU Memory Calculator

Aplicación web para estimar memoria de modelos LLM, KV Cache y cantidad de GPUs requerida por capacidad de VRAM. Esta primera versión está preparada como proyecto estático para GitHub y GitHub Pages.

## Alcance de la versión 1.0

- Página responsive en React + TypeScript.
- Diseño oscuro tipo landing page para infraestructura de IA.
- Cálculo de memoria del modelo.
- Cálculo de KV Cache usando parámetros de arquitectura documentados.
- Comparación de NVIDIA HGX H200, RTX PRO 6000 Blackwell, L40S y L4.
- Separación entre GPU mínimas por memoria y configuración física del board HGX H200.
- Sin backend, base de datos ni telemetría.

## Estructura

```text
public/
  favicon.svg
  robots.txt
src/
  assets/
    datacenter-gpu.jpg
  components/
    BrandMarks.tsx
    Field.tsx
    GpuTable.tsx
    MetricCard.tsx
  hooks/
    use-mobile.tsx
  lib/
    gpuSizing.ts
  routes/
    HomePage.tsx
  main.tsx
  router.tsx
  styles.css
.github/workflows/
  deploy-pages.yml
```

## Desarrollo local

```bash
npm install
npm run dev
```

## Compilación

```bash
npm run build
npm run preview
```

El contenido compilado queda en `dist/`.

## GitHub Pages

1. Subir el repositorio a GitHub.
2. Abrir **Settings → Pages**.
3. Seleccionar **GitHub Actions** como Source.
4. El workflow incluido construye y publica `dist/`.

## Motor matemático

### Memoria del modelo

```text
Memoria GB = Parámetros (B) × bytes por valor × 1.20
```

### KV Cache por solicitud

```text
KV bytes = 2 × tokens de secuencia × layers × KV heads × head dimension × bytes KV
```

La secuencia usa `input promedio + output promedio`. El KV total multiplica el valor por solicitud por el número de solicitudes simultáneas.

### Cantidad de GPUs por VRAM

```text
GPU mínimas = ceil(VRAM total requerida / VRAM por GPU)
```

La configuración física de HGX H200 se expresa en incrementos de cuatro GPUs por board.

## Evolución

La lógica matemática reside en `src/lib/gpuSizing.ts` y está desacoplada de la interfaz. La siguiente versión puede incorporar despliegue específico para Google Cloud sin modificar el núcleo visual de la aplicación.
