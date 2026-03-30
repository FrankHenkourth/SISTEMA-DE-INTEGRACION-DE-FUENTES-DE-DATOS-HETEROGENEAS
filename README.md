# SISTEMA DE INTEGRACIÓN DE FUENTES DE DATOS HETEROGÉNEAS

## Trabajo de Diploma para optar por el título de Ingeniero en Ciencias Informáticas

**Autor:** Frank Ernesto Cortiñas Peña  
**Tutor:** Dr.C. Yunieski Coca Bergolla | Lic. Prof. Aux  
**Institución:** Universidad de las Ciencias Informáticas (UCI)  
**Facultad:** Facultad de Tecnologías Educativas  
**Departamento:** Inteligencia Computacional

---

## 📋 Resumen

Este sistema permite integrar y consolidar de forma eficiente fuentes de datos heterogéneas provenientes de distintas fuentes institucionales utilizando tecnologías libres. La solución facilita la ingestión, transformación y almacenamiento de información proveniente de archivos CSV, hojas de cálculo y bases de datos relacionales, garantizando la consistencia y trazabilidad de los datos integrados.

El sistema está diseñado para resolver la problemática de gestión de datos fragmentados en el Departamento de Inteligencia Computacional de la UCI, donde la información relevante se encuentra distribuida en diversas fuentes sin un mecanismo automatizado que permita su integración sistemática.

---

## 🎯 Objetivo General

Desarrollar un sistema de integración de datos basado en tecnologías libres que permita estructurar el proceso de ingestión, almacenamiento y consolidación de información proveniente de fuentes heterogéneas, con el propósito de facilitar la generación de información analítica y apoyar la toma de decisiones en el Departamento de Inteligencia Computacional de la Universidad de las Ciencias Informáticas.

### Objetivos Específicos

1. **Analizar** los fundamentos teóricos y tecnológicos relacionados con la integración de datos heterogéneos y las tecnologías libres, así como diagnosticar la situación actual de la gestión de información en el departamento.

2. **Diseñar e implementar** un sistema de integración de datos basado en una aplicación de escritorio (PyQt) y un entorno contenerizado (Docker), que permita la ingestión, transformación y almacenamiento de información.

3. **Validar** el sistema desarrollado mediante casos de uso reales del departamento, evaluando su funcionamiento a través de métricas de eficiencia, consistencia de la información y usabilidad.

---

## 🛠️ Tecnologías Utilizadas

### Lenguaje de Programación
- **Python 3.13** - Lenguaje principal para lógica de negocio y procesamiento de datos

### Bibliotecas de Python
- **Pandas** - Manipulación, transformación y validación de datos estructurados
- **SQLAlchemy** - ORM para gestión de conexiones y operaciones con base de datos
- **PyQt6** - Framework para desarrollo de interfaz gráfica de usuario
- **FastAPI** - Framework para creación de API de ingesta

### Base de Datos
- **PostgreSQL** - Sistema gestor de bases de datos relacional para almacenamiento estructurado

### Contenedorización
- **Docker** - Plataforma de contenedores para despliegue, portabilidad y aislamiento del entorno

### Herramientas de Desarrollo
- **Git** - Control de versiones
- **Visual Studio Code** - Editor de código
- **DBeaver / pgAdmin** - Administración de base de datos

---

## 🏗️ Arquitectura del Sistema

El sistema sigue una **arquitectura híbrida ETL/ELT** compuesta por:

