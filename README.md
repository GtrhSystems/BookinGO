# 📅 BookingGo - Sistema de Gestión de Citas y Reservas

<div align="center">

![BookingGo Logo](https://via.placeholder.com/200x80/4F46E5/FFFFFF?text=BookingGo)

[![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

**Plataforma completa de gestión de citas multi-empresa con funcionalidades avanzadas de reservas, personal y comunicación automatizada.**

[🚀 Demo en Vivo](http://185.182.187.200) • [📖 Documentación](docs/) • [🐛 Reportar Bug](issues/) • [💡 Solicitar Feature](issues/)

</div>

---

## 🌟 Características Principales

### 🏢 **Multi-Empresa & Multi-Tenant**
- Gestión completa de múltiples empresas desde una sola instalación
- Roles y permisos granulares (Super Admin, Empresa, Usuario)
- Configuraciones independientes por empresa

### 📅 **Sistema de Reservas Avanzado**
- **Gestión inteligente de disponibilidad** con slots dinámicos
- **Prevención de solapamientos** y control de capacidad
- **Horarios flexibles** con pausas personalizables
- **Gestión de festivos** y días no laborables
- **Reservas recurrentes** y citas grupales

### 👥 **Gestión de Personal**
- Asignación de servicios por empleado
- Horarios individuales y disponibilidad
- Seguimiento de rendimiento y estadísticas
- Sistema de notificaciones para el personal

### 💰 **Monetización & Planes**
- **Múltiples pasarelas de pago**: Stripe, PayPal, Square, Braintree, AuthorizeNet
- **Sistema de suscripciones** con Laravel Cashier Paddle
- **Cupones y descuentos** personalizables
- **Módulos activables** según el plan contratado

### 📧 **Comunicación Automatizada**
- **Plantillas de email multi-idioma** (ES, EN, FR, DE, etc.)
- **Recordatorios automáticos** de citas
- **Confirmaciones y cancelaciones** por email
- **Notificaciones SMS** (múltiples proveedores)
- **Integración con MailChimp** para marketing

### 🔧 **Integraciones & APIs**
- **Google Calendar** sincronización bidireccional
- **Códigos QR** para check-in rápido
- **Exportación iCal** para calendarios externos
- **API RESTful** con autenticación JWT
- **Webhooks** para integraciones personalizadas

---

## 🛠️ Tecnologías

### **Backend**
- **Laravel 11.x** - Framework PHP moderno
- **PHP 8.2+** - Lenguaje de programación
- **MySQL 8.0+** - Base de datos relacional
- **Redis** - Cache y sesiones
- **Queue System** - Procesamiento asíncrono

### **Frontend**
- **Blade Templates** - Motor de plantillas de Laravel
- **Vite** - Build tool moderno
- **Bootstrap 5** - Framework CSS
- **JavaScript ES6+** - Interactividad del cliente

### **Servicios Externos**
- **AWS S3** - Almacenamiento de archivos
- **Google APIs** - Calendar, Maps, reCAPTCHA
- **OpenAI** - Funcionalidades de IA
- **Múltiples SMS Providers** - Notificaciones móviles

---

## 🚀 Instalación Rápida

### Prerrequisitos
- PHP 8.2 o superior
- Composer 2.0+
- MySQL 8.0+ o MariaDB 10.3+
- Node.js 16+ (opcional)

### 1. Clonar el Repositorio
```bash
git clone https://github.com/GtrhSystems/BookinGO.git
cd BookinGO
```

### 2. Instalar Dependencias
```bash
composer install --optimize-autoloader
npm install && npm run build  # Opcional para desarrollo
```

### 3. Configurar Entorno
```bash
cp .env.example .env
php artisan key:generate
```

### 4. Configurar Base de Datos
```bash
# Crear base de datos
mysql -u root -p -e "CREATE DATABASE booking_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"

# Configurar .env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=booking_db
DB_USERNAME=tu_usuario
DB_PASSWORD=tu_contraseña
```

### 5. Ejecutar Migraciones y Seeders
```bash
php artisan migrate --seed
```

### 6. Configurar Permisos
```bash
chmod -R 775 storage bootstrap/cache uploads
php artisan storage:link
```

### 7. Iniciar Servidor
```bash
php artisan serve
```

🎉 **¡Listo!** Visita `http://localhost:8000` para acceder a la aplicación.

---

## 📋 Configuración Avanzada

### Variables de Entorno Importantes

```env
# Aplicación
APP_NAME="BookingGo"
APP_ENV=production
APP_URL=https://tu-dominio.com

# Base de Datos
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_DATABASE=booking_db
DB_USERNAME=booking_user
DB_PASSWORD=secure_password

# Email
MAIL_MAILER=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=tu-email@gmail.com
MAIL_PASSWORD=tu-app-password

# Pagos (Stripe ejemplo)
STRIPE_KEY=pk_live_...
STRIPE_SECRET=sk_live_...

# Google Services
GOOGLE_CLIENT_ID=tu-client-id
GOOGLE_CLIENT_SECRET=tu-client-secret
```

### Configuración de Cron Jobs
```bash
# Agregar al crontab
* * * * * cd /ruta/a/bookinggo && php artisan schedule:run >> /dev/null 2>&1
```

### Configuración de Queue Workers
```bash
# Supervisor configuration
php artisan queue:work --daemon --tries=3
```

---

## 🏗️ Arquitectura del Sistema

### Modelos Principales
- **User** - Usuarios del sistema (Super Admin, Empresa, Cliente)
- **Business** - Empresas/Negocios
- **Service** - Servicios ofrecidos
- **Staff** - Personal/Empleados
- **Appointment** - Citas/Reservas
- **Location** - Ubicaciones/Sucursales
- **Plan** - Planes de suscripción

### Flujo de Reservas
1. **Cliente** selecciona servicio y personal
2. **Sistema** calcula disponibilidad en tiempo real
3. **Validación** de slots y capacidad
4. **Confirmación** automática por email/SMS
5. **Recordatorios** programados
6. **Check-in** con código QR

---

## 🔐 Seguridad

- **Autenticación JWT** para APIs
- **Roles y permisos** con Laratrust
- **Protección CSRF** en formularios
- **Validación de entrada** en todos los endpoints
- **Rate limiting** para prevenir abuso
- **Logs de auditoría** para acciones críticas

---

## 📊 Monitoreo y Analytics

### Métricas Incluidas
- Reservas por período
- Ingresos por servicio/personal
- Tasas de cancelación
- Ocupación por horarios
- Satisfacción del cliente

### Herramientas de Debug
```bash
# Habilitar debug bar (solo desarrollo)
composer require barryvdh/laravel-debugbar --dev

# Logs detallados
tail -f storage/logs/laravel.log
```

---

## 🚀 Despliegue en Producción

### Usando Docker
```bash
# Construir imagen
docker build -t bookinggo .

# Ejecutar contenedor
docker run -d -p 80:80 --name bookinggo-app bookinggo
```

### Despliegue Manual
```bash
# Optimizaciones de producción
composer install --no-dev --optimize-autoloader
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

### CI/CD con GitHub Actions
El proyecto incluye workflows automatizados para:
- ✅ Tests automáticos
- 🚀 Despliegue a staging
- 📦 Despliegue a producción con aprobación manual

---

## 🧪 Testing

```bash
# Ejecutar todos los tests
php artisan test

# Tests con cobertura
php artisan test --coverage

# Tests específicos
php artisan test --filter=AppointmentTest
```

---

## 🤝 Contribuir

1. **Fork** el proyecto
2. **Crea** una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. **Commit** tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. **Push** a la rama (`git push origin feature/AmazingFeature`)
5. **Abre** un Pull Request

### Estándares de Código
- Seguir **PSR-12** para PHP
- **PHPStan** nivel 8 para análisis estático
- **Tests unitarios** para nuevas funcionalidades
- **Documentación** actualizada

---

## 📝 Changelog

### v2.1.0 (2024-01-15)
- ✨ Nuevo sistema de horarios flexibles
- 🔧 Integración con OpenAI para sugerencias
- 🐛 Corrección de bugs en cálculo de disponibilidad
- 📱 Mejoras en responsive design

### v2.0.0 (2023-12-01)
- 🎉 Refactorización completa a Laravel 11
- 🔐 Nuevo sistema de autenticación JWT
- 💳 Integración con múltiples pasarelas de pago
- 🌍 Soporte multi-idioma completo

---

## 📞 Soporte

### Documentación
- 📖 [Wiki del Proyecto](wiki/)
- 🎥 [Video Tutoriales](docs/videos/)
- 📋 [FAQ](docs/faq.md)

### Comunidad
- 💬 [Discord](https://discord.gg/bookinggo)
- 📧 [Email de Soporte](mailto:support@bookinggo.com)
- 🐛 [Reportar Issues](issues/)

### Soporte Comercial
Para soporte empresarial y personalizaciones:
- 🏢 **Email**: enterprise@bookinggo.com
- 📞 **Teléfono**: +1 (555) 123-4567
- 🌐 **Web**: [bookinggo.com/enterprise](https://bookinggo.com/enterprise)

---

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 🙏 Agradecimientos

- **Laravel Team** - Por el increíble framework
- **Contribuidores** - Por hacer este proyecto mejor cada día
- **Comunidad PHP** - Por el ecosistema de herramientas

---

<div align="center">

**¿Te gusta BookingGo? ¡Dale una ⭐ al repositorio!**

Hecho con ❤️ por [GtrhSystems](https://github.com/GtrhSystems)

</div>