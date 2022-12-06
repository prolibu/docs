# Tu CRM o ERP + Prolibu®

## Acerca de las integraciones

Las integraciones son herramientas y servicios que se conectan con Prolibu® para complementar y extender tu flujo de trabajo.

## Ayude a sus equipos a crear impactantes propuestas comerciales sin salir de su CRM o ERP

Prolibu® es un motor de propuestas inteligente (SPE), que le permite crear impactantes propuestas comerciales en tiempo récord, con la capacidad de predicción del verdadero interés de compra del cliente.

Los agentes comerciales pasan una cantidad considerable de tiempo formulando propuestas atractivas de cara al cliente, monitoreando leads calificados de forma subjetiva, etc. Esto requiere un tiempo considerable. La integración de Prolibu® con su CRM o ERP le brinda a usted la posibilidad de: 

- Crear al instante impactantes propuestas comerciales, siguiendo un estricto lineamiento de marca

- Disponer de robots cotizadores que trabajan 24x7 formulando propuestas comerciales desde su sitio web

- Conocer el preciso instante en el que su cliente estudia la propuesta comercial y abórdelo vía chat

- Predecir el verdadero interés de compra del cliente frente a la propuesta comercial

- Organizar sus propuestas de acuerdo al interés de compra del cliente y priorice las que tienen alta probabilidad de cierre

Entre muchos otros beneficios.

La integración de Prolibu® para su CRM o ERP está construida y mantenida por Prolibu®. 

## Tabla de Contenido

