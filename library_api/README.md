# library_api

API REST + sitio web de la Biblioteca (Next.js 16, Firebase, TypeScript). Construido según la Guía 1.

## Puesta en marcha

Entra a la carpeta `library_api` que contiene este `package.json`, no ejecutes
los comandos desde la carpeta exterior que contiene la guía. Desde esa carpeta
exterior, en PowerShell:

```powershell
Set-Location .\library_api
pnpm.cmd install
```

Ejecuta los siguientes comandos ya dentro de esa carpeta. En PowerShell usa
`pnpm.cmd` para evitar el bloqueo de `pnpm.ps1` por la política de ejecución de
Windows.

Las credenciales ya configuradas en `.env` de la carpeta exterior deben estar
también en esta carpeta para que Next.js y los scripts las encuentren. Si
`library_api\.env` aún no existe, desde `library_api` copia la configuración
existente con `Copy-Item ..\.env .\.env`. Si no tienes un `.env` configurado,
crea uno con `Copy-Item .env.example .env` y completa las cuatro variables
siguiendo la sección 2.5 de la guía. No compartas ni subas ese archivo.

Confirma primero que el proyecto está configurado:

```powershell
pnpm.cmd typecheck
pnpm.cmd test
pnpm.cmd lint
pnpm.cmd build
```

En Firebase, activa Authentication con correo/contraseña, crea Firestore y
configura sus reglas como indica la guía. Después, `pnpm.cmd seed` carga los 10
libros de ejemplo en Firestore. Crea tus cuentas de prueba con contraseñas
propias:

```powershell
pnpm.cmd create-user -- estudiante@tucorreo.com "TuClave" "Tu Estudiante" student
pnpm.cmd create-user -- bibliotecario@tucorreo.com "TuClave" "Tu Bibliotecario" librarian
pnpm.cmd dev
```

Abre <http://localhost:3000>; la documentación de la API está en
<http://localhost:3000/api/docs>. Con el servidor en marcha, verifica la
conexión con `pnpm.cmd smoke`. Para restablecer los datos de demostración,
ejecuta `pnpm.cmd reset-demo`.

Nunca subas `.env` ni el `.json` de la cuenta de servicio a git.
