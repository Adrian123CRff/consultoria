# Sistema de Auditorías ISO/IEC 27002 — DataSolutions CR

Aplicación web MVC en PHP 8 y MySQL para gestionar auditorías de seguridad de bases de datos basadas en el estándar ISO/IEC 27002.

## Características

- Autenticación con sesiones seguras y protección CSRF
- Gestión de usuarios (admin, auditor, viewer), organizaciones y áreas
- Catálogo de dominios y controles ISO/IEC 27002 con pesos de impacto (C, I, D)
- Ejecución de cuestionarios de auditoría con niveles de madurez (0–5)
- Subida de evidencias por pregunta
- Cálculo automático de madurez ponderada y exposición al riesgo (Confidencialidad, Integridad, Disponibilidad)
- Reporte ejecutivo completo con gráficos (Chart.js) y mapas de calor
- Comparación de auditorías para seguimiento histórico
- Gestión de recomendaciones de mejora

## Requisitos

| Componente | Versión mínima |
|---|---|
| PHP | 8.1 |
| MySQL / MariaDB | 8.0 / 10.6 |
| Extensiones PHP | `pdo`, `pdo_mysql`, `mbstring`, `fileinfo` |

## Instalación

1. Copiar el proyecto en el directorio del servidor web (ej. `C:\wamp64\www\consultora`).
2. Crear la base de datos ejecutando el script SQL:

```bash
mysql -u root -p < sql/schema.sql
```

3. Ajustar credenciales en `config/database.php` o mediante variables de entorno:

| Variable | Default |
|---|---|
| `DB_HOST` | `127.0.0.1` |
| `DB_PORT` | `3306` |
| `DB_DATABASE` | `consultora_iso27002` |
| `DB_USERNAME` | `root` |
| `DB_PASSWORD` | _(vacío)_ |

4. Iniciar el servidor:

```bash
php -S localhost:8000 -t public
```

O acceder desde WAMP en `http://localhost/consultora/public/`.

## Credenciales iniciales

| Campo | Valor |
|---|---|
| Correo | `admin@datasolutionscr.net` |
| Contraseña | `Admin123*` |

> Cambiar la contraseña del administrador después del primer acceso en producción.

## Estructura principal

```
consultora/
├── app/
│   ├── controllers/   # Controladores MVC
│   ├── core/          # Router, Auth, CSRF, MaturityCalculator, etc.
│   ├── models/        # Modelos PDO
│   └── views/         # Vistas PHP por módulo
├── config/            # Configuración de BD y aplicación
├── public/            # Front controller, assets, uploads
├── routes/web.php     # Definición de rutas
├── sql/schema.sql     # Script de creación de base de datos
└── database/          # Scripts de migración por fase
```

## Documentación

- [Manual de Usuario](MANUAL_USUARIO.md)
- [Manual Técnico](MANUAL_TECNICO.md)
