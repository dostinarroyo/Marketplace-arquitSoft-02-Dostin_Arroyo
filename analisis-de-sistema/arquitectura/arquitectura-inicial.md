# Arquitectura inicial del sistema

## Ejercicio 09: Diseño de la arquitectura en capas

La primera propuesta organiza los módulos del marketplace en una arquitectura de tres capas:

```text
┌──────────────────────────────────────────────┐
│ PRESENTACIÓN                                 │
│ Aplicación web / API REST / Interfaz         │
└──────────────────────┬───────────────────────┘
                       ↓
┌──────────────────────────────────────────────┐
│ LÓGICA DE NEGOCIO                            │
│ Usuarios │ Sellers │ Catálogo │ Carrito      │
│ Pedidos                                      │
└──────────────────────┬───────────────────────┘
                       ↓
┌──────────────────────────────────────────────┐
│ DATOS                                        │
│ Base de datos                                │
└──────────────────────────────────────────────┘
```

| Capa | Responsabilidad | Pregunta que responde |
|---|---|---|
| Presentación | Proporciona la aplicación web y la API REST para interactuar con las funcionalidades del marketplace. | ¿Cómo interactúa el usuario? |
| Lógica de negocio | Implementa las reglas y operaciones de usuarios, sellers, catálogo, carrito y pedidos. | ¿Qué hace el sistema? |
| Datos | Almacena y permite consultar la información del sistema mediante una base de datos. | ¿Dónde se almacena la información? |

## Ejercicio 10: Diagrama de arquitectura inicial

El diagrama integra los actores, la presentación, los módulos de negocio, la base de datos y los sistemas externos identificados para el marketplace.

```mermaid
flowchart TD
    subgraph ACTORES["ACTORES"]
        Cliente["Cliente"]
        Seller["Seller"]
        Admin["Administrador"]
    end

    subgraph PRESENTACION["PRESENTACIÓN"]
        Web["Aplicación Web"]
        API["API REST"]
        Web --> API
    end

    subgraph NEGOCIO["LÓGICA DE NEGOCIO"]
        Usuarios["Usuarios"]
        Sellers["Sellers"]
        Catalogo["Catálogo"]
        Carrito["Carrito"]
        Pedidos["Pedidos"]
    end

    subgraph DATOS["DATOS"]
        BD[("Base de datos")]
    end

    subgraph EXTERNOS["SISTEMAS EXTERNOS"]
        Pago["Pasarela de pago"]
        Envio["Servicio de envío"]
        ERP["ERP"]
    end

    Cliente --> Web
    Seller --> Web
    Admin --> Web
    API --> Usuarios
    API --> Sellers
    API --> Catalogo
    API --> Carrito
    API --> Pedidos

    Usuarios --> BD
    Sellers --> BD
    Catalogo --> BD
    Carrito --> BD
    Pedidos --> BD

    Pedidos -->|"Procesar pago"| Pago
    Pedidos -->|"Gestionar entrega"| Envio
    Catalogo -->|"Consultar productos y stock"| ERP
```

## Descripción

- **Presentación:** permite a clientes, sellers y administradores utilizar el marketplace mediante la aplicación web. La API REST recibe y expone las solicitudes hacia la lógica del sistema.
- **Lógica de negocio:** contiene los módulos de usuarios, sellers, catálogo, carrito y pedidos, que implementan las funcionalidades principales.
- **Datos:** la base de datos almacena la información necesaria para el funcionamiento del marketplace.
- **Sistemas externos:** los pedidos se integran con una pasarela de pago y un servicio de envío; el catálogo consulta productos y stock del ERP.