```
┌─────────────────────────────────────────────────────────────┐
│                    APLICACIÓN DE ESCRITORIO                  │
│                        (PyQt6)                               │
│  ┌─────────────┬─────────────┬──────────────────────────┐   │
│  │   Carga de  │ Previsuali- │   Envío de datos         │   │
│  │   archivos  │ zación      │   hacia API              │   │
│  │   (CSV/XLSX)│             │                          │   │
│  └─────────────┴─────────────┴──────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    ENTORNO CONTENERIZADO                     │
│                        (Docker)                              │
│  ┌──────────────────────────────────────────────────────┐   │
│  │                   FastAPI                             │   │
│  │            (Servicio de ingesta)                      │   │
│  │    • Validación automática de datos                   │   │
│  │    • Documentación Swagger                            │   │
│  └──────────────────────────────────────────────────────┘   │
│                              │                                │
│                              ▼                                │
│  ┌──────────────────────────────────────────────────────┐   │
│  │                  PostgreSQL                           │   │
│  │           (Data Warehouse)                            │   │
│  │    • Almacenamiento estructurado                      │   │
│  │    • Consultas analíticas                             │   │
│  │    • Trazabilidad de datos                            │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Flujo de Procesamiento

1. **Extracción**: Lectura de datos desde archivos CSV, Excel o bases de datos externas
2. **Transformación**: Limpieza, normalización y validación usando Pandas
3. **Carga**: Almacenamiento en PostgreSQL mediante SQLAlchemy
4. **Visualización**: Consulta de datos integrados desde la aplicación PyQt6

---

## ✨ Características Principales

- **Integración de fuentes heterogéneas**: Soporte para CSV, Excel (XLSX) y bases de datos relacionales
- **Interfaz gráfica intuitiva**: Aplicación de escritorio desarrollada con PyQt6 para usuarios no técnicos
- **Validación automática de datos**: Verificación de tipo, formato, rango e integridad referencial
- **Trazabilidad completa**: Registro de metadatos de cada carga (fuente, fecha, usuario, transformaciones)
- **Arquitectura contenerizada**: Despliegue portable y reproducible con Docker
- **Tecnologías 100% libres**: Sin costos de licencias, alineado con políticas institucionales
- **Procesos ETL/ELT**: Enfoque híbrido según características de cada fuente
- **API REST documentada**: Servicio de ingesta con documentación Swagger automática

---

## 📦 Requisitos

### Requisitos del Sistema
- Sistema operativo: Windows, Linux o macOS
- RAM: Mínimo 4 GB (8 GB recomendado)
- Espacio en disco: 2 GB libres mínimo

### Requisitos de Software
- Python 3.13 o superior
- Docker Desktop (para entornos contenerizados)
- Git (para control de versiones)

---

## 🚀 Instalación

### 1. Clonar el repositorio
```bash
git clone <url-del-repositorio>
cd <nombre-del-proyecto>
```

### 2. Crear entorno virtual (recomendado)
```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows
```

### 3. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 4. Configurar el entorno contenerizado
```bash
docker-compose up -d
```

### 5. Ejecutar migraciones de base de datos
```bash
python alembic upgrade head
```

---

## 💻 Uso

### Iniciar la aplicación de escritorio
```bash
python main.py
```

### Funcionalidades disponibles

1. **Carga de archivos**: Seleccione archivos CSV o Excel para importar
2. **Previsualización**: Visualice los datos antes de confirmar la carga
3. **Validación**: El sistema valida automáticamente el esquema y formato
4. **Envío**: Los datos se transfieren al entorno contenerizado vía API
5. **Consulta**: Acceda a los datos integrados desde la interfaz

### Acceso a la API
La documentación interactiva de la API está disponible en:
```
http://localhost:8000/docs
```

---

## 📁 Estructura del Proyecto

```
├── app/
│   ├── desktop/          # Aplicación PyQt6
│   ├── api/              # Servicio FastAPI
│   ├── models/           # Modelos de datos
│   ├── services/         # Lógica de negocio
│   └── utils/            # Utilidades
├── docker/
│   └── postgresql/       # Configuración de base de datos
├── docs/                 # Documentación técnica
├── tests/                # Pruebas unitarias
├── requirements.txt      # Dependencias de Python
├── docker-compose.yml    # Orquestación de contenedores
└── README.md            # Este archivo
```

---

## 📊 Resultados Esperados

1. **Caracterización del proceso actual** de gestión de datos en el departamento
2. **Arquitectura de integración** basada en tecnologías libres
3. **Modelo de ingestión y almacenamiento** con procesos ETL/ELT
4. **Prototipo funcional** del sistema de integración
5. **Mecanismos de visualización** de información integrada
6. **Documentación técnica** completa (manuales, guías, especificaciones)

---

## 📝 Consideraciones Técnicas

- **Licencias**: Todas las tecnologías utilizadas son de código abierto
- **Portabilidad**: El sistema puede desplegarse en diferentes infraestructuras
- **Escalabilidad**: La arquitectura permite crecimiento horizontal
- **Mantenibilidad**: Código modular y documentado según buenas prácticas
- **Seguridad**: Validación automática y control transaccional de datos

---

## 📚 Referencias

- Abadi, D., Boncz, P. & Harizopoulos, S. (2022). *Database Management Systems*
- Stonebraker, M., Madden, S. & Helland, J. (2022). *Data Integration and Heterogeneity*
- Wang, et al. (2025). *Modern Data Engineering with Python*
- Zhang, L., Chen, X. & Meng, Q. (2025). *Open Source Technologies for Data Integration*

---

## 👤 Contacto

**Autor:** Frank Ernesto Cortiñas Peña  
**Correo:** epena@estudiantes.uci.cu  
**Institución:** Universidad de las Ciencias Informáticas, La Habana, Cuba

---

## 📄 Licencia

Este proyecto es parte de un Trabajo de Diploma y su titularidad corresponde a la Universidad de las Ciencias Informáticas (UCI) según normativa vigente.

---

*La Habana, diciembre de 2024*  
*Año 68 del Triunfo de la Revolución*
