# Odiseo

Odiseo es una aplicación de escritorio para Windows que combina un asistente de
chat con un agente capaz de operar la computadora y trabajar con Iurix. El
orquestador y los datos viven en la propia máquina: el modelo propone acciones
y Odiseo decide si y cómo ejecutarlas.

## Qué hace

- **Asistente por chat**: pedís una tarea en lenguaje natural, Odiseo la arma en
  pasos, ejecuta herramientas reales y te cuenta el resultado.
- **Operación del equipo**: navega con Playwright, lee y escribe archivos dentro
  de su workspace, ejecuta PowerShell cuando se lo pedís y consulta el estado
  del sistema. Las acciones sensibles se muestran antes de ejecutarse.
- **Iurix**: busca expedientes por número, carátula o materia; descarga adjuntos
  y novedades; consulta catálogos y prepara el alta de causas. La firma final se
  completa en la web oficial de Iurix.
- **Causas y documentos**: carga asistida de causas, planilla, reportes y
  exportación a PDF.
- **Calendario y avisos**: vista mensual con navegación propia y notificaciones
  de Outlook mientras Iurix esté conectado.
- **Fallos y consultas**: selector de fallos 100 / 500 / 1000 y consultas de
  BCRA con caché local.
- **Licencias y actualizaciones**: prueba gratuita de 7 días, planes mensuales
  y actualizaciones firmadas que se verifican antes de instalarse.

## Aptitudes

- **Local**: historial, configuración y caché en SQLite, sin depender de la nube
  para trabajar.
- **Con sandbox**: el agente solo puede escribir dentro de su workspace.
- **Con permisos visibles**: siempre se ve qué puede hacer y qué requiere
  confirmación.
- **Sin conexión**: los datos ya sincronizados siguen disponibles si Iurix no
  responde.
- **Diagnosticable**: el panel de diagnóstico permite copiar los errores para
  soporte; no los envía por su cuenta.

## Versiones

Cada release incluye su carpeta con el instalador y el manifiesto de
actualización, por ejemplo `v1.2.0/`. También podés actualizar desde
**Configuración → Acerca de → Buscar actualizaciones** dentro de la app.
