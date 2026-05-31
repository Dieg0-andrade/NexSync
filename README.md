# NexSync

**NexSync** es una plataforma de resiliencia operativa para empresas de Santa Cruz ante crisis locales como bloqueos, cortes de energía, escasez de combustible, problemas logísticos o interrupciones de suministro.

El MVP funciona como un **Enterprise Resilience Command Center** que conecta empresas, recursos críticos, eventos de riesgo, alertas, negociaciones y una capa de IA generativa para apoyar decisiones operativas.

Demo pública:

```txt
https://hackaton-nexsync.web.app
```

---

## Problema

Durante una crisis local, muchas empresas reaccionan de forma aislada:

* No saben qué empresas están en riesgo.
* No saben qué recursos críticos están disponibles.
* No tienen una forma rápida de coordinar apoyo operativo.
* Las decisiones se toman tarde, sin visibilidad compartida.
* La falta de coordinación puede generar pérdidas económicas y operativas.

---

## Solución

NexSync centraliza la información crítica en una consola operativa conectada a Firebase Firestore.

La plataforma permite:

* Monitorear empresas y estado operativo.
* Visualizar recursos críticos disponibles.
* Detectar eventos de riesgo activos.
* Consultar alertas operativas.
* Crear negociaciones manuales.
* Generar recomendaciones operativas.
* Simular coordinación multirol entre empresas.
* Generar un brief ejecutivo con Gemini API.
* Cambiar entre vista global y vistas por empresa.
* Inyectar crisis de prueba para demostrar respuesta del sistema.

---

## MVP actual

El MVP incluye:

* Dashboard conectado a Firebase Firestore.
* Vista global de consorcio.
* Vistas por organización/empresa.
* KPIs operativos.
* Empresas monitoreadas.
* Recursos críticos.
* Eventos de riesgo.
* Alertas.
* Historial de negociaciones.
* Motor de recomendación operativa.
* Flujo de coordinación multirol.
* Módulo de pruebas para inyectar crisis.
* Integración con Gemini API para generar AI Operational Briefs.
* Deploy público en Firebase Hosting.

---

## Funcionalidades principales

### 1. Consola de operaciones

Muestra una vista general del estado operativo:

* Empresas monitoreadas.
* Recursos disponibles.
* Eventos de riesgo activos.
* Negociaciones registradas.
* Crisis prioritaria detectada.

---

### 2. Vistas por organización

NexSync permite cambiar entre:

* Vista Consorcio Global.
* Vista AgroNorte.
* Vista EnergiaPiraí.
* Vista TransporteMontero.
* Vista FrigoSantaCruz.

La vista global muestra toda la red operativa.
Las vistas por empresa muestran información filtrada según la organización seleccionada.

En producción, esta lógica se protegería con Firebase Auth y reglas de Firestore por organización.

---

### 3. Decision Engine

El motor de decisión analiza:

* Crisis activas.
* Empresas afectadas.
* Recursos disponibles.
* Ubicación.
* Severidad.
* Proveedor sugerido.

Luego genera una recomendación operativa para crear una negociación prioritaria.

---

### 4. Gemini AI Operational Brief

El MVP integra Gemini API para generar un resumen ejecutivo operativo a partir del contexto real del sistema.

El brief generado incluye:

* Resumen ejecutivo.
* Riesgo detectado.
* Empresa afectada.
* Recurso recomendado.
* Impacto operativo.
* Justificación.
* Próximo paso sugerido.

Esta integración demuestra uso real de IA generativa dentro del flujo operativo.

---

### 5. Coordination Workflow

Simula una coordinación multirol entre:

* Empresa afectada.
* Proveedor del recurso.
* Evaluador de riesgo.
* Capa coordinadora NexSync.

El resultado puede registrarse como una negociación validada.

---

### 6. Módulo de pruebas

Incluye un inyector de crisis para demo.

Permite crear eventos críticos en Firestore y ver cómo el sistema recalcula KPIs y actualiza el tablero.

Escenarios disponibles:

* Bloqueo de ruta.
* Déficit de diésel.
* Corte de energía.
* Estrés hídrico.

---

## Tecnologías usadas

* HTML
* CSS
* JavaScript
* Firebase Firestore
* Firebase Hosting
* Gemini API
* GitHub
* Live Server para desarrollo local

---

## Arquitectura general

```txt
Usuario / Jurado
      ↓
NexSync Web App
      ↓
Firebase Hosting
      ↓
Firebase Firestore
      ↓
Empresas, recursos, crisis, alertas y negociaciones
      ↓
Decision Engine + Gemini API
      ↓
Recomendación operativa + AI Operational Brief
```

---

## Estructura del proyecto

```txt
NexSync/
├─ index.html
├─ config.js          # No se sube a GitHub
├─ .gitignore
├─ README.md
├─ assets/
└─ docs/
```

---

## Configuración local

Para ejecutar el proyecto localmente:

1. Clonar o descargar el repositorio.
2. Crear un archivo `config.js` en la misma carpeta que `index.html`.
3. Agregar la Gemini API key en `config.js`.

Ejemplo:

```js
window.NEXSYNC_CONFIG = {
  GEMINI_API_KEY: "PEGAR_AQUI_GEMINI_API_KEY"
};
```

