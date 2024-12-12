# AWS

- [Servicios Principales](#servicios-principales-aws)
- [Seguridad](#seguridad)
- [Monitoreo](#monitoring)

## Servicios Principales AWS
[Servicios Principales - AWS - Video](https://www.youtube.com/watch?v=B08iQQhXG1Y)

### Host Web Application
- Quieres hacer hosting de tu aplicación web, **Contenido Estático** proporcionado por **AWS S3** (almacenamiento seguro, escalable y de alta disponibilidad).
- Mejorar el performance y reducir la latencia mediante una red de distribución de contenido: **AWS CloudFront**.
- Registrar y administrar dominios fácilmente con **AWS Route 53**, que incluye capacidades de DNS y balanceo de carga geográfico.

### API Hosting
- Ejecuta código sin necesidad de un servidor: **AWS Lambda** (serverless).
- Configura puntos de entrada para invocar Lambda u otros servicios: **AWS API Gateway**.
- Lanza y administra servidores virtuales en la nube: **AWS EC2**.
- Distribuye tráfico entre varias instancias de forma eficiente con **AWS Application Load Balancer**.
- Hostea imágenes de contenedores y orquesta su ejecución: **AWS ECS** (Elastic Container Service).

### Database
- Servicio administrado de bases de datos relacionales: **AWS RDS** (MySQL, PostgreSQL, etc.).
- Base de datos relacional serverless y altamente escalable: **AWS Aurora**.
- Analítica de datos a gran escala y almacenamiento optimizado para BI: **AWS Redshift**.
- Base de datos NoSQL serverless para alta velocidad y escalabilidad: **AWS DynamoDB**.
- Solución de caching en memoria para acelerar aplicaciones: **AWS ElastiCache** (Memcached/Redis).

### Comunicación
- Servicio de notificaciones push y mensajes distribuidos: **AWS SNS** (Simple Notification Service).
- Servicio de colas de mensajes para desacoplar sistemas: **AWS SQS** (Simple Queue Service).
- Orquestación y automatización de flujos de trabajo: **AWS Step Functions**.

### Analytics, Big Data y ML
- Ejecuta consultas SQL directamente sobre datos en S3: **AWS Athena**.
- Herramienta de BI para análisis de datos: **AWS QuickSight**.
- Procesamiento de big data con Apache Spark y Hadoop: **AWS EMR** (Elastic MapReduce).
- Plataforma para desarrollar, entrenar e implementar modelos de Machine Learning: **AWS SageMaker**.

### Seguridad
- Define redes virtuales privadas en AWS: **AWS VPC** (Virtual Private Cloud).
- Gestiona identidades, roles y permisos: **AWS IAM** (Identity and Access Management).

### Seguridad
- [AWS VPC](#aws-vpc)
- [AWS IAM](#aws-iam)

#### AWS VPC
**Amazon VPC (Virtual Private Cloud)** te permite definir una red virtual aislada dentro de la infraestructura de AWS. Con VPC puedes:
- Controlar el rango de direcciones IP (CIDR block) de tu red.
- Configurar subredes privadas y públicas.
- Establecer gateways de Internet y NAT para comunicación entre tu red y el exterior.
- Crear reglas de seguridad con **Security Groups** y **Network ACLs** para controlar tráfico entrante y saliente.
- Conectar tu red on-premises con AWS mediante **VPN** o **AWS Direct Connect**.

VPC es esencial para aplicaciones que necesitan aislamiento, mayor seguridad, y control avanzado sobre el tráfico de red.

#### AWS IAM
**IAM (Identity and Access Management)** es el servicio de AWS que te ayuda a administrar de forma segura el acceso a los recursos de tu cuenta. Con IAM puedes:
- Crear **usuarios**, **grupos**, y **roles** con permisos específicos.
- Usar **políticas (policies)** para definir qué acciones puede realizar un usuario o recurso sobre un servicio.

##### Conceptos clave de IAM:
- **Policy**: Documento en formato JSON que define permisos. Ejemplo:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "CreateFunction",
      "Effect": "Allow",
      "Action": [
        "lambda:CreateFunction"
      ],
      "Resource": "*"
    }
  ]
}
```

Ej. El siguiente ejemplo de política permite a un usuario leer columnas específicas de una tabla en DynamoDB:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadOnlyAccess",
      "Effect": "Allow",
      "Action": [
        "dynamodb:BatchGet*",
        "dynamodb:GetItem",
        "dynamodb:Query",
        "dynamodb:Scan"
      ],
      "Resource": "arn:aws:dynamodb:*:*:table/MyTable",
      "Condition": {
        "ForAllValues:StringEquals": {
          "dynamodb:Attributes": [
            "column-name-1",
            "column-name-2",
            "column-name-3"
          ]
        },
        "StringEqualsIfExists": {
          "dynamodb:Select": "SPECIFIC_ATTRIBUTES"
        }
      }
    }
  ]
}
```

##### Access Key & Secret Access Key: 
- Credenciales que permiten interactuar con AWS a través del SDK o CLI. Estas deben manejarse con cuidado para evitar fugas de seguridad.

##### Otros Concepto Importantes:
- **Grupos**: Permiten asociar políticas a un conjunto de usuarios para facilitar la gestión.
- **Roles**: Similares a los grupos, pero diseñados para ser asumidos por usuarios o servicios por un tiempo limitado. Se usan comúnmente para recursos como instancias EC2 que necesitan permisos temporales.
- **Trust Relationships**: Permiten a un recurso o entidad en una cuenta A acceder a recursos en una cuenta B mediante un rol de confianza.

##### Buenas Practicas:
- Proteger el **Root Account**: No usar esta cuenta para tareas diarias. En su lugar, crear usuarios IAM con los permisos necesarios.
- Usar el **Policy Simulator**: Herramienta útil para probar y validar políticas antes de aplicarlas.
- Habilitar **MFA (Multi-Factor Authentication)** en todas las cuentas críticas.
- Aplicar el principio de **mínimos privilegios**: Otorgar solo los permisos estrictamente necesarios.


### Monitoring
- Monitorea métricas de recursos en tiempo real: **AWS CloudWatch**.
- Rastrea eventos y cambios en tu cuenta AWS: **AWS CloudTrail**.
