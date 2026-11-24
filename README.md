# odiseo-updater

Staging local de los artifacts que se publican en **GitHub Releases** para el
updater firmado de Odiseo (Tauri v2). Acá no hay código: solo los archivos que
se suben al release y las instrucciones de publicación.

## Versión actual: 1.2.0

```
v1.2.0/
├── Odiseo_1.2.0_x64-setup.exe      # instalador NSIS (7,7 MB)
├── Odiseo_1.2.0_x64-setup.exe.sig  # firma minisign del instalador
└── latest.json                     # manifiesto que consume el updater
```

## Endpoint configurado en la app

`plugins.updater.endpoints` de `src-tauri/tauri.conf.json`:

```
https://github.com/liquidsnk86/odiseo/releases/latest/download/latest.json
```

La app compara esa versión con la propia y, antes de instalar, verifica la
firma con la clave pública embebida en `plugins.updater.pubkey`.

## Reglas

- `latest.json` y `.sig` deben corresponder **exactamente** al `.exe` que se
  sube. Si se recompila el instalador, hay que volver a firmar y regenerar el
  JSON.
- No renombrar los archivos: la URL del manifiesto apunta a
  `Odiseo_1.2.0_x64-setup.exe`.
- La clave privada `.tauri-keys/odiseo.key` queda solo en la máquina de
  desarrollo. **Nunca** se sube al repo ni al release.
- Para publicar, seguí [`RELEASE.md`](RELEASE.md).
