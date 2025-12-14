# Visual Board - Proyecto Integrador COM-11117

## 📋 Información del Proyecto

**Nombre:** Visual Board - Aplicación Web Tipo Pinterest  
**Materia:** COM-11117 - Proyecto Integrador  
**Institución:** Universidad Tecnológica de Querétaro  
**Fecha:** Diciembre 2024  

## 👥 Equipo de Desarrollo

- **David Fernando Avila Díaz** - 197851
- **Emiliano Sebastián Millán Giffard** - 214360

## 🎯 Descripción del Proyecto

Visual Board es una aplicación web inspirada en Pinterest que permite a los usuarios crear, compartir y gestionar contenido visual de manera intuitiva. La plataforma combina funcionalidades modernas de frontend con un backend robusto para ofrecer una experiencia de usuario completa.

## ✨ Características Principales

### 🖼️ Gestión de Imágenes
- Carga y visualización de imágenes desde Unsplash API
- Subida de imágenes personalizadas
- Visualización en grid tipo masonry
- Verificación automática de salud de imágenes

### 👤 Sistema de Usuarios
- Registro e inicio de sesión
- Gestión de perfil de usuario
- Autenticación segura

### 📱 Funcionalidades de Contenido
- Creación y edición de posts
- Vista detallada de contenido
- Página de descubrimiento
- Gestión personal de posts

### 🎨 Experiencia de Usuario
- Interfaz responsive con Bootstrap
- Navegación intuitiva
- Estados de carga y manejo de errores
- Diseño moderno y limpio

## 🛠️ Tecnologías Utilizadas

### Frontend
- **React 19.2.1** - Framework principal
- **Vite 7.2.7** - Build tool y desarrollo
- **React Router DOM 7.10.1** - Navegación
- **Bootstrap 5.3.8** - Framework CSS
- **Axios 1.13.2** - Cliente HTTP
- **React Masonry CSS** - Layout de grilla

### Backend
- **FastAPI** - Framework web de Python
- **SQLAlchemy** - ORM para base de datos
- **PostgreSQL** - Base de datos principal
- **Pydantic** - Validación de datos
- **Python-multipart** - Manejo de archivos

### Servicios Externos
- **Unsplash API** - Fuente de imágenes
- **Render** - Hosting del backend
- **GitHub Pages** - Hosting del frontend

## 📁 Estructura del Proyecto

```
Segundo_Proyecto/
├── frontend/                    # Aplicación React
│   ├── src/
│   │   ├── components/         # Componentes reutilizables
│   │   ├── pages/             # Páginas de la aplicación
│   │   ├── services/          # Servicios de API
│   │   ├── hooks/             # Custom hooks
│   │   ├── config/            # Configuraciones
│   │   └── utils/             # Utilidades
│   ├── public/                # Assets públicos
│   ├── index.html             # HTML principal
│   ├── package.json           # Dependencias del frontend
│   └── vite.config.js         # Configuración de Vite
├── backend/                    # API FastAPI
│   ├── app/
│   │   ├── api/               # Endpoints de la API
│   │   ├── core/              # Configuración central
│   │   ├── models/            # Modelos de base de datos
│   │   ├── schemas/           # Esquemas de validación
│   │   └── services/          # Servicios del backend
│   ├── main.py                # Archivo principal
│   └── requirements.txt       # Dependencias de Python
├── visual_board_schema.sql     # Esquema de base de datos
├── docs/                      # Documentación adicional
└── README.md                  # Este archivo
```

## 🚀 Instalación y Configuración

### Prerequisitos
- Node.js (v18 o superior)
- Python (v3.9 o superior)
- PostgreSQL
- Git

### Frontend
```bash
cd frontend
npm install
npm run dev
```

### Backend
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```

### Base de Datos
```bash
# Crear base de datos PostgreSQL
createdb visual_board

# Ejecutar schema
psql visual_board < visual_board_schema.sql
```

## 🔧 Configuración

### Variables de Entorno (Backend)
```
DATABASE_URL=postgresql://username:password@localhost/visual_board
UNSPLASH_ACCESS_KEY=your_unsplash_api_key
```

## 📱 Funcionalidades Implementadas

### ✅ Frontend
- [x] Componente de navegación responsive
- [x] Página de inicio con grid de imágenes
- [x] Sistema de autenticación completo
- [x] Gestión de posts (crear, editar, eliminar)
- [x] Vista de descubrimiento con API de Unsplash
- [x] Modal de detalles de post
- [x] Manejo de estados de carga y error
- [x] Componente de verificación de salud de imágenes

### ✅ Backend
- [x] API RESTful con FastAPI
- [x] Autenticación de usuarios
- [x] CRUD completo de posts
- [x] Integración con Unsplash API
- [x] Subida de archivos
- [x] Verificación de salud de imágenes
- [x] Base de datos PostgreSQL

## 🌐 Despliegue

### Frontend
- **URL de producción:** https://dabtcavila.github.io/WEB-VisualBoard
- **Plataforma:** GitHub Pages
- **Build:** Vite optimizado para producción

### Backend
- **URL de API:** https://visual-board-api.onrender.com
- **Plataforma:** Render
- **Base de datos:** PostgreSQL en Render

## 📊 Testing y Calidad

- Verificación automática de imágenes rotas
- Manejo de errores y estados de carga
- Validación de formularios
- Responsive design testing

## 🔮 Futuras Mejoras

- Implementar sistema de likes y comentarios
- Añadir categorías y etiquetas
- Sistema de seguimiento de usuarios
- Notificaciones en tiempo real
- PWA (Progressive Web App)

## 📝 Licencia

Este proyecto fue desarrollado como parte del Proyecto Integrador de la Universidad Tecnológica de Querétaro.

---

**© 2024 Visual Board - Proyecto Integrador COM-11117**  
Desarrollado por David Fernando Avila Díaz y Emiliano Sebastián Millán Giffard
