# Monorepo QSPQI Launcher

## Estructura

```
qspqi-launcher/
├── qspqi-web-main/     # Submodule — portal principal
├── qspqi-web-hioxx/    # Submodule — calculadora HIOXX
├── docker-compose.yml  # Dev orchestration
├── .env.template       # Environment variables template
├── .gitmodules         # Submodule configuration
└── AGENTS.md           # Agent entry point
```

## Git Submodules

Cada submodule es un repositorio independiente en GitHub (QSP-Quantum-Institute org):

- `qspqi-web-main` → branch `dev`
- `qspqi-web-hioxx` → branch `dev`

### Comandos útiles

```bash
git submodule update --init --recursive  # Clonar submodules
git submodule update --remote             # Actualizar a latest
```

## Docker Compose

Servicios de desarrollo:

| Servicio | Puerto | Descripción |
|----------|--------|-------------|
| qspqi-web-main | 5173 | Portal principal |
| qspqi-web-hioxx | 5174 | Calculadora HIOXX |

Variables en `.env.template`:
- `QSPQI_WEB_MAIN_VITE_HIOXX_URL` — URL del iframe HIOXX en main

## Convenciones

1. **Independencia:** Cada submodule tiene su propio `package.json`, `node_modules`, configs
2. **Sin shared packages:** Duplicación intencional de utilidades comunes (`cn`, colors)
3. **Branding compartido:** Paleta QSP (gold, lightBlue, green, red, dark) en ambos
4. **Specs por submodule:** Documentación de negocio vive en el submodule correspondiente
5. **Agent context dual:** AGENTS.md en root (general) + AGENTS.md en cada submodule (específico)

## Integración main ↔ hioxx

```
qspqi-web-main (/hioxx route)
  └── iframe → VITE_HIOXX_URL (qspqi-web-hioxx)
```

HIOXX corre como SPA independiente. Las rutas internas de hioxx (`/`, `/resumen`, `/calculo`, `/calculo/:type`) funcionan dentro del iframe.
