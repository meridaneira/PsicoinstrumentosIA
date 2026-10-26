# PsicoInstrumenta AI

Prototipo web para organizar proyectos de construcción de instrumentos psicológicos: definición del constructo, dimensiones, banco de ítems, revisión preliminar y exportación de datos.

> **Estado:** prototipo demostrativo (v0.1). No es una plataforma clínica ni un sistema de validación psicométrica. La interfaz utiliza datos de demostración y no está conectada a un proveedor de IA ni a una base de datos.

## Ver la aplicación

### En tu computadora
1. Descarga o clona este repositorio.
2. Abre `index.html` en un navegador moderno (Chrome, Edge, Firefox o Safari).

No requiere instalar dependencias ni ejecutar un servidor.

### Publicar con GitHub Pages
1. Crea un repositorio en GitHub, por ejemplo `psicoinstrumenta-ai`.
2. Sube `index.html`, `README.md`, `LICENSE` y `.gitignore` a la raíz del repositorio.
3. En el repositorio, entra a **Settings → Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Elige la rama `main` y la carpeta `/ (root)`, y guarda.
6. Espera a que GitHub Pages publique el sitio. La URL aparecerá en la sección **Settings → Pages**.

## Funciones incluidas en el prototipo

- Panel de proyectos y proyectos de ejemplo.
- Creación de proyectos demostrativos.
- Organización básica del modelo conceptual y dimensiones.
- Banco de ítems con edición y estados de revisión.
- Lista de criterios para revisión preliminar.
- Exportación de banco de ítems a CSV y plantillas de texto.
- Diseño adaptable a pantallas pequeñas.

## Limitaciones conocidas

- Los cambios se mantienen en memoria mientras la página está abierta; no existe persistencia entre sesiones.
- Los datos precargados son ejemplos y no deben tratarse como resultados reales de investigación.
- La revisión de calidad es una lista de comprobación manual, no un análisis automático con IA.
- No se realiza validación de contenido, análisis factorial, estimación de fiabilidad, baremación ni diagnóstico.
- No introduzcas datos identificables, historias clínicas ni respuestas sensibles de participantes en esta demo.

## Próximos pasos sugeridos

1. Separar interfaz y lógica en componentes mantenibles.
2. Añadir autenticación y base de datos con controles de acceso.
3. Integrar un proveedor de IA desde el backend (las claves nunca deben ir en el frontend).
4. Incorporar trazabilidad entre constructos, dimensiones, indicadores, ítems y fuentes.
5. Añadir exportación DOCX/PDF y pruebas automatizadas.
6. Revisar privacidad, seguridad y obligaciones legales aplicables antes de usar datos reales.

## Estructura

```text
psicoinstrumenta-ai/
├── index.html
├── README.md
├── LICENSE
└── .gitignore
```

## Desarrollo local

El prototipo es estático. Basta con abrir `index.html`. Opcionalmente, puedes usar la extensión **Live Server** de Visual Studio Code para recarga automática durante cambios.

## Contribuciones

Antes de aceptar contribuciones, documenta los cambios y conserva explícitas las limitaciones científicas y psicométricas del producto.
