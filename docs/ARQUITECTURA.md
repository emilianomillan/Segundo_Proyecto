# Arquitectura del Sistema - Visual Board

## 🏗️ Arquitectura General

Visual Board implementa una arquitectura de aplicación web moderna basada en separación de responsabilidades:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│    Frontend     │    │     Backend     │    │   Base de      │
│   (React SPA)   │◄──►│   (FastAPI)     │◄──►│   Datos        │
│                 │    │                 │    │  (PostgreSQL)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │
         ▼                       ▼
┌─────────────────┐    ┌─────────────────┐
│  GitHub Pages   │    │     Render      │
│   (Hosting)     │    │   (Hosting)     │
└─────────────────┘    └─────────────────┘
```

## 🎨 Frontend - React SPA

### Estructura de Componentes
```
src/
├── components/          # Componentes reutilizables
│   ├── BrokenImageHandler.jsx     # Manejo de imágenes rotas
│   ├── EmptyState.jsx             # Estado vacío
│   ├── ImageCard.jsx              # Tarjeta de imagen
│   ├── ImageHealthChecker.jsx     # Verificador de salud
│   ├── LoadingSpinner.jsx         # Indicador de carga
│   ├── MasonryGrid.jsx            # Grid tipo Pinterest
│   ├── Navigation.jsx             # Barra de navegación
│   ├── PostDetailModal.jsx        # Modal de detalles
│   ├── UserAuth.jsx               # Autenticación
│   └── UserLogin.jsx              # Inicio de sesión
├── pages/               # Páginas principales
│   ├── CreatePost.jsx             # Crear publicación
│   ├── Discover.jsx               # Descubrir contenido
│   ├── EditPost.jsx               # Editar publicación
│   ├── Home.jsx                   # Página principal
│   └── MyPosts.jsx                # Mis publicaciones
├── services/            # Servicios de API
│   └── api.js                     # Cliente HTTP
├── hooks/               # Custom Hooks
│   └── usePosts.js                # Hook para posts
├── config/              # Configuración
│   └── api.js                     # Config de API
└── utils/               # Utilidades
    └── cache.js                   # Sistema de cache
```

### Tecnologías Frontend
- **React 19.2.1**: Framework principal
- **React Router DOM**: Navegación SPA
- **Bootstrap 5**: Framework CSS
- **React Masonry CSS**: Layout de grilla
- **Axios**: Cliente HTTP
- **Vite**: Build tool y desarrollo

### Patrones de Diseño Frontend
- **Component Pattern**: Componentes reutilizables
- **Custom Hooks**: Lógica compartida
- **Context Pattern**: Estado global
- **Error Boundaries**: Manejo de errores
- **Lazy Loading**: Optimización de rendimiento

## 🔧 Backend - FastAPI

### Estructura del API
```
app/
├── api/                 # Endpoints de la API
│   ├── discover.py             # Endpoint de descubrimiento
│   ├── health.py               # Health check
│   ├── image_health.py         # Verificación de imágenes
│   ├── posts.py                # CRUD de posts
│   ├── upload.py               # Subida de archivos
│   └── users.py                # Gestión de usuarios
├── core/                # Configuración central
│   ├── config.py               # Configuración global
│   └── database.py             # Conexión a BD
├── models/              # Modelos de base de datos
│   ├── post.py                 # Modelo de Post
│   └── user.py                 # Modelo de Usuario
├── schemas/             # Esquemas de validación
│   ├── discover.py             # Schemas de descubrimiento
│   ├── post.py                 # Schemas de posts
│   └── user.py                 # Schemas de usuarios
└── services/            # Servicios de negocio
    └── unsplash_service.py     # Integración Unsplash
```

### Tecnologías Backend
- **FastAPI**: Framework web moderno
- **SQLAlchemy**: ORM para base de datos
- **Pydantic**: Validación de datos
- **Alembic**: Migraciones de BD
- **Python-multipart**: Manejo de archivos
- **Requests**: Cliente HTTP para APIs externas

### Patrones de Diseño Backend
- **Repository Pattern**: Abstracción de datos
- **Service Layer**: Lógica de negocio
- **Dependency Injection**: Inyección de dependencias
- **Schema Validation**: Validación automática
- **RESTful API**: Arquitectura REST

## 🗄️ Base de Datos - PostgreSQL

### Esquema de Base de Datos
```sql
-- Usuarios
Table: users
├── id (Primary Key)
├── username (Unique)
├── email (Unique)
├── password_hash
├── created_at
└── updated_at

-- Posts
Table: posts
├── id (Primary Key)
├── title
├── description
├── image_url
├── user_id (Foreign Key)
├── created_at
└── updated_at
```

### Relaciones
- **User → Posts**: Un usuario puede tener múltiples posts (1:N)
- **Índices optimizados** para consultas frecuentes
- **Constraints** para integridad referencial

## 🌐 APIs Externas

### Unsplash API
- **Propósito**: Fuente de imágenes de alta calidad
- **Endpoints utilizados**:
  - `/photos/random` - Imágenes aleatorias
  - `/search/photos` - Búsqueda de imágenes
- **Rate Limiting**: Respetado según términos de uso

## 🚀 Despliegue y DevOps

### Frontend - GitHub Pages
- **Build Process**: Vite optimizado para producción
- **Deployment**: GitHub Actions automático
- **CDN**: Distribución global automática
- **HTTPS**: Habilitado por defecto

### Backend - Render
- **Runtime**: Python 3.9+
- **Database**: PostgreSQL managed
- **Auto-deploy**: Desde rama main
- **Environment Variables**: Configuradas en dashboard

## 🔒 Seguridad

### Frontend
- **Input Validation**: Validación en cliente
- **XSS Prevention**: Sanitización de datos
- **CORS**: Configurado correctamente
- **Environment Variables**: No expuestas en build

### Backend
- **Password Hashing**: BCrypt
- **Input Validation**: Pydantic schemas
- **SQL Injection**: Prevención con ORM
- **Rate Limiting**: Implementado por endpoint
- **CORS**: Configuración restrictiva

## 📊 Rendimiento

### Frontend
- **Code Splitting**: Carga por rutas
- **Lazy Loading**: Imágenes y componentes
- **Caching**: Almacenamiento local
- **Bundle Optimization**: Tree shaking con Vite

### Backend
- **Database Indexing**: Consultas optimizadas
- **Connection Pooling**: Gestión eficiente de conexiones
- **Async Processing**: FastAPI asíncrono
- **Response Caching**: Cache de respuestas frecuentes

## 🔍 Monitoreo y Observabilidad

### Logs
- **Frontend**: Console logs en desarrollo
- **Backend**: Logging estructurado
- **Database**: Query logging

### Health Checks
- **Backend Health**: `/api/health`
- **Database Health**: Conexión verificada
- **External APIs**: Status de Unsplash

## 🧪 Testing

### Frontend
- **Unit Tests**: Componentes individuales
- **Integration Tests**: Flujos de usuario
- **E2E Tests**: Pruebas end-to-end

### Backend
- **Unit Tests**: Funciones individuales
- **API Tests**: Endpoints completos
- **Database Tests**: Modelos y queries