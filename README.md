# NexSync

**NexSync** es una plataforma de resiliencia operativa para empresas de Santa Cruz ante crisis locales como bloqueos, cortes de energía, escasez de combustible, problemas logísticos o interrupciones de suministro.

El MVP funciona como un **Enterprise Resilience Command Center** que conecta empresas, recursos críticos, eventos de riesgo, alertas, negociaciones y una capa de IA generativa para apoyar decisiones operativas.

---

## Problema

Durante una crisis local, muchas empresas reaccionan de forma aislada:

- No saben qué empresas están en riesgo.
- No saben qué recursos críticos están disponibles.
- No tienen una forma rápida de coordinar apoyo operativo.
- Las decisiones se toman tarde, sin visibilidad compartida.
- La falta de coordinación puede generar pérdidas económicas y operativas.

---

## Solución

NexSync centraliza la información crítica en una consola operativa conectada a Firebase Firestore.

La plataforma permite:

- Monitorear empresas y estado operativo.
- Visualizar recursos críticos disponibles.
- Detectar eventos de riesgo activos.
- Consultar alertas operativas.
- Crear negociaciones manuales.
- Generar recomendaciones operativas.
- Simular coordinación multirol entre empresas.
- Generar un brief ejecutivo con Gemini API.
- Cambiar entre vista global y vistas por empresa.

---

## MVP actual

El MVP incluye:

- Dashboard conectado a Firebase Firestore.
- Vista global de consorcio.
- Vistas por organización/empresa.
- KPIs operativos.
- Empresas monitoreadas.
- Recursos críticos.
- Eventos de riesgo.
- Alertas.
- Historial de negociaciones.
- Motor de recomendación operativa.
- Flujo de coordinación multirol.
- Módulo de pruebas para inyectar crisis.
- Integración con Gemini API para generar AI Operational Briefs.
- Preparación para deploy en Firebase Hosting.

---

## Funcionalidades principales

### 1. Consola de operaciones

Muestra una vista general del estado operativo:

- Empresas monitoreadas.
- Recursos disponibles.
- Eventos de riesgo activos.
- Negociaciones registradas.
- Crisis prioritaria detectada.

---

### 2. Vistas por organización

NexSync permite cambiar entre:

- Vista Consorcio Global.
- Vista AgroNorte.
- Vista EnergiaPiraí.
- Vista TransporteMontero.
- Vista FrigoSantaCruz.

La vista global muestra toda la red operativa.  
Las vistas por empresa muestran información filtrada según la organización seleccionada.

En producción, esta lógica se protegería con Firebase Auth y reglas de Firestore por organización.

---

### 3. Decision Engine

El motor de decisión analiza:

- Crisis activas.
- Empresas afectadas.
- Recursos disponibles.
- Ubicación.
- Severidad.
- Proveedor sugerido.

Luego genera una recomendación operativa para crear una negociación prioritaria.

---

### 4. Gemini AI Operational Brief

El MVP integra Gemini API para generar un resumen ejecutivo operativo a partir del contexto real del sistema.

El brief generado incluye:

- Resumen ejecutivo.
- Riesgo detectado.
- Empresa afectada.
- Recurso recomendado.
- Impacto operativo.
- Justificación.
- Próximo paso sugerido.

Esta integración demuestra uso real de IA generativa dentro del flujo operativo.

---

### 5. Coordination Workflow

Simula una coordinación multirol entre:

- Empresa afectada.
- Proveedor del recurso.
- Evaluador de riesgo.
- Capa coordinadora NexSync.

El resultado puede registrarse como una negociación validada.

---

### 6. Módulo de pruebas

Incluye un inyector de crisis para demo.

Permite crear eventos críticos en Firestore y ver cómo el sistema recalcula KPIs y actualiza el tablero.

Escenarios disponibles:

- Bloqueo de ruta.
- Déficit de diésel.
- Corte de energía.
- Estrés hídrico.

---

## Tecnologías usadas

- HTML
- CSS
- JavaScript
- Firebase Firestore
- Firebase Hosting
- Gemini API
- GitHub
- Live Server para desarrollo local

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
