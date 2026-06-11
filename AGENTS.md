# QSPQI Launcher — Guía para Agentes

Monorepo launcher del QSP Quantum Institute. Orquesta submodules independientes via git submodules y docker-compose.

## Submodules

| Submodule | Repo | Descripción |
|-----------|------|-------------|
| `qspqi-web-main` | Portal principal | Landing, secciones, embed de HIOXX via iframe |
| `qspqi-web-hioxx` | Calculadora HIOXX | Captura de datos + cálculos modulares |

## Relación entre submodules

- **No hay paquetes compartidos** — cada submodule es un proyecto Vite independiente
- **No hay cross-imports** entre submodules
- **Convenciones compartidas:** paleta de colores QSP, estructura de carpetas similar, stack tecnológico
- **Integración:** main embeds hioxx en `/hioxx` via iframe (`VITE_HIOXX_URL`)

## Dónde buscar contexto

| Necesidad | Ubicación |
|-----------|-----------|
| Lógica de negocio HIOXX | `qspqi-web-hioxx/docs/specs/` |
| Arquitectura HIOXX | `qspqi-web-hioxx/docs/specs/TECHNICAL-ARCHITECTURE.md` |
| Guía agente HIOXX | `qspqi-web-hioxx/AGENTS.md` |
| Layout/branding main | `qspqi-web-main/src/components/layout/` |
| Docker dev | `docker-compose.yml` + `.env.template` |

## Desarrollo local

```bash
# Desde la raíz del monorepo
docker-compose up
```

## Reglas

- No crear imports cruzados entre submodules
- Mantener paleta de colores sincronizada manualmente
- Specs de negocio viven en el submodule correspondiente
- Contexto general del monorepo vive aquí

Ver también: [`docs/MONOREPO.md`](docs/MONOREPO.md)
