### UANL
### FCFM, MCD

## Bases de datos relacionales

#### Tarea 1:

Las siguientes relaciones vienen de la base de datos *2008 Credit Sample Database* del sitio *"SQLSkills"*, en la cual con 9 tablas nos detallan los cargos que se le aplicaron a una empresa por ciertos proveedores, y el estado de los pagos a esos provedores. 

Las tablas son las siguientes:
- Category: describe por código, la categoría del producto (en tipos de dato numérico nominal y strings).
- Charge: tabla principal, contiene a través del tiempo los cargos que le aplicaron a la empresa, (contiene datos nominales, numéricos y dates).
- Corporation: tabla listando ciertas corporaciones, la cuál nos describe la corporación de los sujetos de la tabla member, (contiene datos nominales, strings y dates).
- Member 1 & 2: Al parecer son la misma tabla en 2 secciones, nos describen los sujetos que interactuaron con la empresa en la tabla Charge, las cuales se muestran en variables de date, numeros nominales, strings y numéricos.
- Payment: Muestra los pagos que hizo la empresa a cada sujeto de Member (datos nominales, numéricos y dates).
- Provider: Nos enseña las empresas proveedoras de la empresa principal -datos nominales, strings y dates-.
- Region: Las demás tablas cuentan con un region_no y en esta tabla estas las direcciones para cada region_no.
- Statement: Desplega el "statement amount" para cada miembro. Podría ser la cantidad pagada, se verá más a profundidad posteriormente -en datos nominales, numéricos y dates-.



Como detalle general de las bases, en varias tablas los datos de date todas las horas se repiten, o que algunas columnas que contienen códigos descriptivos estan vacías. Pero fuera de eso la base de datos podría mostrarnos resultados interesantes del ejercicio de esa empresa.




##### SQL Server:

Creado en la década de 1980 por Microsoft, SQL Server funciona para gestionar bases de datos relacionales, basado en un lenguaje de programación de consulta llamado Transact-SQL, en la el cual este sistema de gestión permite no solo almacenar información en un servidor, sino permite también la interacción cliente a servidor, donde el cliente puede generar consultas para acceder a cierta información. SQL Server solamente pudo funcionar en sistemas operativos de Windows, (Santamaría, J., & Hernández, J.; 2016), hasta hace poco que se añadió un soporte de Linux (Deyimar, A; 2018)

Así mismo, SQL Server fue construido siendo pensado como un sistema de gestión de bases de datos (SGBD) confiable y escalable. En la actualidad, es la principal plataforma SGBD para el software empresarial a gran escala. SQL Server se trabaja con aplicaciones .NET. De igual manera, SQL Server usa Management Studio como herramienta de entorno de desarrollo integrado (IDE). (Deyimar, A; 2018)






***Referencias:***

*Santamaría, J., & Hernández, J. (2016). Microsoft SQL Server. SQL SER vs MY SQL, 1-6.*

*(Deyimar, A; (2018, May 8). Diferencia entre MySQL y SQL Server. Tutoriales Hostinger. https://www.hostinger.mx/tutoriales/diferencia-mysql-sql-server*

*Sitio SQLSkills: https://www.sqlskills.com/sql-server-resources/sql-server-demos/*

