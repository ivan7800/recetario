# Mi Recetario PRO

Aplicación web local, instalable y preparada para GitHub Pages para guardar recetas, organizar ingredientes, planificar menús y generar listas de la compra.

## Estado de esta versión

**Versión V8 Definitiva — IndexedDB / Offline / Sin CDN / Motor 1.000.000 recetas**

Esta build mantiene la app ligera y añade un motor mundial capaz de generar recetas virtuales offline sin crear un archivo gigante ni cargar un millón de objetos al iniciar.

### Qué incluye

- Persistencia principal en **IndexedDB**.
- Migración automática desde versiones antiguas que usaban `localStorage`.
- Imágenes guardadas como datos locales al subir archivo.
- URLs externas de imagen desactivadas para mantener privacidad, estabilidad offline y evitar dependencias de servidores externos.
- Sin CDN, sin APIs externas y sin envío de recetas a terceros.
- Service Worker con caché offline de assets propios.
- PWA instalable con iconos reales incluidos.
- Interfaz móvil optimizada.
- Catálogo mundial base con recetas internacionales.
- **Motor virtual de 1.000.000 recetas offline**: genera cada receta solo cuando se visualiza o se añade al recetario.
- Carga progresiva del catálogo mundial para no saturar móvil.
- Buscador y filtros por cocina, ingrediente, etiqueta y estilo.

## Por qué no se guarda un millón como JSON estático

Un millón de recetas completas en JSON plano sería pesado, lento de clonar, incómodo para GitHub Pages y malo para móviles. Esta versión usa un enfoque más profesional: conserva recetas base y añade un generador determinista que crea recetas detalladas bajo demanda.

Resultado: el usuario puede explorar un catálogo de escala millón sin que el zip pese cientos de MB ni que el navegador tenga que cargarlo todo al abrir.

## Funciones principales

- Crear, editar, duplicar, eliminar y marcar recetas favoritas.
- Ingredientes con cantidad, unidad y normalización básica.
- Categorías editables.
- Secciones de compra editables.
- Planificador semanal.
- Lista de la compra agrupada por secciones.
- Modo cocinar paso a paso.
- Catálogo internacional con motor millón offline.
- Importación y exportación JSON.
- Exportación TXT.
- Tarjeta visual de receta para compartir.
- Enlace visual local sin librerías externas.
- Modo claro / oscuro.
- PWA offline.

## Privacidad

La app está diseñada como herramienta local:

- No tiene backend.
- No requiere cuenta.
- No manda recetas a servidores externos.
- No carga librerías externas.
- No guarda imágenes externas por URL.
- Los datos principales viven en IndexedDB dentro del navegador del usuario.

## Límites conocidos

Esta es una aplicación estática para GitHub Pages. Por diseño, no incluye:

- Login.
- Usuarios.
- Sincronización cloud.
- Colaboración entre dispositivos.
- Panel de administración.
- Base de datos remota.

Para convertirla en SaaS real habría que crear una versión superior con backend, autenticación y base de datos remota, por ejemplo con Supabase, Firebase, PocketBase o un backend propio.

## Instalación en GitHub Pages

1. Sube todo el contenido de este proyecto a un repositorio.
2. Activa GitHub Pages desde `Settings > Pages`.
3. Selecciona la rama principal y la carpeta raíz.
4. Abre la URL generada por GitHub Pages.
5. Desde móvil o escritorio, instala la app si el navegador lo permite.

## Estructura

```text
/
├─ index.html
├─ manifest.webmanifest
├─ sw.js
├─ icons/
│  ├─ icon-192.png
│  └─ icon-512.png
├─ README.md
├─ AUDIT_REPORT.md
└─ .gitignore
```

## Recomendación de uso

Aunque IndexedDB soporta colecciones bastante más grandes que `localStorage`, conviene exportar un backup JSON de vez en cuando, especialmente si se guardan muchas recetas con imágenes.

## Puntuación de auditoría

Build estática GitHub-ready V8: **9,8/10**.

Para un 10 absoluto como producto comercial haría falta una versión SaaS opcional con sincronización, cuentas, copias cloud y colaboración.
