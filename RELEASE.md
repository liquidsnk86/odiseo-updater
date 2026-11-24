# Publicar Odiseo 1.2.0

Los artifacts ya están generados y verificados en `v1.2.0/`. Falta solo
publicarlos en GitHub.

## 1) Crear el release

1. Ir a `https://github.com/liquidsnk86/odiseo/releases` → **Draft a new release**.
2. Tag: `v1.2.0`. Título sugerido: `Odiseo 1.2.0`.
3. Descripción (el cuerpo debe identificar la app y la versión):

   ```
   Odiseo 1.2.0

   <pegar las notas de la sección [1.2.0] de CHANGELOG.md>
   ```

   Ese mismo texto está en el campo `notes` de `v1.2.0/latest.json`.
4. Subir como assets los tres archivos de `v1.2.0/`:
   - `Odiseo_1.2.0_x64-setup.exe`
   - `Odiseo_1.2.0_x64-setup.exe.sig`
   - `latest.json`
5. Marcar **Set as the latest release** y publicar. No debe quedar como
   *draft* ni como *pre-release*.

## 2) Verificar

```bash
curl -L https://github.com/liquidsnk86/odiseo/releases/latest/download/latest.json
```

Debe devolver `"version": "1.2.0"` y esta URL:

```
https://github.com/liquidsnk86/odiseo/releases/download/v1.2.0/Odiseo_1.2.0_x64-setup.exe
```

Después, en Odiseo: **Configuración → Acerca de → Buscar actualizaciones**.
Debe ofrecer la versión 1.2.0.

## Si no aparece la actualización

- El release tiene que estar publicado y marcado como *latest*.
- El asset del manifiesto debe llamarse exactamente `latest.json`.
- La URL dentro del JSON debe coincidir con el nombre real del `.exe`.
- GitHub Releases puede tardar unos minutos en refrescar la CDN.

## Si dice "firma inválida"

La firma y el instalador no corresponden. Regenerarlos desde el repo de
`solid_snk_agent`:

```bash
TAURI_SIGNING_PRIVATE_KEY="$(cat .tauri-keys/odiseo.key)" \
  npm run tauri build -- --bundles nsis

ODISEO_GITHUB_REPO=liquidsnk86/odiseo \
  npm run release:update 1.2.0 \
  src-tauri/target/release/bundle/nsis/Odiseo_1.2.0_x64-setup.exe
```

Y volver a copiar los tres archivos a `v1.2.0/`.

## Próximas versiones

1. Subir la versión en `package.json`, `src-tauri/tauri.conf.json`,
   `src-tauri/Cargo.toml` y `src/version.ts`; agregar sección en `CHANGELOG.md`;
   hacer commit.
2. Repetir los dos comandos anteriores con la versión nueva.
3. Copiar el instalador, el `.sig` y el `latest.json` a una carpeta `vX.Y.Z/`
   y actualizar este archivo y el `README.md`.
