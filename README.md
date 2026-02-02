# FichAI API Documentation

Documentación de la API pública de FichAI usando [Mintlify](https://mintlify.com).

## Setup Local

1. Instalar Mintlify CLI:
```bash
npm i -g mintlify
```

2. Correr en modo desarrollo:
```bash
mintlify dev
```

La documentación estará disponible en `http://localhost:3000`.

## Estructura del Proyecto

```
fichai-docs/
├── mint.json           # Configuración de Mintlify
├── openapi.json        # OpenAPI spec
├── introduction.mdx    # Página principal
├── quickstart.mdx      # Guía de inicio rápido
├── authentication.mdx  # Autenticación
├── guides/
│   ├── desarrollos.mdx # Guía de desarrollos
│   ├── pagination.mdx  # Paginación
│   ├── errors.mdx      # Manejo de errores
│   └── rate-limits.mdx # Rate limits
├── api-reference/
│   ├── introduction.mdx
│   ├── desarrollos/
│   │   ├── list.mdx    # GET /desarrollos
│   │   └── get.mdx     # GET /desarrollos/{slug}
│   └── organizations/
│       └── desarrollos.mdx # GET /organizations/{slug}/desarrollos
├── logo/
│   ├── light.svg
│   └── dark.svg
└── images/
    ├── hero-light.svg
    └── hero-dark.svg
```

## Deploy a Producción

### Opción 1: Mintlify Cloud (Recomendado)

1. Ir a [mintlify.com](https://mintlify.com) y crear cuenta
2. Conectar el repositorio de GitHub
3. Configurar dominio personalizado: `docs.fichai.com` o `developers.fichai.com`

### Opción 2: Vercel

1. Crear proyecto en Vercel
2. Conectar repositorio
3. Build command: `mintlify build`
4. Output directory: `.mintlify`

## Actualizar OpenAPI Spec

Cuando cambien los endpoints, actualizar el spec:

```bash
# Desde fichai-web, regenerar el spec
cd ../fichai-web
npx next-openapi-gen generate

# Copiar a docs
cp public/openapi-public.json ../fichai-docs/openapi.json
```

## Dominio Personalizado

Para configurar `docs.fichai.com`:

1. En Mintlify dashboard, ir a Settings > Custom Domain
2. Agregar `docs.fichai.com`
3. En tu DNS, agregar CNAME:
   ```
   docs.fichai.com -> cname.mintlify.dev
   ```

## Links Útiles

- [Mintlify Documentation](https://mintlify.com/docs)
- [MDX Components](https://mintlify.com/docs/content/components)
- [Customization](https://mintlify.com/docs/settings/global)
