Introduction

NestMart is a Java web application built with Spring MVC and JSP/JSTL.
The project is packaged as a WAR, runs locally on GlassFish Server, and uses JDBC for database connectivity (MySQL/SQL Server).

It supports build and execution directly via IDE or Apache Ant.

Database connection configuration is provided through web.xml (JDBC sample config).

The application includes full e-commerce functionalities: account management, shopping cart, ordering, promotions, product management, reporting, etc.

Key Technologies

Language/Runtime: Java 8 (JRE/JDK 1.8)

Framework: Spring 4.3.x (Core, MVC, JDBC, Security)

View: JSP + JSTL

App server: GlassFish

Build: Apache Ant (build.xml) + PowerShell scripts

Packaging: WAR (dist/nestmartappFinal.war)

Database: SQL Server (driver mssql-jdbc-12.2.0.jre8.jar)

System Requirements

JDK 8

Apache Ant 1.10+

Git

GlassFish Server

Project Structure
├─ src/                 # Java source code, MANIFEST configuration
├─ web/                 # Web resources and JSP files
├─ lib/                 # Library JARs (Spring, JDBC, JSTL, etc.)
├─ build/               # Intermediate build directory (Ant)
├─ dist/                # WAR output (e.g. nestmartappFinal.war)
├─ nbproject/           # NetBeans/Ant project settings
├─ build.xml            # Ant build script
└─ web/WEB-INF/         # web.xml, dispatcher-servlet.xml, Spring configs

Configuration

web/WEB-INF/jdbc.properties or web/WEB-INF/application.properties

Edit DB connection parameters (URL, user, password, pool, etc.).

web/WEB-INF/applicationContext.xml, dispatcher-servlet.xml

Declare beans, datasource, view resolver, component scan, etc.

⚠️ Do not commit sensitive information. Use environment variables/secrets in CI/CD if necessary.

Running in NetBeans with GlassFish

Open the project in NetBeans (8.x/12.x).

Add GlassFish to NetBeans:

Tools → Servers → Add Server → GlassFish Server → Next

Choose GLASSFISH_HOME, domain domain1

Java Platform: select JDK 8

Set GlassFish as project server:

Right-click project → Properties → Run

Server: GlassFish Server

Context Path: <context-path> (e.g. /app)

Configure JDBC (if using SQL Server):

Copy lib/mssql-jdbc-12.2.0.jre8.jar into GLASSFISH_HOME\glassfish\domains\domain1\lib

Start GlassFish, open Admin Console http://localhost:4848

Create JDBC Connection Pool & JDBC Resource (if app uses JNDI)

Or make sure web/WEB-INF/jdbc.properties contains correct DB connection info

Run the application:

Right-click project → Run (or press F6)

NetBeans will build WAR and deploy it to GlassFish

Access: http://localhost:8080/<context-path>

Running on Public Server

The application is also deployed and can be accessed directly via:
👉 https://nestmart.publicvm.com/nestmartappFinal/client/orderHistory.htm

Troubleshooting

DB connection errors: check jdbc.properties and JDBC driver in lib/.

404/500 on access: check server logs and dispatcher-servlet.xml.

Build/Ant errors: ensure JDK 8 and Ant are in PATH.

Docker issues: verify environment variables, port conflicts, and file permissions.
