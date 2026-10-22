# Deploy Vercel + dominio Hostinger

## 1. Subir proyecto a Vercel

1. Crear cuenta en vercel.com (login con GitHub).
2. Subir esta carpeta a un repo de GitHub.
3. En Vercel: New Project → importar repo.
4. Framework: "Other" (es HTML estatico).
5. Deploy. Listo, da url tipo `proyecto.vercel.app`.

## 2. Conectar dominio de Hostinger

1. En Vercel: Project → Settings → Domains.
2. Agregar tu dominio (ej `naturizable.com`).
3. Vercel muestra registros DNS a usar. Dos opciones:

### Opcion A — Solo subdominio o raiz simple (recomendado)
Agregar en Vercel el dominio. Te da:
- Tipo `A` → host `@` → valor `76.76.21.21`
- Tipo `CNAME` → host `www` → valor `cname.vercel-dns.com`

### Opcion B — Nameservers completos
Cambiar nameservers en Hostinger a los de Vercel (menos recomendado si usas Hostinger para mas cosas, ej correo).

## 3. Editar DNS en Hostinger

1. Entrar a hPanel (panel Hostinger).
2. Dominios → tu dominio → DNS / Zona DNS.
3. Borrar registros `A` y `CNAME` viejos que apunten a Hostinger hosting.
4. Agregar los registros que dio Vercel (paso 2).
5. Guardar.

## 4. Esperar propagacion

- Toma entre 10 min y 24h.
- Verificar en Vercel: Settings → Domains → debe decir "Valid Configuration".

## 5. Actualizaciones futuras

- Cambios en el codigo → push a GitHub → Vercel redeploya solo.
- No se toca Hostinger de nuevo salvo cambio de dominio.

## Nota

- Si usas correo `@tudominio.com` en Hostinger, NO borres los registros `MX`. Solo tocar `A` y `CNAME` de la web.
