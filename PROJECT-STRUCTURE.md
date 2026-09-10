# Estructura del proyecto

```text
.
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
├── public/
│   ├── favicon.svg
│   └── robots.txt
├── src/
│   ├── assets/
│   │   └── datacenter-gpu.jpg
│   ├── components/
│   │   ├── BrandMarks.tsx
│   │   ├── Field.tsx
│   │   ├── GpuTable.tsx
│   │   └── MetricCard.tsx
│   ├── hooks/
│   │   └── use-mobile.tsx
│   ├── lib/
│   │   └── gpuSizing.ts
│   ├── routes/
│   │   └── HomePage.tsx
│   ├── main.tsx
│   ├── router.tsx
│   └── styles.css
├── .gitignore
├── index.html
├── package.json
├── README.md
├── tsconfig.app.json
├── tsconfig.json
├── tsconfig.node.json
└── vite.config.ts
```

La primera versión es una SPA estática. El motor matemático está aislado en `src/lib/gpuSizing.ts` y la landing principal en `src/routes/HomePage.tsx`.
