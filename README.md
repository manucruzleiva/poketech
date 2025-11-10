# PokeTech - Sistema de Guías de Matchups para Pokemon TCG Live

## Descripción del Proyecto
PokeTech es una aplicación web moderna diseñada para ayudar a los jugadores de Pokemon Trading Card Game Live a mejorar su juego a través de un sistema inteligente de análisis de matchups y generación de guías estratégicas.

## Características Principales
- 🎮 Gestión de mazos con cartas del TCG Pokemon
- 📊 Análisis detallado de matchups entre mazos
- 🤖 Generación de guías estratégicas con IA
- 📱 Interfaz responsive accesible desde cualquier dispositivo
- 🔄 Sincronización en tiempo real de datos

## Stack Tecnológico

### Frontend
- **Framework**: Flutter Web
- **Estado**: Flutter Riverpod
- **HTTP Client**: Dio
- **Almacenamiento Local**: SharedPreferences
- **UI/UX**: Material Design 3, Google Fonts, Flutter Animate

### Backend
- **Framework**: FastAPI
- **Base de Datos**: PostgreSQL (Amazon RDS)
- **Autenticación**: JWT
- **APIs Externas**: 
  - Pokemon TCG API
  - OpenAI API

### Infraestructura
- **Despliegue**: AWS App Runner
- **Base de Datos**: Amazon RDS (PostgreSQL)
- **Secretos**: AWS Secrets Manager
- **CI/CD**: GitHub Actions

## Estructura del Proyecto

```
poketech/
├── frontend/                 # Aplicación Flutter Web
│   ├── lib/
│   │   ├── core/            # Configuraciones y utilidades core
│   │   │   ├── config/      # Configuración de la app
│   │   │   ├── network/     # Cliente HTTP y manejo de API
│   │   │   └── theme/       # Tema y estilos
│   │   ├── features/        # Módulos de la aplicación
│   │   │   ├── auth/        # Autenticación
│   │   │   ├── deck/        # Gestión de mazos
│   │   │   └── matchup/     # Análisis de matchups
│   │   └── main.dart        # Punto de entrada
│   ├── pubspec.yaml         # Dependencias Flutter
│   ├── Dockerfile          # Construcción de imagen
│   └── apprunner.yaml      # Configuración App Runner
│
├── backend/                 # API FastAPI
│   ├── app/
│   │   ├── api/            # Endpoints de la API
│   │   ├── core/           # Configuraciones core
│   │   ├── models/         # Modelos de datos
│   │   └── services/       # Lógica de negocio
│   ├── requirements.txt    # Dependencias Python
│   ├── Dockerfile         # Construcción de imagen
│   └── apprunner.yaml     # Configuración App Runner
│
└── .github/
    └── workflows/          # GitHub Actions CI/CD
```

## Configuración del Entorno de Desarrollo

### Prerequisitos
- Flutter SDK (última versión estable)
- Python 3.11+
- VS Code con extensiones Flutter y Python
- PostgreSQL (local o acceso a RDS)

### Configuración Frontend
```bash
# Navegar al directorio frontend
cd frontend

# Instalar dependencias
flutter pub get

# Ejecutar en modo desarrollo
flutter run -d chrome
```

### Configuración Backend
```bash
# Navegar al directorio backend
cd backend

# Crear entorno virtual
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar servidor de desarrollo
uvicorn app.main:app --reload
```

## Variables de Entorno y Secretos
El proyecto utiliza AWS Secrets Manager para gestionar las siguientes variables:

```yaml
database-url: URL de conexión a PostgreSQL RDS
jwt-secret: Clave para firma de tokens JWT
pokemon-tcg-api-key: API key para Pokemon TCG API
openai-api-key: API key para OpenAI API
```

## Despliegue

### Frontend
El frontend se despliega automáticamente en AWS App Runner:
1. Se construye la aplicación Flutter Web
2. Se sirve a través de Nginx
3. Configuración automática de SSL/TLS

### Backend
El backend se despliega en AWS App Runner:
1. Se construye la API FastAPI
2. Conexión automática con RDS
3. Gestión de secretos a través de AWS Secrets Manager

## Flujo de CI/CD
1. Push a main o PR trigger el workflow
2. Ejecución de tests
3. Construcción de imágenes
4. Despliegue automático en App Runner

## Monitoreo y Logs
- Métricas de App Runner
- Logs en CloudWatch
- Alertas configuradas para:
  - Errores de aplicación
  - Latencia alta
  - Uso de recursos

## Contribución
1. Crear branch: `feature/nombre-feature`
2. Implementar cambios
3. Asegurar que tests pasan
4. Crear PR a main
5. Code review y merge

## Comandos Útiles

### Frontend
```bash
# Generar código
flutter pub run build_runner build

# Análisis estático
flutter analyze

# Ejecutar tests
flutter test
```

### Backend
```bash
# Verificar formato
black .

# Ejecutar tests
pytest

# Verificar tipos
mypy .
```

## Enlaces Útiles
- [Documentación API](url-a-tu-api-docs)
- [Flutter Docs](https://flutter.dev/docs)
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [AWS App Runner](https://aws.amazon.com/apprunner/)
- [Pokemon TCG API](https://docs.pokemontcg.io/)

## Estado del Proyecto
![GitHub Workflow Status](url-a-tu-badge)
![API Status](url-a-tu-badge)

## Licencia
Este proyecto está licenciado bajo los términos de la licencia MIT.