4. Abrir `index.html` con Live Server.

---

## Seguridad de API keys

La Gemini API key no se sube a GitHub.

El archivo `config.js` está excluido mediante `.gitignore`.

```txt
config.js
public/config.js
serviceAccountKey.json
*.env
.env
node_modules/
```

Para el MVP de hackatón, la API key se carga desde un archivo local de configuración.

En producción, esta integración debería moverse a Firebase Functions o un backend seguro para proteger credenciales y aplicar control de acceso por organización.

---

## Firebase

El MVP usa Firebase Firestore como base de datos operativa.

Colecciones principales:

```txt
companies
resources
crisis_events
alerts
negotiations
```

### companies

Representa empresas conectadas a la red NexSync.

Campos esperados:

```txt
name
sector
location
status
```

### resources

Representa recursos críticos disponibles.

Campos esperados:

```txt
name
type
quantity
unit
ownerCompanyId
available
```

### crisis_events

Representa eventos de riesgo o crisis operativas.

Campos esperados:

```txt
type
description
location
severity
active
companyId
createdAt
```

### alerts

Representa alertas operativas.

Campos esperados:

```txt
title
message
level
read
```

### negotiations

Representa negociaciones entre empresas.

Campos esperados:

```txt
buyerCompanyId
resourceId
offer
status
agentFlow
createdAt
```

---

## Deploy

El proyecto está desplegado en Firebase Hosting.

URL de demo:

```txt
https://hackaton-nexsync.web.app
```

---

## Flujo de demo recomendado

1. Abrir la consola de operaciones.
2. Mostrar KPIs y crisis prioritaria.
3. Cambiar entre vista global y vista de empresa.
4. Ir al módulo de pruebas.
5. Simular una crisis.
6. Volver a la consola de operaciones.
7. Generar recomendación operativa.
8. Generar AI Operational Brief con Gemini.
9. Ejecutar Coordination Workflow.
10. Registrar decisión validada.
11. Mostrar el historial de negociaciones.

---

## Propuesta de valor

NexSync ayuda a empresas y operadores de infraestructura crítica a coordinar recursos durante crisis locales, reduciendo tiempos de respuesta, pérdidas operativas y decisiones aisladas.

El sistema puede ser usado por:

* Cámaras empresariales.
* Parques industriales.
* Empresas agroindustriales.
* Operadores logísticos.
* Empresas de energía.
* Empresas de agua.
* Municipios o centros de coordinación.

---

## Modelo de negocio

Modelo B2B SaaS orientado a empresas, asociaciones productivas y operadores de infraestructura crítica.

Posibles clientes:

* Parques industriales.
* Cámaras empresariales.
* Cooperativas.
* Empresas logísticas.
* Agroindustrias.
* Operadores energéticos.
* Operadores de agua.
* Gobiernos municipales o centros de emergencia.

Posibles planes:

* Plan empresa individual.
* Plan consorcio.
* Plan cámara/asociación.
* Plan enterprise con integración avanzada.

---

## Impacto esperado

NexSync busca reducir:

* Tiempo de respuesta ante crisis.
* Pérdidas por interrupción operativa.
* Falta de coordinación entre empresas.
* Duplicación de esfuerzos.
* Decisiones tomadas sin visibilidad de recursos disponibles.

También permite aumentar:

* Visibilidad operativa.
* Coordinación interempresarial.
* Uso eficiente de recursos críticos.
* Capacidad de respuesta ante crisis locales.
* Resiliencia de sectores productivos en Santa Cruz.

---

## Diferenciadores

* Enfoque local en problemáticas reales de Santa Cruz.
* Uso de Firebase Firestore para datos operativos.
* Integración con Gemini API para generación de briefs ejecutivos.
* Vistas por organización para simular privacidad empresarial.
* Flujo de coordinación multirol.
* Módulo de pruebas para inyectar crisis y demostrar reacción del sistema.
* Consola enterprise orientada a industria, logística, energía, agua y agro.

---

## Roadmap

### MVP actual

* Firestore conectado.
* Dashboard operativo.
* Vistas por organización.
* Motor de decisión.
* Gemini AI Brief.
* Simulación de coordinación.
* Inyector de crisis.
* Firebase Hosting.

### Próximas mejoras

* Firebase Auth.
* Reglas de Firestore por organización.
* Firebase Functions para Gemini.
* Integración con mapas.
* Métricas de impacto económico.
* Notificaciones en tiempo real.
* Auditoría de decisiones.
* Modelos predictivos de riesgo.
* Integración con datos externos de clima, tráfico o bloqueos.
* Panel administrativo para operadores de consorcio.
* Historial completo de decisiones por empresa.

---

## Estado del MVP

```txt
Etapa 1: Dashboard conectado a Firestore
Etapa 2: Agente de recomendación operativa
Etapa 3: Simulación de coordinación multirol
Etapa 4: UI enterprise / Operations Console
Etapa 5: Gemini AI Operational Brief
Etapa 6: Firebase Hosting
```

---

## Equipo

Proyecto desarrollado para la Hackathon Build With AI 2026 organizada por GDG Santa Cruz.
Integrantes:
* Diego Andrade
* Sebastian Aspiazu
* Salim Suarez
* Mathias Frias
* Daniel Roca
* 
  

