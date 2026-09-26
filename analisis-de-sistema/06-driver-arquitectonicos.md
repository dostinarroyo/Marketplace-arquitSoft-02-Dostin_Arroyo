# 06 - Drivers arquitectónicos

## Objetivo
Integrar los elementos identificados anteriormente y determinar cuál de ellos influye de manera significativa en las decisiones de arquitectura.

## Drivers arquitectónicos

| ID | Driver arquitectónico | Origen | ¿Por qué influye en la arquitectura? |
|---|---|---|---|
| DA01 | El sistema debe soportar un incremento importante de usuarios durante campañas comerciales. | AC03 - Escalabilidad | Puede influir en la estrategia de escalamiento y despliegue. |
| DA02 | El sistema debe mantener tiempos de respuesta adecuados durante una alta concurrencia. | AC01 - Rendimiento | Puede influir en la comunicación entre componentes, procesamiento y almacenamiento. |
| DA03 | El sistema debe proteger los datos de usuarios y operaciones de compra. | AC04 - Seguridad | Puede influir en autenticación, autorización y protección de datos. |
| DA04 | El sistema debe integrarse con una pasarela de pago externa mediante una API. | RC04 - Pasarela de pago | Condiciona la forma de comunicación e integración con servicios externos. |
| DA05 | El sistema debe integrarse con servicios externos para envío y facturación. | RC05 - Servicio de envío / Facturación | Afecta la interoperabilidad, tolerancia a fallos y diseño de adaptadores. |
| DA06 | El sistema debe permitir crecimiento del catálogo de productos y vendedores. | HU02, HU05 | Influye en la estructura de datos, capacidad de almacenamiento y modularidad del sistema. |

## Observación
Los drivers arquitectónicos representan los factores más relevantes para definir los patrones y decisiones de diseño del marketplace.

