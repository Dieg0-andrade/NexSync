# Modelo de Datos - NexSync

Este documento describe la estructura inicial de datos usada por NexSync en Firebase Firestore.

## Base de datos

NexSync utiliza Cloud Firestore como base de datos NoSQL para almacenar información operativa en tiempo real.

La base utilizada es:

```txt
(default)
```

## Colecciones principales

```txt
companies
resources
crisis_events
alerts
negotiations
```

---

## 1. companies

Representa a las empresas u organizaciones participantes dentro de la red NexSync.

### Campos

| Campo      | Tipo   | Descripción                                                 |
| ---------- | ------ | ----------------------------------------------------------- |
| name       | string | Nombre de la empresa                                        |
| sector     | string | Sector económico: Agro, Industria, Energía, Agua, Logística |
| location   | string | Ubicación dentro de Santa Cruz                              |
| status     | string | Estado operativo de la empresa                              |
| waterNeed  | number | Nivel de necesidad de agua                                  |
| energyNeed | number | Nivel de necesidad de energía                               |
| fuelNeed   | number | Nivel de necesidad de combustible                           |

### Ejemplo

```txt
Documento: empresa_demo_1

name: AgroNorte
sector: Agro
location: Montero
status: operativa
waterNeed: 70
energyNeed: 40
fuelNeed: 50
```

---

## 2. resources

Representa recursos críticos disponibles o solicitables dentro de la red.

### Campos

| Campo          | Tipo    | Descripción                          |
| -------------- | ------- | ------------------------------------ |
| type           | string  | Tipo de recurso                      |
| name           | string  | Nombre descriptivo del recurso       |
| quantity       | number  | Cantidad disponible                  |
| unit           | string  | Unidad de medida                     |
| ownerCompanyId | string  | ID de la empresa propietaria         |
| available      | boolean | Indica si el recurso está disponible |

### Ejemplo

```txt
Documento: diesel_demo_1

type: combustible
name: Diesel industrial
quantity: 5000
unit: litros
ownerCompanyId: empresa_demo_1
available: true
```

---

## 3. crisis_events

Representa eventos de crisis que afectan la operación normal de las empresas.

### Campos

| Campo       | Tipo    | Descripción                      |
| ----------- | ------- | -------------------------------- |
| type        | string  | Tipo de crisis                   |
| location    | string  | Ubicación afectada               |
| severity    | string  | Nivel de severidad               |
| description | string  | Descripción del evento           |
| active      | boolean | Indica si el evento sigue activo |

### Ejemplo

```txt
Documento: bloqueo_demo_1

type: bloqueo
location: Carretera al Norte
severity: alta
description: Bloqueo afecta transporte de combustible y alimentos
active: true
```

---

## 4. alerts

Representa alertas operativas generadas a partir de riesgos o eventos críticos.

### Campos

| Campo   | Tipo    | Descripción                   |
| ------- | ------- | ----------------------------- |
| title   | string  | Título de la alerta           |
| message | string  | Mensaje operativo             |
| level   | string  | Nivel de criticidad           |
| read    | boolean | Indica si la alerta fue leída |

### Ejemplo

```txt
Documento: alerta_demo_1

title: Riesgo de desabastecimiento
message: AgroNorte podría quedarse sin combustible en 12 horas
level: alta
read: false
```

---

## 5. negotiations

Representa solicitudes o negociaciones de recursos entre empresas.

### Campos

| Campo          | Tipo      | Descripción                  |
| -------------- | --------- | ---------------------------- |
| buyerCompanyId | string    | ID de la empresa solicitante |
| resourceId     | string    | ID del recurso solicitado    |
| offer          | number    | Oferta o cantidad propuesta  |
| status         | string    | Estado de la negociación     |
| createdAt      | timestamp | Fecha de creación            |

### Ejemplo

```txt
Documento generado automáticamente

buyerCompanyId: empresa_demo_1
resourceId: diesel_demo_1
offer: 4500
status: pendiente
createdAt: timestamp
```

---

## Relación entre colecciones

```txt
companies
  └── puede poseer recursos en resources

resources
  └── referencia a companies mediante ownerCompanyId

crisis_events
  └── genera contexto para alerts

alerts
  └── informa riesgos a las empresas

negotiations
  └── conecta companies con resources
```

## Uso dentro del MVP

El MVP lee las colecciones `companies`, `resources`, `crisis_events`, `alerts` y `negotiations` desde Firestore.

Además, permite crear nuevas negociaciones desde la interfaz web. Cada negociación creada se almacena automáticamente en la colección `negotiations`.

## Próximas mejoras
* Agregar autenticación de usuarios.
* Asociar cada empresa con un usuario responsable.
* Agregar historial de decisiones por agente.
* Agregar prioridad automática de recursos.
* Integrar Gemini o Vertex AI para generar recomendaciones inteligentes.
