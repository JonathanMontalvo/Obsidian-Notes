2025-05-25 18:20

tags: [angular]

---
# Angular project structure
my-angular-app/
│
├── 📁 src/
│   ├── 📁 app/
│   │   ├── 📁 components/        → Componentes organizados por funcionalidad
│   │   │   ├── 📁 login/
│   │   │   │   ├── login.component.ts
│   │   │   │   ├── login.component.html
│   │   │   │   ├── login.component.scss
│   │   │   │   └── login.module.ts
│   │   │   ├── 📁 dashboard/
│   │   │   └── ...
│   │   │
│   │   ├── 📁 interfaces/        → Interfaces y modelos de datos
│   │   │   ├── user.interface.ts
│   │   │   ├── product.interface.ts
│   │   │   └── ...
│   │   │
│   │   ├── 📁 services/          → Servicios para llamadas HTTP o lógica compartida
│   │   │   ├── auth.service.ts
│   │   │   ├── user.service.ts
│   │   │   └── ...
│   │   │
│   │   ├── 📁 shared/            → Componentes, pipes, directivas reutilizables
│   │   │   ├── 📁 components/
│   │   │   │   ├── navbar/
│   │   │   │   └── modal/
│   │   │   ├── 📁 pipes/
│   │   │   ├── 📁 directives/
│   │   │   └── shared.module.ts
│   │   │
│   │   ├── app.component.ts
│   │   ├── app.module.ts
│   │   └── app-routing.module.ts
│   │
│   ├── 📁 assets/
│   ├── 📁 environments/
│   └── index.html
│
├── angular.json
├── package.json
└── tsconfig.json
