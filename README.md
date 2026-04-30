STE‑CLM — Aplicación móvil (Android) + Panel web (Vercel) --> CARLOS MARTÍNEZ

## Visión general
La app móvil de STE‑CLM es una aplicación Android orientada a la difusión de comunicados, utilidades y acceso a funcionalidades para afiliados/no afiliados, con un backend web desplegable en Vercel que centraliza contenidos (noticias/comunicados), métricas y servicios de autenticación. La solución está diseñada para crecer: el núcleo cubre el flujo de acceso seguro y el consumo de contenidos, y permite añadir módulos futuros sin rehacer la base.

## Qué incluye la aplicación móvil (Android)

### 1) Acceso y seguridad
- Acceso por DNI + correo con código : flujo de verificación que solicita un código enviado por email y valida al usuario antes de permitir el uso completo.
- DNI enmascarado en pantalla : por privacidad, el DNI se muestra parcialmente oculto (prefijo visible y resto enmascarado), evitando exposición accidental.
- Validación adicional de correo + contraseña (login) : se añade una capa extra para evitar accesos “con cualquier cosa” y reducir riesgos de suplantación.
- Gestión de sesión : la app guarda el estado de sesión localmente y protege la navegación para impedir entrar a pantallas principales sin una sesión válida.

### 2) Comunicados / noticias
- Listado de comunicados consumidos desde backend.
- Notificaciones de nuevos comunicados : la app puede avisar cuando hay un comunicado nuevo.
- Comportamiento cuidado en primera instalación : al instalar por primera vez, no muestra el “último comunicado anterior” como si fuera nuevo; solo avisa cuando aparece uno posterior.

### 3) Intereses del usuario (segmentación)
- Selección de intereses/sectores para personalizar qué avisos o contenidos son relevantes.
- Base preparada para segmentar notificaciones por grupos (p. ej. Primaria, Secundaria, Interinos…).

### 4) Chat y mensajería (base funcional)
- Chat estilo mensajería con estructura de hilos y envío de mensajes.
- Preparado para evolucionar a sincronización y persistencia más robusta según necesidades.
  
### 5) Menú y utilidades
- Accesos a recursos y herramientas útiles (por ejemplo, enlaces a secciones informativas y utilidades).
- Interfaz coherente con identidad visual (icono de la app integrado en pantallas clave y menú).
  
### 6) Estabilidad y robustez
- Manejo defensivo para evitar cierres por errores comunes (null checks, control de errores en tareas periódicas, protección de navegación).
- Ajustes de build para generar APK/AAB de forma estable.
  
## Qué incluye el panel web (Vercel)

### 1) Panel de administración (ruta principal)
- Panel para gestionar contenido (comunicados/noticias) y funcionalidades administrativas.
- Autenticación de administrador basada en variables de entorno y sesión segura (cookie HttpOnly).
  
### 2) Dashboard de usuario (ruta dedicada)
- Acceso separado para “usuario normal” del dashboard, con credenciales configuradas en entorno y sesión propia.
- Ideal para mostrar métricas, vistas de control o herramientas internas sin dar acceso a toda la administración.
  
### 3) Servicios API para la app móvil
- Endpoints para:
  - Solicitud y verificación de código (DNI+correo).
  - Login con correo+contraseña (cuando aplica).
  - Noticias/comunicados, métricas y otros servicios de soporte.
    
## Distribución: APK y AAB
- APK : pensado para instalación directa (pruebas internas, distribución manual).
- AAB : formato recomendado/obligatorio para publicación en Google Play.
- Soporte para variantes que evitan conflictos de instalación (útil si conviven builds de prueba y producción).
  
## Configuración clave (alto nivel)
- Variables de entorno en Vercel para credenciales de acceso (admin/dashboard), secretos de sesión y servicios de correo.
- Posibilidad de ajustar listas de usuarios/credenciales sin tocar el cliente (backend como punto de control).
  
## Evolución futura (extensible por diseño)
La arquitectura permite añadir, sin rehacer lo existente:
- Nuevos módulos (formularios, trámites, área privada, carnet digital, etc.).
- Roles y permisos más completos (admin, moderador, usuario, invitado).
- Persistencia avanzada y auditoría (base de datos, logs de actividad).
- Notificaciones segmentadas por campañas, eventos y perfiles.
- Chat con persistencia y sincronización completa en tiempo real.
- Integración con analítica y paneles de control más detallados.
  
## Resumen
La app móvil ya cubre lo esencial: acceso seguro , privacidad , consumo de comunicados , notificaciones controladas , intereses , chat base y menú de utilidades , todo conectado con un backend en Vercel y un panel web para gestión. A partir de esta base, se pueden incorporar nuevas funcionalidades de forma incremental y ordenada.


