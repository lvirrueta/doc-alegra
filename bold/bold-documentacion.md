# Bold - Documentación <a id="index"></a>

- [Bold](#bold)
- [API - Integrations](#api-integrations)
- [API - Link de Pagos](#api-link-pagos)
- [API - Botón de Pagos](#api-boton-pagos)

## Bold
Bold es una empresa que ofrece soluciones de pago para negocios, permitiendo recibir pagos con tarjetas de manera fácil, rápida y segura. Su aplicación móvil, disponible en Google Play, facilita la gestión de transacciones mediante datáfonos móviles.

***

## API Integrations <a id="api-integrations"></a>
Api integrations ofrece la capacidad de integrar fácilmente la creación y gestión de pagos en tu plataforma existente. Con esta API, se podrán automatizar procesos, personalizar la experiencia de pago y aprovechar al máximo las capacidades de nuestra plataforma.

[Tarea - Asana](https://app.asana.com/0/1208399707757626/1208968353887281)

1. [Tipos de peticiones que se pueden realizar con la API de bold](#api-bold)
2. [Tiempo de respuesta y adecuación para Alegra](#tiempo-respuesta-alegra)
3. [Requerimientos técnicos para la integración](#requerimientos-tecnicos)
4. [Códigos de respuesta y de error](#codigos-respuesta)
5. [Tipo de API](#tipo-api)

<div style="text-align: right; font-size: 25px;">
  <a href="#index">&uarr;</a>
</div>

### Tipo de Peticiones API Bold<a id="api-bold"></a>
- **Consulta de métodos de pago disponibles:** Permite obtener informacion sobre los métodos de pago que el datáfono puede procesar.

- **Consulta de terminales de pago disponibles:** Facilita la obtención de una lista de los datáfonos asociados a la cuenta del comercio.

- **Creación de pagos mediante API** Permite iniciar transacciones de pago desde la aplicación del comercio, enviando instrucciones al datáfono para procesar pagos con tarjeta u otros medios.


### Tiempo de respuesta y adecuación para Alaegra<a id="tiempo-respuesta-alegra"></a>
La documentación no proporciona información sobre los tiempos de respuesta, dado que la API está diseñada para integraciones en tiempo real con datáfonos, se espera que los tiempo de respuesta sean adecuados


### Requerimientos técnicos para la integración<a id="requerimientos-tecnicos"></a>
- **Cuenta en Bold:** Es necesario tener una cuenta activa en **Bold**.
- **Datáfono SmartPro vinculado** Se requiere al menos un datáfono SmartPro asociado a la cuenta.
- **El datáfono debe estar encendido:** El datáfono debe estar encendido y con la aplicación abierta o en modo background.
- **Llave de identidad :** Se puede obtener desde el panel de integraciones de **Bold**.


### Códigos de respuesta y error<a id="codigos-respuesta"></a>
La respuesta es en tipo JSON, y los posibles errores: 
- **AP001** No se tiene mapeado el fallo a un error en particular.
- **AP002** El campo taxes del objeto amount no representa ninguna de las configuraciones posibles.
- **AP003** El método de pago enviado no se encuentra activo.
- **AP004** El datáfono seleccionado no se encuentra vinculado.
- **AP005** El cuerpo del body enviado no cuenta con todos los campos obligatorios, valida en la respuesta que campo te hace falta.  
- **AP006** Uno de los campos del body no cuenta con el tipo esperado según lo definido en esta documentación.

### Tipo de API<a id="tipo-api"></a>
La API de Bold es de tipo RESTful, utiliza métodos de HTTP estandar y en formato JSON

***

## API Link de Pagos <a id="api-link-pagos"></a>
API Link de pagos ofrece la capacidad de integrar fácilmente la creación y gestión de links de pago en tus aplicaciones y plataformas existentes. Con esta API, se podrán automatizar procesos, personalizar la experiencia de pago y aprovechar al máximo las capacidades de nuestra plataforma.

[Tarea - Asana](https://app.asana.com/0/1208399707757626/1208968353887279)

1. [Seguridad y Autenticación](#api-pagos-seguridad)
1. [Funcionalidades Principales](#api-pagos-funciones)
1. [¿Implica suscripción o pagos?](#api-pagos-suscripcion)
1. [¿Hay límite de solicitudes en la API?](#api-pagos-limite)
1. [Tipo de integración: API REST o SOAP](#api-pagos-rest)
1. [Tiempo de respuesta](#api-pagos-tiempo)
1. [Tipos de respuesta y errores](#api-pagos-tipo)

<div style="text-align: right; font-size: 25px;">
  <a href="#index">&uarr;</a>
</div>

### Seguridad y Autenticación<a id="api-pagos-seguridad"></a>
Las solicitudes a la API requieren una llave de identidad (x-api-key) que debe incluirse en las cabeceras de cada petición para garantizar la autenticidad y seguridad de las transacciones.

### Funcionalidades Principales<a id="api-pagos-funciones"></a>
**Url Base:** https://integrations.api.bold.co 

- [Consulta de métodos de pagos](#api-pagos-consulta)
- [Creación de enlace de pago](#api-pagos-creación)
- [Consulta estado y datos del enlace de pagos](#api-pagos-consulta-estado)

#### Consulta de métodos de pago<a id="api-pagos-consulta"></a>
- Endpoint: `GET`->`/online/link/v1/payment_methods`
- Descripción: Permite obtener los métodos de pago habilitados y sus límites de monto mínimo y máximo.

#### Creación de Enlace de Pago<a id="api-pagos-creación"></a>
- Endpoint: `POST`->`/online/link/v1`
- Descripción: Crea un link de pago que permite a los comercios generar links para que sus clientes puedan realizar pagos.
- Flujo de Trabajo: 
  - El comercio envía solicitud `POST` con los detalles de pago.
  - La API valida la solicitud y genera un enlace de pago único.
  - El comercio recibe el enlace para compartirlo con el cliente.

#### Consulta de enlace de pagos<a id="api-pagos-consulta-estado"></a>
- Endpoint: `GET`->`/online/link/v1/{payment_link}`
- Descripción: Permite a los usuarios consultar el estado y los datos asociados a un link de pago.
- Flujo de Trabajo: 
  - El comercio envía una solicitud `GET` con el identificador del enlace.
  - La API responde con los detalles actualizados del enlace, incluyendo su estado y otra información relevante.

### ¿Implica suscripción o pagos?<a id="api-pagos-suscripcion"></a>
No se mencionan un costo o suscripción

### ¿Hay límite de solicitudes en la API?<a id="api-pagos-limite"></a>
No se especifica un límite explicito de solicitudes.

### Tipo de integración: API REST o SOAP<a id="api-pagos-rest"></a>
La API utiliza un modelo REST y acepta solicitudes en formato JSON

### Tiempo de respuesta<a id="api-pagos-tiempo"></a>
La documentación no proporciona información sobre los tiempos de respuesta.

### Tipo de respuestas<a id="api-pagos-tipo"></a>
- La API proporciona respuestas en tipo JSON
- La API no proporciona los errores.

***

## API Botón de Pagos <a id="api-boton-pagos"></a>
El **Botón de Pagos** es una herramienta que permite integrar una solución de pago, redirigiendo a los clientes a la pasarela de pagos de Bold para completar transacciones de manera segura. 

[Tarea - Asana](https://app.asana.com/0/1208399707757626/1208968353887280)

1. [Formas de Integración](#api-boton-integracion)
1. [Tipo de integración: API REST o SOAP](#api-boton-rest)
1. [Tiempo de respuesta](#api-boton-tiempo)
1. [Respuestas o códigos de error](#api-boton-error)
1. [¿Implica suscripción o pagos?](#api-boton-sucripcion)
1. [¿Hay límite de solicitudes en la API?](#api-boton-limite)

<div style="text-align: right; font-size: 25px;">
  <a href="#index">&uarr;</a>
</div>

### Formas de Integración<a id="api-boton-integracion"></a>
- **Plugins:** Bold ofrece plugins para plataformas de comercio electrónico.
- **Integración Manual:** Para sitios web personalizados, es posible añadir el botón de pagos mediante código
  - Obtener las llaves de autenticación proporcionadas por Bold.
  - Generar un identificador único para cada venta.
  - Crear un hash de integridad para asegurar la transacción.
  - Configurar una URL de redirección post-pago.
  - Preparar los datos de la venta y añadir el botón en el sitio web.
  - Consultar el estado de una transacción después del pago.
- **Integración Personalizada del Botón de Pagos:** Si se prefiere adaptar el botón de pagos al diseño del sitio web del cliente
  - **Inicializar el Script de Bold:** Carga el script necesario en el encabezado.
  - **Crear una instancia de Venta:** Con el constructor BoldCheckout se especifica la transacción.
  - **Asignar Funcionalidad al Elemento Deseado:** Asociar la acción de apertura de la pasarela de pagos de Bold al elemento de la pagina.

### Tipo de integración: API REST o SOAP <a id="api-boton-rest"></a>
La API utiliza un modelo REST y acepta solicitudes en formato JSON

### Tiempo de respuesta<a id="api-boton-tiempo"></a>
La documentación no proporciona información sobre los tiempos de respuesta.

### Respuestas o códigos de error <a id="api-boton-error"></a>
- La API proporciona respuestas en tipo JSON
- La API no proporciona los errores.

### ¿Hay límite de solicitudes en la API? <a id="api-boton-limite"></a>
La documentación no menciona limites en las solicitudes de la API



