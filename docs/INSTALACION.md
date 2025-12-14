# Guía de Instalación - Visual Board

## 🔧 Configuración del Entorno de Desarrollo

### Prerequisitos del Sistema

1. **Node.js** (v18.0 o superior)
   - Descargar desde: https://nodejs.org/
   - Verificar instalación: `node --version`

2. **Python** (v3.9 o superior)
   - Descargar desde: https://python.org/
   - Verificar instalación: `python --version`

3. **PostgreSQL** (v13 o superior)
   - Descargar desde: https://postgresql.org/
   - Verificar instalación: `psql --version`

4. **Git**
   - Descargar desde: https://git-scm.com/
   - Verificar instalación: `git --version`

## 📦 Instalación del Proyecto

### 1. Clonar el Repositorio
```bash
git clone https://github.com/emilianomillan/Segundo_Proyecto.git
cd Segundo_Proyecto
git checkout David
```

### 2. Configuración del Frontend
```bash
cd frontend
npm install
```

### 3. Configuración del Backend
```bash
cd ../backend
pip install -r requirements.txt
```

### 4. Configuración de la Base de Datos

#### Crear Base de Datos
```bash
createdb visual_board
```

#### Ejecutar Schema
```bash
psql visual_board < ../visual_board_schema.sql
```

## ⚙️ Variables de Entorno

### Backend (.env)
Crear archivo `.env` en la carpeta `backend/`:
```
DATABASE_URL=postgresql://username:password@localhost/visual_board
UNSPLASH_ACCESS_KEY=your_unsplash_api_key
```

### Frontend
La configuración del frontend se encuentra en `frontend/src/config/api.js`

## 🚀 Ejecutar el Proyecto

### Iniciar Backend
```bash
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

### Iniciar Frontend
```bash
cd frontend
npm run dev
```

## 🌐 URLs de Acceso

- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:8000
- **Documentación API:** http://localhost:8000/docs

## 🔍 Verificación de Instalación

### Verificar Backend
```bash
curl http://localhost:8000/api/health
```

### Verificar Frontend
Abrir navegador en http://localhost:5173

## ⚡ Scripts Útiles

### Frontend
- `npm run dev` - Servidor de desarrollo
- `npm run build` - Build de producción
- `npm run preview` - Vista previa del build

### Backend
- `uvicorn main:app --reload` - Servidor de desarrollo
- `python -m pytest` - Ejecutar tests

## 🛠️ Solución de Problemas

### Error de Base de Datos
1. Verificar que PostgreSQL esté ejecutándose
2. Comprobar credenciales en DATABASE_URL
3. Verificar que la base de datos existe

### Error de Dependencias
1. Limpiar cache de npm: `npm cache clean --force`
2. Eliminar node_modules y reinstalar: `rm -rf node_modules && npm install`
3. Actualizar pip: `pip install --upgrade pip`

### Error de Puertos
1. Verificar que los puertos 5173 y 8000 estén libres
2. Cambiar puertos en configuración si es necesario