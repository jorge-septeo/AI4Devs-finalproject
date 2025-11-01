## Índice

0. [Ficha del proyecto](#0-ficha-del-proyecto)
1. [Descripción general del producto](#1-descripción-general-del-producto)
2. [Arquitectura del sistema](#2-arquitectura-del-sistema)
3. [Modelo de datos](#3-modelo-de-datos)
4. [Especificación de la API](#4-especificación-de-la-api)
5. [Historias de usuario](#5-historias-de-usuario)
6. [Tickets de trabajo](#6-tickets-de-trabajo)
7. [Pull requests](#7-pull-requests)

---

## 0. Ficha del proyecto

### **0.1. Tu nombre completo:**
JGM

### **0.2. Nombre del proyecto:**
**RepoAgents** - AI Agent Integration Template

### **0.3. Descripción breve del proyecto:**
RepoAgents es una plantilla de repositorio que transforma cualquier proyecto en un equipo completo de desarrollo mediante la integración de múltiples agentes de IA. Permite a desarrolladores individuales trabajar con diferentes roles y perfiles de agentes (GitHub Copilot, Gemini CLI, Claude, Jules, OpenCode, etc.) a través de comunicación asíncrona en GitHub Issues y Pull Requests, utilizando el estándar AGENTS.md como configuración central.

### **0.4. URL del proyecto:**
Proyecto educativo (Proyecto Final AI4Devs). https://github.com/jorge-septeo/AI4Devs-finalproject

### 0.5. URL o archivo comprimido del repositorio
**GitHub Repository**: https://github.com/jorge-septeo/AI4Devs-finalproject

> **Nota**: El repositorio es privado con fines educativos. El acceso puede compartirse de forma segura mediante invitación de GitHub o mediante el servicio [onetimesecret](https://onetimesecret.com/) si es necesario para evaluación.


---

## 1. Descripción general del producto

### **1.1. Objetivo:**

**RepoAgents** tiene como propósito facilitar el acceso a equipos de desarrollo completos mediante inteligencia artificial. 

**Problema que soluciona:**
- Los desarrolladores individuales a menudo necesitan cumplir múltiples roles: desarrollador, revisor de código, arquitecto, tester, documentador, etc.
- La colaboración asíncrona con IA puede ser caótica sin una estructura clara
- Cada proveedor de agentes IA tiene su propia configuración y formato
- No existe un estándar claro para instruir a múltiples agentes en un mismo proyecto

**Valor que aporta:**
- **Plantilla lista para usar**: Configuraciones pre-establecidas para 7+ agentes IA diferentes
- **Estándar unificado**: Utiliza AGENTS.md como punto central de configuración
- **Automatización GitHub**: Workflows para code review, testing y documentación automáticos
- **Educacional**: Ejemplos claros de cómo usar cada agente y cuándo
- **Flexible**: Usa solo los agentes que necesites, ignora el resto

**Para quién:**
- Desarrolladores individuales que quieren aumentar su productividad
- Equipos pequeños que quieren experimentar con IA en desarrollo
- Estudiantes aprendiendo sobre desarrollo asistido por IA (como este proyecto educativo)
- Proyectos que quieren facilitar contribuciones con IA
- Cualquiera interesado en el estándar AGENTS.md

### **1.2. Características y funcionalidades principales:**

#### 1. **Archivo AGENTS.md Central**
- Configuración unificada que todos los agentes pueden leer
- Incluye guías de código, testing, documentación y PRs
- Formato Markdown estándar y extensible
- Compatible con el estándar https://agents.md/

#### 2. **Configuraciones Multi-Agente**
Incluye configuraciones específicas para:
- **GitHub Copilot**: `.github/copilot-instructions.md` para sugerencias contextuales
- **Gemini CLI**: `agents/gemini/.gemini/settings.json` para análisis y documentación
- **Claude**: `agents/claude/claude-config.md` para code review profundo
- **OpenCode**: `agents/opencode/opencode-rules.md` para calidad de código
- **Jules**: `agents/jules/jules-config.md` para implementación full-stack
- Preparado para Codex, Factory y otros agentes

#### 3. **GitHub Actions Workflows**
- **agent-code-review.yml**: Review automático de PRs con métricas
- **agent-testing.yml**: Validación de tests y configuraciones
- Reportes automáticos en Pull Requests
- Validación de cobertura de código

#### 4. **Templates de Issues**
- Template estructurado para feature requests
- Campos específicos para que agentes procesen las peticiones
- Labels automáticos para organización
- Acceptance criteria predefinidos

#### 5. **Documentación Completa**
- **Setup Guide**: Guía paso a paso para configurar cada agente
- **Agent Comparison**: Matriz comparativa de capacidades
- **Examples**: Ejemplos de AGENTS.md para diferentes proyectos
- Mejores prácticas para cada agente

#### 6. **Herramientas de Desarrollo**
- ESLint y Prettier configurados
- Jest para testing
- TypeScript con modo estricto
- Scripts npm para validación automática

### **1.3. Diseño y experiencia de usuario:**

**Flujo de trabajo principal:**

```
1. Developer clona/usa template
   ↓
2. Personaliza AGENTS.md para su proyecto
   ↓
3. Elige qué agentes usar
   ↓
4. Crea issues para tareas
   ↓
5. Menciona agentes (@claude, @jules)
   ↓
6. Agentes responden/implementan
   ↓
7. GitHub Actions validan cambios
   ↓
8. Merge automatizado o manual
```

**Interfaz de usuario:**

El proyecto es principalmente una plantilla de repositorio, por lo que la "interfaz" es:
- **GitHub Issues**: Para crear tareas y comunicarse con agentes
- **GitHub Pull Requests**: Para reviews automáticos y manuales
- **IDE (VS Code)**: Para desarrollo con Copilot y otros agentes
- **Terminal**: Para comandos de Gemini CLI y otros CLIs
- **GitHub Actions**: Para ver resultados de automatizaciones

**Capturas de flujo** (ejemplo conceptual):

```
┌─────────────────────────────────────────┐
│  1. Create Issue with Feature Request  │
│  Template auto-fills structure         │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  2. Agent (@jules) analyzes and plans   │
│  Posts implementation plan as comment   │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  3. Agent creates PR with changes       │
│  GitHub Actions auto-review triggers    │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  4. Review bot comments on PR           │
│  Coverage, lint, test results shown     │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  5. Developer/agent addresses feedback  │
│  Uses Copilot for quick fixes           │
└─────────────────────────────────────────┘
              ↓
┌─────────────────────────────────────────┐
│  6. Final validation passes → Merge!    │
└─────────────────────────────────────────┘
```

### **1.4. Instrucciones de instalación:**

#### **Requisitos previos:**
- **Git**: v2.x o superior
- **Node.js**: v18.x o superior
- **npm**: v9.x o superior
- **Cuenta de GitHub**: Para usar como template
- **Acceso a al menos un agente IA**: Copilot, Claude, Gemini, etc.

#### **Opción 1: Usar como Template (Recomendado)**

```bash
# 1. Si tienes acceso al repositorio, puedes usarlo como template
#    o clonar la estructura para tu propio proyecto

# 2. Clona el repositorio (requiere acceso)
git clone https://github.com/jorge-septeo/AI4Devs-finalproject.git
cd AI4Devs-finalproject

# 3. Instala dependencias
npm install

# 4. Verifica la instalación
npm test
```

#### **Opción 2: Clonar directamente**

```bash
# 1. Clonar el repositorio
git clone https://github.com/jorge-septeo/AI4Devs-finalproject.git
cd AI4Devs-finalproject

# 2. Instalar dependencias
npm install

# 3. Ejecutar tests para verificar
npm test

# 4. Validar configuraciones de agentes
npm run validate
```

#### **Configuración de Agentes:**

##### **GitHub Copilot** (Opcional - requiere suscripción)
```bash
# 1. Instala VS Code
# 2. Instala extensión GitHub Copilot
# 3. Inicia sesión con tu cuenta GitHub
# 4. El archivo .github/copilot-instructions.md se detectará automáticamente
```

##### **Google Gemini CLI** (Opcional - tiene tier gratuito)
```bash
# 1. Instala Gemini CLI
npm install -g @google/generative-ai-cli

# 2. Configura tu API key
export GEMINI_API_KEY="tu-api-key-aqui"

# 3. Agrega a tu shell profile
echo 'export GEMINI_API_KEY="tu-api-key"' >> ~/.zshrc

# 4. Prueba
gemini "Hola, revisa el AGENTS.md"
```

##### **Claude** (Opcional - API o claude.ai)
```bash
# Opción A: Via claude.ai
# 1. Ve a https://claude.ai
# 2. Sube archivos del proyecto
# 3. Referencia: "Sigue las guías en agents/claude/claude-config.md"

# Opción B: Via API
export CLAUDE_API_KEY="tu-api-key-aqui"
```

##### **Otros Agentes**
```bash
# OpenCode, Jules, Factory: Consulta docs/setup-guide.md
# para instrucciones detalladas de cada agente
```

#### **Estructura del Proyecto:**

```
proyecto/
├── AGENTS.md                       # ⭐ Configuración principal
├── .github/
│   ├── copilot-instructions.md     # Config Copilot
│   ├── workflows/                  # GitHub Actions
│   └── ISSUE_TEMPLATE/             # Templates issues
├── agents/                         # Configs específicas
│   ├── gemini/
│   ├── claude/
│   ├── opencode/
│   └── jules/
├── docs/                           # Documentación
│   ├── setup-guide.md
│   └── agent-comparison.md
├── examples/                       # Ejemplos
├── package.json                    # Dependencias Node
└── README.md                       # Este archivo
```

#### **Comandos Disponibles:**

```bash
# Testing
npm test                    # Ejecutar tests
npm run test:watch          # Tests en modo watch
npm run test:coverage       # Tests con coverage

# Linting
npm run lint                # Verificar código
npm run lint:fix            # Arreglar problemas automáticamente

# Formateo
npm run format              # Formatear código
npm run format:check        # Verificar formato

# Validación completa
npm run validate            # Lint + Format + Tests

# Documentación
npm run docs                # Generar docs API
```

#### **Verificación de Instalación:**

```bash
# 1. Tests pasan
npm test
# ✅ Debería mostrar: Tests: X passed

# 2. Lint pasa
npm run lint
# ✅ Sin errores

# 3. Validación de agentes
npm run validate
# ✅ Todas las configuraciones válidas
```

#### **Personalización Inicial:**

1. **Actualiza AGENTS.md** con información de tu proyecto:
   ```bash
   # Edita las secciones:
   # - Project Overview
   # - Setup Commands
   # - Project Structure
   ```

2. **Elige tus agentes**:
   ```bash
   # Elimina carpetas de agentes que no uses
   rm -rf agents/jules  # Por ejemplo
   ```

3. **Actualiza package.json**:
   ```bash
   # Cambia nombre, descripción, autor, etc.
   ```

4. **Configura GitHub Actions**:
   ```bash
   # Ve a Settings > Actions en GitHub
   # Habilita workflows
   ```

5. **Agrega secrets** (si usas APIs):
   ```bash
   # Settings > Secrets and variables > Actions
   # Agrega: GEMINI_API_KEY, CLAUDE_API_KEY, etc.
   ```

#### **¡Listo!** 🎉

Ahora puedes:
- Crear issues con el template
- Mencionar agentes en comentarios
- Abrir PRs que serán auto-reviewed
- Usar Copilot mientras codeas
- Ejecutar `gemini "comando"` para análisis

Para más detalles, consulta `docs/setup-guide.md`

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**
> Usa el formato que consideres más adecuado para representar los componentes principales de la aplicación y las tecnologías utilizadas. Explica si sigue algún patrón predefinido, justifica por qué se ha elegido esta arquitectura, y destaca los beneficios principales que aportan al proyecto y justifican su uso, así como sacrificios o déficits que implica.


### **2.2. Descripción de componentes principales:**

> Describe los componentes más importantes, incluyendo la tecnología utilizada

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

> Representa la estructura del proyecto y explica brevemente el propósito de las carpetas principales, así como si obedece a algún patrón o arquitectura específica.

### **2.4. Infraestructura y despliegue**

> Detalla la infraestructura del proyecto, incluyendo un diagrama en el formato que creas conveniente, y explica el proceso de despliegue que se sigue

### **2.5. Seguridad**

> Enumera y describe las prácticas de seguridad principales que se han implementado en el proyecto, añadiendo ejemplos si procede

### **2.6. Tests**

> Describe brevemente algunos de los tests realizados

---

## 3. Modelo de Datos

### **3.1. Diagrama del modelo de datos:**

> Recomendamos usar mermaid para el modelo de datos, y utilizar todos los parámetros que permite la sintaxis para dar el máximo detalle, por ejemplo las claves primarias y foráneas.


### **3.2. Descripción de entidades principales:**

> Recuerda incluir el máximo detalle de cada entidad, como el nombre y tipo de cada atributo, descripción breve si procede, claves primarias y foráneas, relaciones y tipo de relación, restricciones (unique, not null…), etc.

---

## 4. Especificación de la API

> Si tu backend se comunica a través de API, describe los endpoints principales (máximo 3) en formato OpenAPI. Opcionalmente puedes añadir un ejemplo de petición y de respuesta para mayor claridad

---

## 5. Historias de Usuario

> Documenta 3 de las historias de usuario principales utilizadas durante el desarrollo, teniendo en cuenta las buenas prácticas de producto al respecto.

**Historia de Usuario 1**

**Historia de Usuario 2**

**Historia de Usuario 3**

---

## 6. Tickets de Trabajo

> Documenta 3 de los tickets de trabajo principales del desarrollo, uno de backend, uno de frontend, y uno de bases de datos. Da todo el detalle requerido para desarrollar la tarea de inicio a fin teniendo en cuenta las buenas prácticas al respecto. 

**Ticket 1**

**Ticket 2**

**Ticket 3**

---

## 7. Pull Requests

> Documenta 3 de las Pull Requests realizadas durante la ejecución del proyecto

**Pull Request 1**

**Pull Request 2**

**Pull Request 3**

