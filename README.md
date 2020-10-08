# Wordpress-aws-ha

# Don't forget to check the [wiki](https://github.com/Mateo-RH/wordpress-aws-ha/wiki)

Implementación **_High Availability_** de Wordpress en AWS

## Contexto

La universidad Eafit desea implementar Wordpress con el fin de que sus estudiantes puedan gestionar su material educativo. para esto se solicita realizar el despliegue de wordpress en un ambiente de nube con capacidad de 20.000 usuarios, tolerancia al fallo de 99% y almacenamiento de 500gb.
Adicionalmente debido a los programas de intercambio que ofrece la universidad, se solicita habilitar el sistema en 2 zonas de disponibilidad (Norte de Virginia y Ohio) con el fin de que el sistema pueda soportar un tráfico del 80% local y 20% extranjero.
Como el proyecto se tiene visionado para ser mantenido a largo plazo es necesario integrar un sistema de monitoreo para indexar la información y reportes del rendimiento del sistema, junto con un Pipeline de DevOps que testee y despliegue los nuevos cambios realizados en la aplicación.


## Requisitos funcionales

| Numeral | Descripción |
| --- | --- |
| 1 | Nombre de dominio para el sistema |
| 2 | Certificado SSL válido para el sistema |
| 3 | Sistema de cache CDN |
| 4 | Implementar Single Sign on (SSO), con Active Directory, LDAP, o auth0, gmail |
| 5 | Se debe implementar DevOps, para: Gestión de VM, Gestión de SO, Gestión de Aplicación, para la Instalación en Pruebas y Producción. |
| 6 | Sistema de backup y restore de datos, contenidos, aplicaciones, etc. |
| 7 | Sistema de monitoreo de Operación |
| 8 | Balanceadores de carga |

## Requisitos no funcionales

| QA | Descripción |
| --- | --- |
| Availability | Escalabilidad horizontal |
| Availability | Tolerancia de 2000 usuarios concurrentes |
| Performance | Tiempos de respuesta menor a 1 segundo |
| Security | Técnicas de autenticación de 2 factores |

## Diseño
![Disenio](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/Dise%C3%B1o/Wordpress.png) 

## Presupuesto (Mensual)

_Lo primero es saber que vamos a utilizar_

### Lista de Servicios:

1. Instancias **Amazon EC2**
2. Almacenamiento **Amazon S3**
3. Servicio web para el CDN **Amazon CloudFront**
4. Base de datos **Amazon RDS**
5. Balanceador de cargas **Amazon Elastic Load Balancing**
6. Servicio de Monitoreo **Amazon CloudWatch**
7. Dominio _(Gratis)_
8. Certificado _(Gratis)_

_Amazon Ofrece una calculadora para obtener la cotización de nuestros servicios_
https://calculator.s3.amazonaws.com/index.html?key=cloudformation/fb9db249-3391-4788-a32f-a40a84a86ce1#key=NONE

### Amazon EC2

* Vamos a utilizar 29 instancias **_Linux on t2.micro_** con volúmenes de 8gb cada una.
* Este servicio nos costaría **$246,50**  Mensuales 

![min](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/Anotaci%C3%B3n%202020-03-22%20142501.png)

* Esta es una opción alterna que podríamos utilizar para usar menos instancias, utilizar 12 instancias **_Linux on t2.medium_** con volúmenes de 8gb cada una.

![Medium](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/medium.png)

### Amazon S3

* Vamos a utilizar un almacenamiento estándar y calculamos el precio con los requisitos predeterminados.
* La transferencia de datos entrantes es gratuita y la transferencia de datos salientes es de 1 GB gratis por región al mes
* Este servicio nos costaría **$12.73** Mensuales

![s3](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/S3.png)

### Amazon CloudFront

* Al utilizar CloudFront para hacer de CDN necesitamos la Transferencia de datos de afuera y la transferencia de datos a origen.
* Este servicio nos costaría **$48,25** Mensuales 

![CloudFront](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/CloudFront.png)

### Amazon RDS

* Necesitaremos una base de datos MySQL de clase **_db.t2.micro_**  **_Multi-AZ_** con 500 GB de almacenamiento.
* Este servicio nos costaría **$233,21** Mensuales

![RDS](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/RDS.png)

### Amazon Elastic Load Balancing 

* De este servicio necesitaremos un Balanceador de cargas, con 500 GB/mensuales de procesamiento de datos.
* Este servicio nos costaría **$4,47** Mensuales 

 ![balanceador](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/balanceador.png)

### Amazon CloudWatch

* Usaremos un servicio de monitoreo para RDS, EC2, AutoScalingGroup, TargetGroup, ELB y S3. un total de 6 alarmas 
* EL tamaño de registros ingeridos, archivados y vendidos. Serán de 200GB cada uno
* Este servicio nos costaría **$209,5** Mensuales

![monitoreo](https://github.com/Mateo-RH/wordpress-aws-ha/blob/master/Imagenes/!0.Presupuesto/Monitoreo%20.png)


## Resumen
_con Instancias Micro_

* 29 Instancias Micro EC2 = **$246,50**  
* 1 S3 = **$12,73**
* CloudFront = **$48,25**
* 1 RDS = **$233,21**
* 1 ELB = **$4,47**
* 1 CloudWatch = **$209,5**
* 1 Dominio = **$0,0**
* 1 Certificado = **$0,0**

#### Total = **$655,10**                 

_con Instancias Medium_

* 12 Instancias Medium EC2 = **$407,64**
* 1 S3 = **$12,73**
* CloudFront = **$48,25**
* 1 RDS = **$233,21**
* 1 ELB = **$4,47**
* 1 CloudWatch = **$209,5**
* 1 Dominio = **$0,0**
* 1 Certificado = **$0,0**

#### Total = **$824,94**






