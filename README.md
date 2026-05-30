# NexSync

Plataforma de resiliencia operativa multiagente para crisis locales en Santa Cruz de la Sierra.

## Problema
En Santa Cruz, eventos como bloqueos, cortes de energía, escasez de combustible, interrupciones logísticas o falta de agua pueden afectar directamente la operación de empresas, productores, industrias y servicios esenciales.
Actualmente, muchas organizaciones reaccionan de forma aislada, sin coordinación, sin visibilidad compartida de recursos y sin mecanismos inteligentes para anticipar riesgos o negociar apoyo operativo.

## Solución
NexSync propone una red operativa inteligente donde cada empresa puede registrar su estado, necesidades y recursos disponibles. La plataforma permite simular agentes de IA que monitorean recursos críticos, detectan riesgos y proponen negociaciones entre empresas.

## Objetivo del MVP
El MVP permite:
* Visualizar empresas registradas.
* Visualizar recursos críticos disponibles.
* Visualizar eventos de crisis activos.
* Visualizar alertas operativas.
* Crear negociaciones de recursos entre empresas.
* Conectar una interfaz web con Firebase Firestore.

## Flujo principal
1. Una empresa registra su estado operativo.
2. El sistema muestra sus necesidades de agua, energía o combustible.
3. Se registra un evento de crisis local.
4. La plataforma muestra alertas operativas.
5. Una empresa solicita un recurso crítico.
6. Se crea una negociación en Firestore.
7. La información queda disponible para la demo.

## Arquitectura técnica
```txt
Usuario
  ↓
Interfaz Web NexSync
  ↓
Firebase Web SDK
  ↓
Cloud Firestore
  ↓
Colecciones:
- companies
- resources
- crisis_events
- alerts
- negotiations
```

## Tecnologías utilizadas
* HTML
* CSS
* JavaScript
* Firebase Firestore
* Firebase Web SDK
* GitHub

## Estructura de Firestore
### companies
Guarda información de empresas participantes.
Campos principales:
```txt
name
sector
location
status
waterNeed
energyNeed
fuelNeed
```

### resources
Guarda recursos críticos disponibles.
Campos principales:
```txt
type
name
quantity
unit
ownerCompanyId
available
```

### crisis_events
Guarda eventos de crisis locales.
Campos principales:

```txt
type
location
severity
description
active
```

### alerts
Guarda alertas operativas.
Campos principales:
```txt
title
message
level
read
```

### negotiations
Guarda negociaciones de recursos entre empresas.
Campos principales:
```txt
buyerCompanyId
resourceId
offer
status
createdAt
```

## Aplicación de IA
La visión del sistema es implementar agentes de IA capaces de:

* Analizar necesidades operativas de cada empresa.
* Detectar riesgos de desabastecimiento.
* Priorizar recursos críticos.
* Recomendar acciones ante crisis.
* Simular negociación entre empresas.
* Generar alertas inteligentes.

## Cómo ejecutar el MVP
1. Clonar o descargar el repositorio.
2. Abrir el archivo `index.html`.
3. Ejecutarlo con Live Server en VS Code.
4. Verificar que Firestore tenga las colecciones necesarias.
5. Probar la creación de negociaciones desde la interfaz.

## Estado del proyecto
MVP en desarrollo para la Hackathon Build With AI 2026 Santa Cruz.

## Equipo
Nombre del equipo: BOCOL
Integrantes:
* Diego Andrade Canedo
* Elias Daniel Roca Padilla
* Salim Elias Suarez Vespa
* David Rodrigo Torrico Vera
* Sebastian Aspiazu Mojica
* Jherson Mathias Frias Cerspedes
