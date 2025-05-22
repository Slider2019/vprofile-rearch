# 🔐 Proyecto: VProfile AWS Refactor v2.0

![Bash](https://img.shields.io/badge/-Bash-4EAA25?logo=gnu-bash&logoColor=white)![SSH](https://img.shields.io/badge/-SSH-000000?logo=ssh)![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)![RabbitMQ Badge](https://img.shields.io/badge/RabbitMQ-F60?logo=rabbitmq&logoColor=fff&style=flat)![Apache Tomcat Badge](https://img.shields.io/badge/Apache%20Tomcat-F8DC75?logo=apachetomcat&logoColor=000&style=flat)![MySQL Badge](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=fff&style=flat)![GoDaddy Badge](https://img.shields.io/badge/GoDaddy-1BDBDB?logo=godaddy&logoColor=000&style=flat)![Apache Maven Badge](https://img.shields.io/badge/Apache%20Maven-C71A36?logo=apachemaven&logoColor=fff&style=flat)




## 📚 Descripción del Proyecto

Este proyecto consistió en **refactorizar completamente una arquitectura en AWS**, migrando de un enfoque tradicional basado en **IaaS (Infrastructure as a Service)**  a una solución moderna y optimizada utilizando **PaaS/SaaS (Platform/Software as a Service)**. Esta transformación tuvo como objetivo **reducir la complejidad operativa, mejorar la escalabilidad, facilitar el mantenimiento**  y optimizar los costos.

----------

## Índice

<!-- Tabla de contenidos -->
<details close>
    <summary>Tabla de Contenidos</summary>
    <ol>
        <ul>
            <li><a href="#objetivo-del-proyecto">Objetivo del proyecto</a></li>
            <li>
                <a href="#el-problema-del-enfoque-tradicional">2.- El Problema del Enfoque Tradicional</a>
                <ul>
                    <li><a href="#solución-pasar-de-iaas-a-paas-saas">Solución Pasar de IaaS a PaaS SaaS</a></li>
                    <li><a href="#servicios-que-se-usarán-en-aws">Servicios que se usarán en AWS</a></li>
                </ul>
            </li>
            <li><a href="#comparación-lift-y-shift-vs-refactorización">3.- Comparación Lift y Shift vs
                    Refactorización</a></li>
            <li><a href="#arquitectura-del-proyecto">4.- Arquitectura del proyecto</a></li>
            <li><a href="#flujo-de-ejecución-del-proyecto">5.- Flujo de Ejecución del Proyecto</a></li>
            <li>
                <a href="#inicio-de-la-construcción-del-proyecto">6.- Inicio de la construcción del Proyecto</a>
                <ul>
                    <li><a href="#configuración-de-seguridad-para-backend-en-aws-parte-de-arquitectura-beanstalk">Configuración
                            de Seguridad para Backend en AWS Parte de Arquitectura Beanstalk</a></li>
                    <li><a href="#arquitectura-general">Arquitectura General</a></li>
                    <li><a href="#servicios-backend-involucrados">Servicios Backend Involucrados</a></li>
                    <li><a href="#reglas-del-grupo-de-seguridad-del-backend">Reglas del Grupo de Seguridad del
                            Backend</a></li>
                    <li><a href="#pasos-en-la-consola-de-aws">Pasos en la Consola de AWS</a></li>
                    <li><a href="#crear-el-grupo-de-seguridad-backend">Crear el grupo de seguridad Backend</a></li>
                    <li><a href="#agregar-regla-de-entrada-interna">Agregar regla de entrada interna</a></li>
                    <li><a href="#crear-par-de-claves-pem">Crear Par de Claves PEM</a></li>
                </ul>
            </li>
            <li>
                <a href="#creación-de-una-base-de-datos-con-amazon-rds-para-el-proyecto">7.- Creación de una Base de
                    Datos con Amazon RDS para el Proyecto</a>
                <ul>
                    <li><a href="#por-qué-usar-rds">Por qué usar RDS</a></li>
                    <li><a href="#paso-1-buscar-y-acceder-a-amazon-rds">Paso 1 Buscar y acceder a Amazon RDS</a></li>
                    <li><a href="#paso-2-entendiendo-los-grupos-de-parámetros">Paso 2 Entendiendo los Grupos de
                            Parámetros</a></li>
                    <li><a href="#crear-un-grupo-de-parámetros">Crear un grupo de parámetros</a></li>
                    <li><a href="#paso-3-crear-un-db-subnet-group">Paso 3 Crear un DB Subnet Group</a></li>
                    <li><a href="#crear-un-grupo-de-subredes">Crear un grupo de subredes</a></li>
                    <li><a href="#paso-4-crear-la-instancia-de-base-de-datos">Paso 4 Crear la instancia de base de
                            datos</a></li>
                    <li><a href="#credenciales">Credenciales</a></li>
                    <li><a href="#configuración-de-instancia">Configuración de instancia</a></li>
                    <li><a href="#paso-5-configuración-de-conectividad">Paso 5 Configuración de conectividad</a></li>
                    <li><a href="#configuración-adicional">Configuración adicional</a></li>
                    <li><a href="#paso-final-crear-la-base-de-datos">Paso Final Crear la base de datos</a></li>
                </ul>
            </li>
            <li>
                <a href="#creación-de-elasticache-memcached-en-aws">8.- Creación de ElastiCache Memcached en AWS</a>
                <ul>
                    <li><a href="#acceso-al-servicio-elasticache">Acceso al servicio ElastiCache</a></li>
                    <li><a href="#creación-del-grupo-de-parámetros">Creación del Grupo de Parámetros</a></li>
                    <li><a href="#creación-del-grupo-de-subredes">Creación del Grupo de Subredes</a></li>
                    <li><a href="#creación-del-clúster-de-memcached">Creación del clúster de Memcached</a></li>
                    <li><a href="#configuración-del-clúster">Configuración del clúster</a></li>
                    <li><a href="#espera-y-prueba">Espera y prueba</a></li>
                </ul>
            </li>
            <li>
                <a href="#creación-de-amazon-mq-con-rabbitmq-en-aws">9.- Creación de Amazon MQ con RabbitMQ en AWS</a>
                <ul>
                    <li><a href="#qué-es-amazon-mq">Qué es Amazon MQ</a></li>
                    <li><a href="#requisitos">Requisitos</a></li>
                    <li><a href="#paso-a-paso-para-crear-un-broker-de-rabbitmq">Paso a Paso para Crear un Broker de
                            RabbitMQ</a></li>
                    <li><a href="#buscar-el-servicio">Buscar el servicio</a></li>
                    <li><a href="#seleccionamos-rabbitmq">Seleccionamos RabbitMQ</a></li>
                    <li><a href="#configuración-básica">Configuración básica</a></li>
                    <li><a href="#configuración-adicional">Configuración adicional</a></li>
                    <li><a href="#revisión-y-creación">Revisión y creación</a></li>
                </ul>
            </li>
            <li>
                <a href="#accediendo-y-configurando-rds-desde-una-ec2">10.- Accediendo y Configurando RDS desde una
                    EC2</a>
                <ul>
                    <li><a href="#inicialización-de-la-base-de-datos-rds">Inicialización de la Base de Datos RDS</a>
                    </li>
                    <li><a href="#estado-inicial">Estado inicial</a></li>
                    <li><a href="#crear-instancia-ec2-temporal">Crear instancia EC2 temporal</a></li>
                    <li><a href="#conexión-a-mysql-y-despliegue-del-esquema">Conexión a MySQL y despliegue del
                            esquema</a></li>
                    <li><a href="#obtener-datos-de-acceso-a-la-base-de-datos">Obtener datos de acceso a la base de
                            datos</a></li>
                    <li><a href="#conectar-a-mysql-desde-la-instancia">Conectar a MySQL desde la instancia</a></li>
                    <li><a href="#clonar-el-repositorio-del-proyecto">Clonar el repositorio del proyecto</a></li>
                    <li><a href="#ejecutar-el-script-sql">Ejecutar el script SQL</a></li>
                    <li><a href="#verificar">Verificar</a></li>
                    <li><a href="#limpieza">Limpieza</a></li>
                </ul>
            </li>
            <li>
                <a href="#beanstalk">11.- BeanStalk</a>
                <ul>
                    <li><a href="#configuración-de-elastic-beanstalk">Configuración de Elastic Beanstalk</a></li>
                    <li><a href="#creación-de-roles-iam-para-beanstalk">Creación de roles IAM para Beanstalk</a></li>
                    <li><a href="#pasos">Pasos</a></li>
                    <li><a href="#creación-del-entorno-beanstalk">Creación del entorno Beanstalk</a></li>
                    <li><a href="#configuración-personalizada">Configuración personalizada</a></li>
                    <li><a href="#configuración-de-instancias-y-escalado">Configuración de instancias y escalado</a>
                    </li>
                    <li><a href="#políticas-de-despliegue">Políticas de despliegue</a></li>
                    <li><a href="#notas-finales">Notas finales</a></li>
                </ul>
            </li>
            <li>
                <a href="#configuración-de-entorno-beanstalk-y-conexión-con-servicios-de-backend">
                    12.- Configuración de entorno Beanstalk y conexión con servicios de backend
                </a>
                <ul>
                    <li><a href="#pasos-para-conectar-el-entorno-beanstalk-con-los-servicios-de-backend">Pasos para
                            conectar el entorno Beanstalk con los servicios de backend</a></li>
                    <li><a href="#verificación-del-entorno-beanstalk">Verificación del entorno Beanstalk</a></li>
                    <li><a href="#verificación-de-los-servicios-backend">Verificación de los servicios backend</a></li>
                    <li><a href="#configuración-del-grupo-de-seguridad">Configuración del grupo de seguridad</a></li>
                    <li><a href="#guardar-cambios">Guardar cambios</a></li>
                    <li><a href="#resumen-y-preparación-para-el-siguiente-paso">Resumen y preparación para el siguiente
                            paso</a></li>
                </ul>
            </li>
            <li>
                <a href="#construcción-del-artefacto-y-configuración-del-backend">13.- Construcción del Artefacto y
                    Configuración del Backend</a>
                <ul>
                    <li><a href="#recolección-de-información-del-backend">Recolección de información del backend</a>
                    </li>
                    <li><a href="#tips">Tips</a></li>
                    <li><a href="#preparar-el-código-fuente">Preparar el código fuente</a></li>
                    <li><a href="#clonación-del-repositorio">Clonación del repositorio</a></li>
                    <li><a href="#actualización-del-archivo-application-properties">Actualización del archivo
                            application properties</a></li>
                    <li><a href="#construcción-del-artefacto-war">Construcción del artefacto WAR</a></li>
                    <li><a href="#verificar-versiones">Verificar versiones</a></li>
                    <li><a href="#compilar-proyecto">Compilar proyecto</a></li>
                    <li><a href="#despliegue-en-elastic-beanstalk">Despliegue en Elastic Beanstalk</a></li>
                    <li><a href="#subida-del-artefacto">Subida del artefacto</a></li>
                    <li><a href="#proceso-de-despliegue">Proceso de despliegue</a></li>
                    <li><a href="#habilitar-https-con-certificado-acm">Habilitar HTTPS con certificado ACM</a></li>
                    <li><a href="#agregar-listener-https-443">Agregar listener HTTPS 443</a></li>
                    <li><a href="#asociar-dominio-personalizado-godaddy-u-otro">Asociar dominio personalizado GoDaddy u
                            otro</a></li>
                    <li><a href="#en-godaddy">En GoDaddy</a></li>
                    <li><a href="#verificación-final">Verificación final</a></li>
                </ul>
            </li>
            <li>
                <a href="#aws-cloudfront-introducción-y-configuración">14.- AWS CloudFront Introducción y
                    Configuración</a>
                <ul>
                    <li><a href="#qué-es-aws-cloudfront">Qué es AWS CloudFront</a></li>
                    <li><a href="#por-qué-necesitamos-una-cdn">Por qué necesitamos una CDN</a></li>
                    <li><a href="#cómo-se-integra-cloudfront">Cómo se integra CloudFront</a></li>
                    <li><a href="#pasos-para-configurar-una-distribución-cloudfront">Pasos para configurar una
                            distribución CloudFront</a></li>
                    <li><a href="#actualizar-dns-en-godaddy">Actualizar DNS en GoDaddy</a></li>
                    <li><a href="#resultado-final">Resultado Final</a></li>
                </ul>
            </li>
            <li>
                <a href="#resumen-y-consideraciones-finales">15.- Resumen y consideraciones Finales</a>
                <ul>
                    <li><a href="#resumen-final-del-proyecto">Resumen Final del Proyecto</a></li>
                    <li><a href="#consideraciones-finales">Consideraciones Finales</a></li>
                    <li><a href="#desafios-enfrentados">Desafíos Enfrentados</a></li>
                    <li><a href="#lecciones-aprendidas">Lecciones Aprendidas</a></li>
                    <li><a href="#pros-y-contras-de-este-enfoque">Pros y Contras de este enfoque</a></li>
                    <li><a href="#próximos-pasos-para-la-evolución-del-proyecto">Próximos Pasos para la Evolución del
                            Proyecto</a></li>
                </ul>
            </li>
            <li><a href="#contacto">16.- Contacto</a></li>
        </ul>
    </ol>
</details>
<br>








---

## Objetivo del proyecto

Este proyecto es una evolución del anterior donde desplegué la aplicación **vProfile** tanto localmente como en la nube. En ese primer enfoque apliqué la estrategia **Lift & Shift** —es decir, mover mi stack tal como está, sin cambios, hacia AWS usando instancias EC2.

Ahora, en esta fase... **¡es hora de refactorizar!** Vamos a rediseñar los servicios usando una estrategia más avanzada:

> 🔄 Re-arquitectura / Refactorización:
> 
> Mejorar agilidad, facilitar el escalado, añadir nuevas funcionalidades más rápido, reducir costes y complejidad operativa.
<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

---

## 2.- El Problema del Enfoque Tradicional

Supongamos que tenemos muchos servicios (DB, App, Web, DNS, etc.) ejecutándose en:

-   🖥️ Máquinas físicas
-   🧳 Máquinas virtuales
-   ☁️ Instancias EC2

Para mantenerlos necesitamos:

-   Equipos de virtualización
-   Equipos de administración de centros de datos
-   Equipos de monitoreo
-   SysAdmins, etc.

⚠️ Resultado:

-   **Altos gastos operativos y de capital**
-   Procesos manuales difíciles de automatizar
-   Escalabilidad complicada

### Solución Pasar de IaaS a PaaS SaaS

En lugar de depender de **infraestructura como servicio (IaaS)** (por ejemplo, EC2), usaremos servicios administrados:

> ✅ Plataforma como Servicio (PaaS)
> 
> ✅ Software como Servicio (SaaS)

Beneficios:

-   Infraestructura como código 🧾
-   Elasticidad y escalabilidad integradas 📈
-   Pago por uso 💳
-   Automatización 🚀

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

----------

##  Servicios que se usarán en AWS

### 🌐 Frontend con **Elastic Beanstalk**

**AWS Elastic Beanstalk**  es un servicio **PaaS (Plataforma como Servicio)**  que nos permitirá  **implementar y administrar aplicaciones web fácilmente**  sin tener que preocuparnos por toda la infraestructura que hay debajo (como EC2, balanceadores, escalado, etc.).

Es como si pusiéramos nuestra aplicación en una **maceta mágica (Beanstalk)**  y Amazon se encargara de regarla, cuidarla, podarla y hasta escalarla si crece demasiado 🌿🚀.

#### Lo que hará por nosotros Elastic Beanstalk

Cuando subamos nuestro código, Elastic Beanstalk automáticamente:

1.  **Crea la infraestructura por nosotros**:
    
    -   Instancias EC2
    -   Balanceador de carga (si lo necesitamos)
    -   Auto Scaling
    -   Almacenamiento (EBS)
    -   Logs y monitoreo con CloudWatch
        
2.  **Al desplegar nuestra app**:
    
    -   Podemos usar **Java, Python, Node.js, .NET, PHP, Ruby, Go, Docker**, entre otros.
    -   Nosotros subimos nuestro código, y él lo pone a correr en un entorno preconfigurado.
        
3.  **Gestiona el ciclo de vida**:
    
    -   Escalado automático basado en la carga. 
    -   Deploys versionados (podemos hacer rollback si algo falla).
    -   Integración con Git, CodePipeline o desde la consola.
        
4.  **Monitoreará nuestra aplicación**:
    
    -   Logs disponibles.
    -   Integración con CloudWatch para alertas.
    -   Vistas de salud (verde, amarillo, rojo 🟢🟡🔴).

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

##  Backend:

### 📊 **RDS**

#### ¿Qué hará?

Proveerá una **base de datos MySQL completamente gestionada**, donde no nos preocuparemos por:

-   Instalar, configurar ni mantener MySQL.
-   Hacer respaldos automáticos.
-   Escalar verticalmente (cambiar el tipo de instancia) o usar réplicas de lectura para escalar horizontalmente.
    

🔧 **Para nuestro proyecto**:  

Será ideal porque necesitaremos **persistencia de datos**  para nuestra aplicación (usuarios, productos, pedidos, logs, etc.). Además, al estar en RDS, podremos **automatizar backups, failover y monitoreo**, lo cual es clave en una arquitectura moderna DevOps.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### 🧠 ElastiCache (como reemplazo de Memcached)

#### ¿Qué hará?

Nos dará una **capa de caché en memoria**, lo que significa:

-   Respuestas **ultrarrápidas**  a consultas frecuentes (por ejemplo, sesiones de usuario, listas de productos populares).
    
-   Reducción de carga en la base de datos.
    

🔧 **Para nuestro proyecto**:  

Nos servirá para **mejorar el rendimiento**  y la **escalabilidad**  de nuestra aplicación. En vez de consultar siempre MySQL, podremos almacenar los resultados comunes en ElastiCache y acelerar tiempos de respuesta en nuestra página.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### 📬 Amazon MQ (como reemplazo de RabbitMQ)

#### ¿Qué hará?

Proporcionará un **servicio de mensajería confiable**, donde los componentes de nuestro sistema podrán comunicarse de forma **asíncrona**  usando colas y topics:

-   Produce y consume mensajes (por ejemplo, para órdenes, notificaciones, tareas en background).
    
-   Compatible con AMQP (el protocolo de RabbitMQ).
    

🔧 **Para nuestro proyecto**:  

Nos permitirá **desacoplar servicios**, por ejemplo, cuando un microservicio genere un evento que otro microservicio procesa. Amazon MQ maneja **reintentos, almacenamiento de mensajes y entrega garantizada**, sin que nosotros tengamos que configurar RabbitMQ a mano.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### 🌐 Route 53 – DNS gestionado

#### ¿Qué hará?

Se encargará de traducir los **nombres de dominio (como [www.tuproyecto.com](http://www.tuproyecto.com))**  a direcciones IP de nuestros recursos (EC2, Beanstalk, ALB, etc.), pero con esteroides:

-   Alta disponibilidad y baja latencia.
-   Routing geográfico, failover, balanceo DNS, etc.
-   Integración con otros servicios de AWS.
    

🔧 **Para nuestro proyecto**:  

Será nuestro **administrador de nombres**  para que nuestra aplicación esté disponible desde internet con un dominio profesional, más opciones de **resiliencia y tráfico inteligente**.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### 🚀 CloudFront – CDN (Content Delivery Network)

#### ¿Qué hará?

Distribuirá el **contenido estático y dinámico** de nuestra web (como imágenes, JS, CSS, videos, o incluso páginas web) desde **servidores distribuidos globalmente**, con:

-   Bajos tiempos de carga.
-   Protección contra DDoS (con AWS Shield).
-   Compresión y caching inteligente.
    

🔧 **Para nuestro proyecto**:  

Será perfecto para acelerar la carga de nuestro frontend, mejorar la experiencia de usuario y **optimizar tráfico global**. Ideal si nuestra app tiene clientes en distintas regiones del mundo.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

----------

## 3.- Comparación Lift y Shift vs Refactorización

| Componente Tradicional (Lift & Shift) | Refactorizado en AWS     |
|--------------------------------------|---------------------------|
| EC2 + Tomcat manual                  | Elastic Beanstalk         |
| Memcached en EC2                    | ElastiCache               |
| RabbitMQ en EC2                     | Amazon MQ                 |
| MySQL en EC2                        | Amazon RDS                |
| NFS                                 | EFS o S3                  |
| DNS propio                          | Route 53                  |
| CDN externo/manual                  | CloudFront                |


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

## 4.- Arquitectura del Proyecto

1.  🌐 Usuario accede a la **URL**
2.  🌍 Se resuelve vía **Route 53**
3.  🚀 Redirige a **CloudFront**
4.  🔄 CloudFront responde con contenido cacheado
5.  🧭 Redirige al **Application Load Balancer** (parte de Beanstalk)
6.  🏗️ El ALB enruta hacia una **EC2 en Auto Scaling Group** (Aquí corre **Tomcat**)
7.  📦 Los artefactos se almacenan en **S3**
8.  🔁 Backend accedido por:
    -   **Amazon MQ**
    -   **ElastiCache**
    -   **Amazon RDS**
9.  🧠 **CloudWatch** gestiona alertas y escalado

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

## 5.- Flujo de Ejecución del Proyecto

1.  Iniciar sesión en AWS Console
2.  Crear par de claves para EC2 de Beanstalk 🔐
3.  Crear **Security Group** para el backend:
    -   ElastiCache
    -   RDS
    -   Amazon MQ
4.  Crear:
    -   📊 RDS
    -   🧠 ElastiCache
    -   📨 Amazon MQ
5.  Crear entorno de **Elastic Beanstalk**
6.  Actualizar **Security Groups**:
    -   Permitir tráfico de Beanstalk al Backend
    -   Permitir tráfico interno entre servicios Backend
7.  Lanzar instancia EC2 temporal para inicializar la DB con `mysql -h <endpoint RDS>`
8.  Ajustar Health Check de Beanstalk a `/login`
9.  Agregar listener HTTPS (puerto 443) al Load Balancer
10.  Construir artefacto con:
    -   RDS endpoint
    -   ElastiCache endpoint
    -   MQ endpoint
11.  Deploy en Beanstalk
12.  Configurar **CloudFront** con SSL
13.  Actualizar DNS:
    -   Via Route 53
    -   O GoDaddy (según convenga)
14.  🎉 ¡Probar en la URL final!

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

---

## 6.- Inicio de la construcción del Proyecto

### 1.- Configuración de Seguridad para Backend en AWS Parte de Arquitectura Beanstalk

----------

###  Arquitectura General

-   Usaremos **Elastic Beanstalk** para desplegar nuestra aplicación.
-   Elastic Beanstalk creará:
    -   Instancias **EC2** para alojar la app.
    -   Un **grupo de seguridad para la instancia EC2**.
    -   Un **grupo de seguridad para el Load Balancer (ELB)**.
    -   Una **regla automática** para permitir tráfico entre el grupo del ELB y el grupo de la aplicación.

----------

###  Servicios Backend Involucrados

Tendremos varios servicios en el backend:

-   **Amazon MQ** 🐰
-   **Amazon RDS** 💾
-   **Amazon ElastiCache** 🧠

🛡 Para estos servicios crearemos un **grupo de seguridad común**, llamado `Backend Security Group`.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

###  Reglas del Grupo de Seguridad del Backend

-   **Crear primero el grupo sin reglas**.
-   Luego, editar las **reglas de entrada** con:
    -   Tipo: `All Traffic` 🚦
    -   Origen: el **propio ID del grupo de seguridad** (para permitir comunicación interna entre servicios).
-   Esto permite que MQ, RDS y ElastiCache se comuniquen entre ellos libremente.

📝 Más adelante, cuando se cree el grupo de seguridad de **Elastic Beanstalk**, actualizaremos este grupo de backend para permitir tráfico del mismo.

----------

###  Pasos en la Consola de AWS

###  Crear el grupo de seguridad Backend

1.  Ir a **EC2 > Security Groups**.
    
2.  Seleccionar **Create Security Group**.
    
3.  Asignar un nombre descriptivo, por ejemplo:
    
    ```
    vprofile-rearch-backend-sg
    
    
    ```
    
    _(para identificar que es parte del proyecto de Re-arquitectura)_
    
4.  No agregar reglas de entrada aún.
    
5.  Confirmar que las **reglas de salida** estén por defecto (permiten todo).
    
6.  Crear el grupo.
    

###  Agregar regla de entrada interna

1.  Una vez creado, editar reglas de entrada:
    -   Tipo: **All Traffic**
    -   Fuente: **ID del mismo grupo de seguridad**
    -   Descripción: “Permitir tráfico interno entre servicios backend”

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

###  Crear Par de Claves PEM

Este paso es **opcional**, pero útil si necesitamos acceder a la instancia EC2 para depurar problemas.

1.  Ir a **EC2 > Key Pairs**.
2.  Crear nueva clave:
    -   Nombre: `vprofile-rearch-key`
    -   Tipo: `.pem` (para acceso desde Linux/macOS)

⚠️ **Nota**: Beanstalk maneja todo por defecto, pero si se requiere acceso manual para debugging, la clave será útil.

----------

## 7.- Creación de una Base de Datos con Amazon RDS para el Proyecto


###  Por qué usar RDS

Necesitamos una base de datos para nuestra aplicación de perfiles, y usaremos Amazon RDS por sus ventajas en administración, escalabilidad y seguridad. En este proyecto trabajaremos con **MySQL 8.0**.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Paso 1 Buscar y acceder a Amazon RDS

1.  Primero que todo debemos asegurarnos de estar en la **misma región** de AWS.
2.  Busca **RDS** en el buscador del panel de AWS.
3.  En el dashboard de RDS, dirígete a **"Databases" > "Create database"**.

----------

### Paso 2 Entendiendo los Grupos de Parámetros

📌 En RDS **no podemos hacer login SSH** como en EC2 para modificar directamente archivos de configuración.

✅ Para eso existe el concepto de **grupo de parámetros**:

Permite personalizar configuraciones como `max_connections`, `query_cache_size`, etc.

###  Crear un grupo de parámetros

1.  En el menú lateral de RDS, seleccionamos **"Parameter groups"**.
2.  Click en **"Create parameter group"**.
3.  Configuramos:
    -   **Group type**: `DB Parameter Group`
    -   **Engine**: `MySQL Community`
    -   **Parameter group family**: `mysql8.0`
    -   **Group name**: `rds-rearch-vprofile-grp`
    -   **Description**: (repetimos el nombre)
4.  Click en **Create**.


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

----------

### Paso 3 Crear un DB Subnet Group

📌 Un **DB Subnet Group** es un conjunto de subredes dentro de una VPC. RDS necesita estar en al menos dos zonas de disponibilidad para tolerancia a fallos.

### Crear un grupo de subredes

1.  Ir a **"Subnet groups"** en RDS.
2.  Click en **"Create DB subnet group"**.
3.  Configuramos:
    -   **Name**: `rds-rearch-subnet-group`
    -   **Description**: Igual que el nombre
    -   **VPC**: Usaremos la predeterminada (a menos que tengamos una personalizada)
    -   **Availability zones & subnets**: Seleccionamos todas las subredes disponibles
4.  Click en **Create**.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Paso 4 Crear la instancia de base de datos

1.  Vamos a **"Databases" > "Create database"**
2.  Seleccionamos:
    -   **Creation method**: `Standard Create`
    -   **Engine**: `MySQL`
    -   **Version**: `8.0.x` 
    -   **Template**: `Free tier` ✅

### Credenciales:

-   **DB instance identifier**: `nombre de la instancia`
-   **Master username**: `aquí tu contraseña`
-   **Autogenerar contraseña** ✅ (Recuerda copiarla y guardarla)

### Configuración de instancia

-   **DB instance class**: `db.t4g.micro` o `db.t3.micro` (depende de la región)
-   **Storage**:
    -   **Type**: `gp3 (General Purpose SSD)`
    -   **Allocated storage**: `20 GB`
    -   ❌ Desactivar el escalado automático de almacenamiento

No queremos escalado automático, ya que éste será un proyecto de prueba, pero en condiciones reales, hay que activarlo.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Paso 5 Configuración de conectividad

-   **VPC**: predeterminada
-   **Subnet group**: seleccionar el grupo creado: `rds-rearch-subnet-group`
-   **Public access**: `No` ❌ (uso interno)
-   **VPC security group**: usar grupo de seguridad creado para backend
-   **Availability Zone**: `No preference`

----------

### Configuración adicional

-   **Database port**: `3306` (por defecto de MySQL)
-   **Authentication**: `Password authentication`
-   ❌ Desactivar enhanced monitoring y CloudWatch (para mantener el free tier. En condiciones reales, ésto se debe activar)
-   **Initial database name**: `nombre de la DB` 
-   **Backup**: puede mantenerse activo si se desea
-   **Encryption**: dejar como está
-   **Log exports**: activarlo si deseamos enviar logs a CloudWatch (opcional)
-   **Auto minor version upgrade**: opcional según el proyecto
-   **Maintenance**: dejar sin definir

### Paso final Crear la base de datos

-   Click en **"Create database"**.
-   AWS comenzará el aprovisionamiento de la instancia RDS.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---


## 8.- Creación de ElastiCache Memcached en AWS


### 1. Acceso al servicio ElastiCache

-   Vamos a la **Consola de AWS**.
-   Buscamos **“ElastiCache”** o también puedes escribir **“memcache”** en el buscador.
-   Seleccionamos el servicio **ElastiCache**.

----------

### 2. Creación del Grupo de Parámetros

> Similar a como se hace en RDS.

1.  Ir a **Parameter Groups**.
2.  Hacer clic en **Create Parameter Group**.
3.  Completar:
    -   **Parameter group family:** `memcached`
    -   **Group name:** `vprofile-cache`
    -   **Description:** Algo descriptivo como `Custom param group for Memcached`.
    -   **Engine version:** `memcached 1.6` (última versión estable).
4.  Hacer clic en **Create**.

> ⚠️ Nota: Los parámetros avanzados no se configuraron en éste proyecto

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### 3. Creación del Grupo de Subredes

1.  Vamos a **Subnet Groups**.
2.  Clic en **Create Subnet Group**.
3.  Completar:
    -   **Name** y **Description** del grupo.
    -   Seleccionar la **VPC por defecto**.
    -   Todas las subredes disponibles aparecerán seleccionadas automáticamente.
4.  Hacer clic en **Create**.

----------

### 4. Creación del clúster de Memcached

1.  Ir al **Dashboard de ElastiCache**.
2.  Clic en **Create Cache**.
3.  Selecciona el motor **Memcached**.
4.  Elegir el método de creación:
    -   Selecciona **Standard create** para ver todas las opciones.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------
### 5. Configuración del clúster

Completamos los siguientes campos:

| Opción                    | Valor                                                                 |
|--------------------------|-----------------------------------------------------------------------|
| **Name**                 | `vprofile-cache`                                                      |
| **Engine**               | `Memcached`                                                          |
| **Version**              | `1.6.x` (Ej: `1.6.22`, `1.6.17`, etc.)                                |
| **Port**                 | `11211` (¡Importante! Asegúrate de que coincida con tu app)          |
| **Parameter group**      | El que creamos: `vprofile-cache`                                 |
| **Node type**            | `cache.t2.micro` (mínimo costo: 0.5 GB RAM)                          |
| **Number of nodes**      | `1`                                                                  |
| **Subnet group**         | El grupo que creamos antes                                           |
| **Availability Zone**    | Sin preferencia                                                      |
| **Security Group**       | Seleccionamos el grupo adecuado: `backend-sg`                      |
| **Maintenance**          | Default                                                              |
| **Notifications (SNS)**  | Puedes dejarlo en desactivado si no usas SNS                         |

> ✅ Verifica bien:
> 
> -   Tipo de nodo (ej. `t2.micro` o `t3.micro`)
> -   Versión del engine `1.6`
> -   Puerto `11211`
> -   Grupo de seguridad correcto , luego Clic en **Create**.

----------

### 6. Esperamos y probamos

-   La creación tomará unos minutos.
-   Al finalizar, tendremos disponible el **endpoint** para conectarnos desde nuestra aplicación.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

## 9.- Creación de Amazon MQ con RabbitMQ en AWS

#### Qué es Amazon MQ

Es un servicio administrado de **brokers de mensajería** que soporta **RabbitMQ y Apache ActiveMQ**. Permite evitar la gestión manual de nuestras instancias EC2.

----------

#### Requisitos

-   Usar **RabbitMQ** como broker.
-   Usar la opción más **económica** (una sola instancia).
-   No se usará VPC personalizada (se utilizará la **VPC por defecto**).
-   Tener un grupo de seguridad (El cual reutilizaremos).

----------

### Paso a Paso para Crear un Broker de RabbitMQ

#### 1. Buscar el servicio

-   En la consola de AWS, escribimos `RabbitMQ` o `Amazon MQ`.
-   Entramos al servicio **Amazon MQ**.

#### 2. Seleccionamos RabbitMQ

-   Clic en **"Create broker"**.
-   Tipo de broker: **RabbitMQ**.
-   Tipo de implementación: **Single-instance broker** (más económico).
-   Siguiente.

#### 3. Configuración básica

-   **Nombre**: `vprofile-rearch-rabbitmq`
-   **Tipo de instancia**: `mq.t3.micro` (el más pequeño)
-   **Nombre de usuario**: `tu nombre de usuario`
-   **Contraseña**: 12 caracteres (guardar para archivo de configuración)

#### 4. Configuración adicional

-   **Versión del motor**: Usar la predeterminada (ej. `3.13`)
-   **Logging**: No habilitar CloudWatch logs
-   **Tipo de acceso**: `Private access` (porque se accede desde dentro de la VPC)
-   **VPC y subred**: Usar **VPC por defecto**
-   **Grupo de seguridad**: Seleccionar el grupo creado anteriormente (ej. `backend-sg`)
-   **Cifrado y mantenimiento**: Usar valores por defecto


#### 5. Revisión y creación

-   Revisar que todos los valores estén correctos:
    -   Instancia `mq.t3.micro`
    -   RabbitMQ
    -   Acceso privado
    -   Grupo de seguridad correcto
-   Clic en **"Create broker"**

🕐 **Esto tardará algunos minutos en aprovisionarse.**

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

## 10.- Accediendo y Configurando RDS desde una EC2

### Inicialización de la Base de Datos RDS

#### Estado inicial

-   RDS disponible ✅
-   Puerto: `3306`
-   Instancia es **privada**, sin acceso público.

### Crear instancia EC2 temporal

> Propósito: accesar a RDS y ejecutar el script SQL para inicializar la BD.

1.  **Lanzar instancia EC2**
    -   SO: `Ubuntu Server 24`
    -   Tipo: `t2.micro`
    -   Nombre: `cliente-mysql`
    -   Par de llaves: usar uno existente o crear uno nuevo.
2.  **Grupo de seguridad para EC2**
    
    -   Nombre: `cliente-wipro-mysql-sg`
    -   Regla: permitir puerto `22 (SSH)` desde `mi IP`.

3.  **Conexión por SSH**
    
    ```bash
    ssh -i /ruta/a/tu/llave.pem ubuntu@<IP-pública>
    
    
    ```
    
4.  **Preparar el entorno**
    
    ```bash
    sudo -i
    apt update && apt install mysql-client git -y
    
    
    ```
    
5.  **Permitir acceso entre grupos de seguridad**
    
    -   Añadir una regla de entrada en el SG de RDS:
        -   Tipo: `MySQL/Aurora (3306)`
        -   Fuente: SG del cliente EC2 (`cliente-wipro-mysql-sg`)

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Conexión a MySQL y despliegue del esquema

#### Obtener datos de acceso a la base de datos

-   Endpoint de RDS
-   Usuario: `nombre de usuario`
-   Contraseña: (guardada previamente)

#### Conectar a MySQL desde la instancia

```bash
mysql -h <endpoint> -u admin -p


```

> ⚠️ No poner nunca la contraseña directamente en la línea de comandos por seguridad.

### Clonar el repositorio del proyecto

```bash
git clone <https://github.com/Slider2019/vprofile-rearch.git>
cd vprofile-rearch
git checkout main


```

### Ejecutar el script SQL

```bash
mysql -h <endpoint> -u admin -p accounts < src/main/resources/db_backup.sql


```

### Verificar

```sql
SHOW TABLES;


```

----------

### Limpieza

-   El propósito de la instancia EC2 fue **inicializar la BD**.
-   Ya no es necesaria, por lo que procedemos a **terminarla desde la consola**.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

## 11.- BeanStalk


### Configuración de Elastic Beanstalk

-   Recordar proyecto anterior:
    -   Configuración de Tomcat en EC2
    -   Creación de par de claves, grupo de seguridad, balanceador de carga, plantilla AMI, grupo de autoescalado
-   Beanstalk ofrece todo en un solo servicio:
    -   Auto Scaling Group, AMI, S3 para artefactos, CloudWatch, etc.
    -   Sin costos adicionales (solo pagamos por recursos usados como EC2)

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

---

### Creación de roles IAM para Beanstalk


### Pasos

1.  Ir a **IAM → Roles → Crear rol**
2.  Seleccionar **Servicio AWS → EC2**
3.  Adjuntar políticas:
    -   `Acceso de administrador AWS Elastic Beanstalk`
    -   `Plataforma de roles personalizados AWS Elastic Beanstalk`
    -   `SNS de roles de AWS Elastic Beanstalk`
    -   `Notificaciones de la capa web AWS Elastic Beanstalk`
4.  Nombrar el rol (ej: `Rearch-bean`)

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Creación del entorno Beanstalk

#### 🚀 Pasos iniciales:

-   Ir a **Elastic Beanstalk → Crear aplicación**
-   **Plataforma**: Tomcat + Corretto 21 (Java 21)
-   **Nombre de aplicación y entorno**: Únicos y verificados
-   **URL personalizada**: Asegurar disponibilidad

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Configuración personalizada

🔧 Detalles clave:

-   **VPC**:
    -   Seleccionar VPC por defecto
    -   Habilitar IP pública
    -   Subredes disponibles
-   **Seguridad**:
    -   Grupo de seguridad creado por Beanstalk (editable después)
    -   Volumen raíz: **GP3** (evitar errores de configuración obsoleta)

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---


### Configuración de instancias y escalado

 Opciones:

-   **Capacidad**:
    -   Mínimo: 2 instancias
    -   Máximo: Definir según necesidades
    -   Tipo de instancia: **t2.micro**
-   **Balanceador de carga**:
    -   Tipo: **Aplicación** (HTTP/HTTPS)
    -   Listener en puerto 80
    -   Habilitar **Stickinness** (sticky sessions)


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Políticas de despliegue

🎯 Estrategias recomendadas:

1.  **Rolling**: Actualizar instancias en lotes (ej: 50% = 1 instancia a la vez).
2.  **Inmutable**: Crear nuevas instancias antes de eliminar las antiguas (más seguro pero costoso).
3.  **División de tráfico**: Pruebas canarias (ej: 10% del tráfico a nueva versión).


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---


### Notas finales

-   **Variables de entorno**: Configurar según necesidades (ej: conexión a BD).
-   **Revisar configuración**: Verificar roles, seguridad, escalado y VPC antes de lanzar.
-   **Despliegue**: En los próximos pasos (subida de artefacto y pruebas).


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---


## 12.- Configuración de entorno Beanstalk y conexión con servicios de backend

**Objetivo:** Establecer conexión entre Elastic Beanstalk y los servicios de backend, como RDS y Amazon MQ, asegurando las reglas de seguridad adecuadas.

----------

### Pasos para conectar el entorno Beanstalk con los servicios de backend


#### 1. Verificación del entorno Beanstalk

-   **Aplicación por defecto:**
    -   Al hacer clic en la URL proporcionada, debería ver la aplicación por defecto alojada en Beanstalk.
-   **Próximos pasos:**
    -   En la próxima clase, se cambiará la aplicación por la correspondiente a nuestro perfil.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

#### 2. Verificación de los servicios backend

-   **Servicios backend ya configurados:**
    -   RDS
    -   Amazon MQ
    -   Memcache
-   **Conexión de Beanstalk con backend:**
    -   El entorno Beanstalk necesita conectarse a estos servicios de backend.
    -   **Grupo de seguridad backend:** Verificar que la regla de seguridad del backend permita la conexión desde Beanstalk.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

#### 3. Configuración del grupo de seguridad

-   **Verificar grupo de seguridad de Beanstalk:**
    -   Seleccionar las instancias de Beanstalk desde el panel de instancias.
    -   Identificar el **grupo de seguridad de la instancia** (no el de balanceador de carga).
-   **Obtener el ID del grupo de seguridad:**
    -   Hacer clic en el grupo de seguridad para obtener el **ID del grupo de seguridad de la instancia**.
    -   Nos aseguramos de que no sea el ID del grupo de seguridad del balanceador de carga.
-   **Configuración del grupo de seguridad backend:**
    -   Acceder al grupo de seguridad del backend.
    -   Asegurarse de que está habilitado el tráfico permitido desde el grupo de seguridad de Beanstalk.
-   **Añadir regla al grupo de seguridad del backend:**
    -   Seleccionar **Reglas de entrada**.
    -   **Añadir regla:** Permitir todo el tráfico desde el grupo de seguridad de Beanstalk (instancia de Beanstalk).
    -   Descripción: Especificar que la regla permite el tráfico de Beanstalk a backend.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

#### 4. Guardar cambios

-   **Guardar reglas:**
	-   Después de añadir la regla, hacer clic en **Guardar reglas**.
-   **Obtener datos del servicio backend:**
    -   Acceder a todos los servicios de backend y obtener:
        -   Endpoint del backend
        -   Número de puerto
        -   Nombre de usuario
        -   Contraseña
-   Guardar estos datos en un archivo, ya que serán necesarios en los próximos pasos para construir y desplegar el artefacto en el entorno Beanstalk.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

#### Resumen y preparación para el siguiente paso

-   **Reglas de seguridad:** Asegúrate de que el grupo de seguridad de backend permita tráfico desde las instancias de Beanstalk.
-   **Datos necesarios:** Recopila los endpoints y credenciales de los servicios de backend para el despliegue futuro en Beanstalk.


<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------



## 13.- Construcción del Artefacto y Configuración del Backend

Pasos para construir y desplegar un artefacto Java (WAR) en **AWS Elastic Beanstalk**, integrando varios servicios backend (RDS, Amazon MQ, ElastiCache) y asegurando conectividad segura mediante HTTPS.

---

### Recolección de información del backend

1.  **RDS** (MySQL):
    -   Guarda el **endpoint**, **usuario (`nombre usuario`)** y **contraseña**.
2.  **Amazon MQ (RabbitMQ)**:
    -   Copia la URL después del `/`, cambia el puerto a `5671`.
    -   Usuario: `nombre de usuario`, contraseña definida durante la creación.
3.  **ElastiCache (Memcached)**:
    -   Copia el endpoint de configuración.
    -   Asegúrate que el puerto es `11211`.

### Tips

-   Usa notas adhesivas para almacenar temporalmente los datos sensibles.
-   Verifica todos los endpoints y puertos cuidadosamente en el archivo `application.properties`.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Preparar el código fuente

#### Clonación del repositorio

1.  Ve a `https://github.com/Slider2019/vprofile-rearch`.
    
2.  Clona el repositorio:
    
    ```bash
    git clone <https://github.com/Slider2019/vprofile-rearch.git>
    
    
    ```
    
3.  Abre en **Visual Studio Code**.
    
4.  verificar que la rama esté en `main`.
    

### Actualización del archivo application properties

Ubicado en `src/main/resources/application.properties`:

-   Cambia:
    
    ```
    spring.datasource.url=jdbc:mysql://<endpoint-RDS>:3306/<nombre_db>
    spring.datasource.username=[nombre de usuario]
    spring.datasource.password=[contraseña]
    spring.rabbitmq.host=[endpoint de RabbitMQ]
    spring.rabbitmq.port=5671
    spring.rabbitmq.username=[nombre de usuario]
    spring.rabbitmq.password=[contraseña]
    spring.cache.type=memcached
    memcached.servers=<endpoint-ElastiCache>:11211
    
    
    ```
    

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Construcción del artefacto WAR

#### Verificar versiones

```bash
mvn -version


```

-   Maven: `3.9.9`
-   Java: `17+`

> ⚠️ Si no coinciden, desinstala e instala usando:

-   Windows: `choco uninstall` y `choco install`
-   Mac: `brew uninstall` y `brew install`

### Compilar proyecto

```bash
mvn install


```

Resultado: Se crea un archivo WAR en la carpeta `/target`, por ejemplo:

`vprofile-rearch.war`

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>



----------

### Despliegue en Elastic Beanstalk

#### Subida del artefacto

1.  Ve a tu entorno de Elastic Beanstalk.
2.  Haz clic en **Upload and Deploy**.
3.  Selecciona el archivo WAR.
4.  Asigna un nombre de versión (ej: `vprofile-rearch-vapp-1.9`).
5.  Política de despliegue: Rolling, 50% batch size.
6.  Haz clic en **Deploy**.

#### Proceso de despliegue

-   Verifica en la pestaña de **Eventos**.
-   Elastic Beanstalk actualizará las instancias de a una (rolling deployment).
-   Ve al **target group** en EC2 → salud de instancias cambia a medida que se despliegan.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>



----------

### Habilitar HTTPS con certificado ACM

#### Agregar listener HTTPS 443

1.  Ir a **Configuration** → Load balancer.
2.  Editar configuración del listener.
3.  Añadir protocolo `HTTPS` y puerto `443`.
4.  Seleccionar un certificado ACM (previamente creado).
5.  Guardar y aplicar los cambios.

> Esto puede tomar varios minutos y modificará el load balancer.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Asociar dominio personalizado GoDaddy u otro

#### En GoDaddy

1.  Copia la URL del entorno Elastic Beanstalk.
2.  Ve a tu dominio en GoDaddy.
3.  Gestiona el DNS.
4.  Añade registros CNAME apuntando a la URL del entorno para habilitar HTTPS.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>



----------

### Verificación final

1.  Abre la URL en navegador (ahora con HTTPS).
2.  Inicia sesión con las credenciales de prueba:
    -   Usuario: `admin_vp`
    -   Contraseña: `admin_vp`
3.  Comprueba el funcionamiento correcto de la app y conectividad con los servicios backend.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------


## 14.- AWS CloudFront Introducción y Configuración


### Qué es AWS CloudFront

CloudFront es el servicio de **Content Delivery Network (CDN)** de AWS.

Su propósito es **distribuir contenido globalmente con baja latencia y alta velocidad** de transferencia.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Por qué necesitamos una CDN

✅ Nuestro sitio está alojado en **Virginia del Norte (EE.UU.)**

❌ Usuarios de otras regiones (Asia, Europa, África) acceden más lentamente.

⚠️ Crear servidores en cada región es costoso y complejo.

🟢 **Solución**: Usar una CDN → **CloudFront**

> 🔁 CloudFront tiene más de 600 ubicaciones de borde que cachean el contenido y lo sirven desde la ubicación más cercana al usuario.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Cómo se integra CloudFront

1.  Actualmente, la URL apunta al **Load Balancer** de Elastic Beanstalk.
2.  Vamos a **crear una distribución de CloudFront** que apunte a ese Load Balancer.
3.  Actualizamos la entrada DNS en GoDaddy para que apunte a CloudFront.

----------

### Pasos para configurar una distribución CloudFront

1.  **Ir al servicio CloudFront** en la consola de AWS.
2.  Crear una nueva **distribución**:
    -   **Origen**: seleccionar el Load Balancer de Beanstalk.
        -   Verifica en EC2 que es el correcto.
    -   **Protocolo**: "Match Viewer" (se adapta a HTTP o HTTPS según el cliente).
    -   **Nombre del origen**: se puede dejar por defecto.
    -   **Métodos HTTP permitidos**: `GET`, `HEAD`, `POST`, `PUT`, `PATCH`, `DELETE`
    -   **Política de caché**: usar configuración heredada (`Legacy Cache Settings`)
        -   Encabezados: todos
        -   Cadenas de consulta: todas
        -   Cookies: todas
3.  **WAF (Web Application Firewall)**:
    -   Opción avanzada (no gratuita).
    -   ⚠️ No activar por ahora.
    -   🛡️ Recomendado para producción: protege contra amenazas comunes.
4.  **Región de distribución**:
    -   Usar **“All Edge Locations”** para mejor rendimiento.
5.  **Nombre de dominio alternativo (CNAME)**:
    -   Ejemplo: `vprorearch.midominio.com`
    -   Requiere un **certificado SSL en ACM** que coincida con el dominio.
6.  **Política de seguridad**: mantener la predeterminada.
7.  **Crear distribución**

> ⏳ Puede tardar 10 minutos en desplegarse.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


----------

### Actualizar DNS en GoDaddy

1.  Ir al panel de DNS.
2.  Crear nuevo registro tipo **CNAME**:
    -   **Nombre**: mismo que el dominio alternativo (`vprorearch.midominio.xyz`)
    -   **Valor**: dominio de la distribución de CloudFront (sin `https://`)
3.  Guardar los cambios.

> 🕐 Tarda unos minutos en estar disponible.

----------

### Resultado Final

🔄 CloudFront ahora entrega el contenido desde **Edge Locations globales**,
ofreciendo alta disponibilidad, baja latencia y mejor experiencia al usuario 🌍🚀

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>



----------


## 15.- Resumen y consideraciones Finales


### Resumen Final del Proyecto

Este proyecto consistió en la re-arquitectura completa de una aplicación monolítica desplegada en una instancia EC2 hacia una arquitectura moderna y escalable utilizando servicios gestionados de AWS.

Durante el proceso, se aplicaron conceptos clave como:

• Configuración de grupos de seguridad personalizados  
• Gestión de claves SSH  
• Registro de dominios y creación de registros DNS en Route 53  
• Configuración de mecanismos de _stickiness_ en el Application Load Balancer  
• Uso de Amazon CloudFront como CDN para mejorar la latencia  
• Integración de Amazon MQ, ElasticCache y Amazon RDS para sustituir servicios auto-gestionados

El flujo de despliegue también incluyó prácticas de monitoreo básico a través de Amazon CloudWatch y el uso de AWS Elastic Beanstalk para el manejo del ciclo de vida de la aplicación.

Finalizado el proyecto, se llevó a cabo una **limpieza controlada** del entorno para evitar costos innecesarios, eliminando recursos temporales como instancias EC2, bases de datos, cachés, brokers, buckets, y registros DNS.

Este ejercicio representa una excelente práctica de migración cloud-native con foco DevOps.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Consideraciones Finales

#### Desafíos Enfrentados

• Comprensión y configuración detallada de servicios distribuidos de AWS  
• Tiempo de espera prolongado para la eliminación completa de algunos recursos (CloudFront, Beanstalk)  
• Configuración precisa de las reglas de seguridad y puertos de comunicación  
• Coordinación entre servicios interdependientes (DB, Cache, MQ, App)  
• Gestión de la caché del navegador durante pruebas de validación con CloudFront

Estos retos permitieron consolidar una visión más profunda sobre cómo se interconectan los servicios en la nube y cómo planificar una arquitectura resiliente desde el inicio.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

#### Lecciones Aprendidas

✅ Importancia del orden y la nomenclatura clara al trabajar con múltiples servicios en AWS  
✅ El monitoreo constante y las alarmas automatizadas son claves para mantener entornos sanos  
✅ La automatización de despliegue y la limpieza de recursos son tan importantes como el desarrollo en sí  
✅ Entender el flujo de red (desde DNS hasta instancia) es crucial para diagnosticar problemas  
✅ Practicar la documentación durante el desarrollo facilita futuras iteraciones y colaboraciones

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Pros y Contras de este enfoque

✔️ **Pros**:

• Alta disponibilidad y escalabilidad aseguradas con Elastic Load Balancer y Auto Scaling  
• Reducción de carga en la aplicación gracias a CDN (CloudFront) y caching (ElasticCache)  
• Simplificación operativa con servicios gestionados (RDS, MQ)  
• Mejora del rendimiento global mediante edge locations

❌ **Contras**:

• Dependencia total del ecosistema AWS  
• Curva de aprendizaje considerable en configuración inicial  
• Gestión manual de algunos recursos al no usar IAC (Infrastructure as Code)  
• Costos potenciales si no se configura correctamente la infraestructura

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---

### Próximos Pasos para la Evolución del Proyecto

Para seguir desarrollando y profesionalizando este proyecto, se tomará en consideración la implementación de herramientas clave del ecosistema DevOps:

🔧 **Jenkins**  
Integración continua (CI) y entrega continua (CD) para automatizar el proceso de construcción, pruebas y despliegue de la aplicación.

🛠 **Ansible**  
Automatización de la configuración y despliegue de servicios en servidores o contenedores, eliminando tareas repetitivas y asegurando consistencia.

📦 **Terraform**  
Gestión de infraestructura como código (IaC), permitiendo reproducibilidad, control de versiones y despliegues más seguros en AWS.

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>


---


## 🙌 **Si, has llegado hasta aquí, ¡Gracias por leer!. 
### Si te interesa ver el código o probarlo, clona el repo y comienza tu propia aventura y si tienes alguna consulta o duda, enviame un mensaje privado por linkedin

<p align="right">(<a href="#índice">Volver al inicio</a>)</p>

---

## 16.- Contacto

Enlace a Linkedin 
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-0077B5?logo=linkedin)](https://www.linkedin.com/in/diegorojasv/)<br>
💬 💡**TIP**:  Haz clic con el botón derecho o Ctrl+clic para abrir en una pestaña nueva y no salir de GitHub 😉
