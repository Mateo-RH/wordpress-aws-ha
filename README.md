# Wordpress-aws-ha
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