- [Implementación de la integración de Prolibu® para su CRM o ERP](#implementación-de-la-integración-de-prolibu-para-su-crm-o-erp) 
  - [Requisitos](#requisitos)
  - [Implementación](#implementación)
  - [Flujo Integración](#flujo-integración)
- [Como Empezar](#como-empezar)
  - [Definición del contrato de datos](#definición-del-contrato-de-datos)
  - [Información básica](#información-básica)
  - [Obtener un ApiKey de conexión](#obtener-un-apikey-de-conexión)
  - [Consumo ApiRest personalizados](#consumo-apirest-personalizados)
  - [Suscribirse a eventos mediante Prolibu® Webhooks](#suscribirse-a-eventos-mediante-prolibu-webhooks)

---------------

## Implementación de la integración de Prolibu® para su CRM o ERP

### Requisitos

- Contar con una cuenta activa en Prolibu®
- Obtener un token de autorización de acceso a los datos de la cuenta
- Poder realizar solicitudes de tipo REST
- Contar dentro de su CRM o ERP con la información de:
  - Leads/Clientes
  - Agentes comerciales
  - Lista(s) de precio(s)

### Implementación

Los CustomObjects en Prolibu® son objetos que parten desde cero y permiten cubrir las necesidades particulares de su negocio, expuestos bajo el estándar RESTful y soportando formatos como XML o JSON.

### Flujo Integración

![Flujo Integración!](https://s3.amazonaws.com/files.nodriza.io/sales/Wilmar%20Ibarguen/Integracion%20Directa.jpeg)

## Como Empezar

### Definición del contrato de datos

Estos CustomObjects son implementados dentro de su cuenta Prolibu® por uno de nuestros expertos de TI mediante un contrato de datos en el cual se acuerdan que campos y comportamientos debe tener este nuevo objeto dentro de la plataforma. A continuación veremos un ejemplo de los campos en un contrato de datos.

```json
{
    "uuid": "090392-T90",
    "lead": {
        "firtsName": "Jane",
        "lastName": "Doe",  
        "email": "janed@prolibu.com",
        "mobile": "+57 3128932934",
        "metadata": {
            "source": "Facebook"
        }
    },
    "agent": {
        "firtsName": "John",
        "lastName": "Doe",  
        "email": "jdoe@prolibu.com",
        "mobile": "+57 3128932934"
    },
    "data": {
        "title": "Get now!",
        "expirationDate": "2021-03-30",
        "metadata": {
            "commercialTerms": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam egestas eu risus nec tristique.",
            "relatedInformationTable": "<table><thead><tr><th>one</th></tr></thead><tbody><tr><td>description</td></tr></tbody></table>",
            "financinglPlan": {
                "start": 2000,
                "monthlyPayment": 200,
                "interestRate": 1.5
            }
        },
        "products": [
            {
                "name": "PRODUCT NAME",
                "sku": "992DNUW92UE",
                "quantity": 1,
                "discountRate": 10,
                "price" : 10000,
                "currency": "USD",
                "metadata": {
                    "images": [
                        "https://s3.amazonaws.com/cdn.prolibu.com/rest-api-doc-images/Profile-menu.png",
                        "https://s3.amazonaws.com/cdn.prolibu.com/rest-api-doc-images/Profile-menu.png"
                    ]
                }    
            }
        ] 
    }
}
```

### Información básica

Para la creación de una propuesta comercial en Prolibu® se hace requerida la siguiente información:

#### UUID 
llave foranea entre su CRM o ERP y Prolibu® 

#### Agent
Información sobre el agente comercial que atiende la propuesta comercial. Campos Requeridos:

- firtsName
- lastName
- email

[Ver todos campos disponibles](https://prolibu-docs.github.io/docs/#/reference-user)

#### Lead
Información sobre el lead/cliente a quien va dirigida la propuesta comercial. Campos Requeridos:

- firtsName
- lastName
- email

[Ver todos campos disponibles](https://prolibu-docs.github.io/docs/#/reference-lead)

#### Data
Información que ira contenida en la propuesta comercial. Campos Requeridos:

- title
- products

[Ver todos campos disponibles](https://prolibu-docs.github.io/docs/#/reference-proposal)

#### Products
Información sobre productos contenidos en la propuesta comercial. Campos Requeridos:

- sku
- name
- price

[Ver todos campos disponibles](https://prolibu-docs.github.io/docs/#/reference-product)

#### Metadata
Sirve para suministrar información adicional propia del negocio que no cuenta con un campo estándar en Prolibu®. Por ejemplo:

- Información de Financiación
- Condiciones comerciales
- Imágenes
- Rénder 360
- Videos
- etc.

O cualquier otro dato que quiera presentar o almacenar dentro de la propuesta comercial en Prolibu®.

### Obtener un ApiKey de conexión

Las ApiKey son una forma de autenticación para que otras aplicaciones accedan mediante programación a los datos dentro de su cuenta Prolibu® de una manera simple y segura.

[Vea aquí el instructivo para generar un ApiKey dentro de su cuenta Prolibu®](https://github.com/prolibu-docs/docs/blob/main/api-key.md)

### Consumo ApiRest personalizados

Una vez implementado el CustomObject de Prolibu® dentro de su cuenta se entregará una URL con la documentación. En esa URL usted verá algo muy parecido a la imagen mostrada debajo, aquí se detallará la forma de conexión, autenticación, endpoints, paramentos y respuestas del nuevo objeto.

![Image Postman!](https://s3.amazonaws.com/files.nodriza.io/sales/Wilmar%20Ibarguen/Captura%20de%20pantalla%202021-11-10%20a%20la-s-%2010-57-20%20p-%20m-.png?=1636603319879)

### Suscribirse a eventos mediante Prolibu® Webhooks

Los webhooks le permiten crear o configurar integraciones, que se suscriben a ciertos eventos en Prolibu®. Cuando se activa uno de esos eventos, enviaremos una solicitud HTTP POST a la URL configurada en el webhook.

Para suscribirse a cualquier evento dentro de  Prolibu® necesita configurar en el módulo de Webhooks los siguientes datos:

#### Payload url
Es la URL del servidor que recibirá las solicitudes POST del webhook.

#### Authorization
Establecer una autorización de webhook le permite asegurarse de que las solicitudes POST enviadas a la URL sean de Prolibu®. Cuando establezca una autorización, recibirá el encabezado AUTORIZACIÓN en la solicitud POST del webhook.

#### Content type
Los webhooks se pueden entregar utilizando diferentes tipos de contenido:

- El tipo de contenido application/json entregará la carga útil JSON directamente como el cuerpo de la solicitud POST. 
- El tipo de contenido application/x-www-form-urlencoded enviará la carga útil JSON como un parámetro de formulario llamado carga útil.

#### Active
De forma predeterminada, las entregas de webhook están "activas". Puede optar por deshabilitar la entrega de cargas útiles de webhook de seleccionando "Activo".

#### Events

Los eventos son el núcleo de los webhooks. Estos webhooks se activan cada vez que se realiza una determinada acción en la plataforma nodriza, que la URL de carga útil de su servidor intercepta y sobre la que actúa.

[Vea aquí todos los eventos disponibles](https://prolibu-docs.github.io/docs/#/reference-webhook)

---------------
© 2021 PROLIBU TECH SAS, ALL RIGHTS RESERVED.
