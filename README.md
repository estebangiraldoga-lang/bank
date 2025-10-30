# 💰 BankApp — Proyecto de Lógica y Solución de Problemas

Aplicación bancaria desarrollada en **Java 21** y **Spring Boot 3**, que simula las operaciones básicas de un banco: gestión de clientes, cuentas, depósitos, retiros y cálculo de intereses.  
Usa almacenamiento en **archivos JSON** (sin base de datos) y ofrece una **API REST documentada con Swagger**.

---

## 🧩 Estructura del proyecto

```bash
src/
├── main/java/com/logsoluprobl/appbank/
│   ├── AppbankApplication.java        # Punto de entrada principal
│   ├── config/OpenApiConfig.java      # Configuración de Swagger/OpenAPI
│   ├── controller/BankController.java # Controlador REST
│   ├── service/                       # Lógica del negocio
│   ├── repository/                    # Persistencia en JSON
│   ├── model/                         # Clases del dominio (Account, Customer, etc.)
│   ├── exception/                     # Excepciones personalizadas
│   └── util/                          # Utilidades generales
│
└── resources/
    ├── application.properties         # Configuración de Spring Boot
    └── data/                          # Archivos JSON con datos (clientes, cuentas)
🚀 Ejecución del proyecto
Clona el repositorio:

bash
Copiar código
git clone https://github.com/tu-usuario/logica-solucion-problemas-main.git
cd logica-solucion-problemas-main
Ejecuta el proyecto con Maven Wrapper:

bash
Copiar código
.\mvnw.cmd spring-boot:run
Abre tu navegador y accede a:

bash
Copiar código
http://localhost:8080/swagger-ui.html
Aquí podrás probar los endpoints de la API (crear clientes, abrir cuentas, hacer depósitos, etc.).

##⚙️ Tecnologías utilizadas
Tecnología	Descripción
Java 21	Lenguaje principal.
Spring Boot 3	Framework para desarrollo web.
Maven Wrapper	Gestión de dependencias y ejecución del proyecto.
Swagger / OpenAPI	Documentación interactiva de la API.
JSON	Formato para almacenamiento de datos.

##🧠 Descripción de las capas
Capa	Propósito
controller	Recibe las peticiones HTTP (API REST).
service	Contiene la lógica de negocio: operaciones bancarias, intereses, validaciones.
repository	Maneja la persistencia en archivos JSON.
model	Define las entidades: Cliente, Cuenta, Transacción, etc.
exception	Controla errores específicos del dominio.
config	Configura Swagger y parámetros de la aplicación.

##🏦 Clases principales
🔹 AppbankApplication.java
Punto de entrada principal del proyecto.
Ejecuta la aplicación y levanta el servidor embebido en el puerto 8080.

🔹 OpenApiConfig.java
Configura la documentación Swagger/OpenAPI.
Permite probar los endpoints desde el navegador con una interfaz amigable.

🔹 BankController.java
Controlador REST que gestiona las operaciones:

Crear clientes

Consultar cuentas

Realizar depósitos y retiros

Aplicar intereses

🔹 Account.java
Clase abstracta base para todas las cuentas.
Contiene atributos como:

id, owner, balance, transactions
Y métodos como:

deposit(), withdraw(), applyInterest()

🔹 CheckingAccount.java y SavingsAccount.java
Implementan el comportamiento específico de:

CheckingAccount → Cuentas corrientes

SavingsAccount → Cuentas de ahorro

🔹 BankService.java y BankServiceImpl.java
Implementan la lógica del negocio:

Validaciones

Creación de cuentas

Cálculo de intereses (usando el patrón Strategy)

🔹 JsonRepository.java
Permite guardar y leer datos desde archivos JSON locales (sin base de datos).

💡 Patrón de diseño usado: Strategy
El cálculo de intereses usa diferentes estrategias:

SimpleRateStrategy → Tasa fija.

TieredRateStrategy → Tasa por niveles.

Esto permite cambiar la forma de calcular intereses sin modificar las clases principales.

##⚠️ Manejo de errores
El proyecto define excepciones personalizadas en la clase DomainException.java para manejar errores del negocio, como:

Retiro mayor al saldo disponible.

Cuenta inexistente.

Cliente duplicado.

##📚 Endpoints principales (API REST)
Método	Endpoint	Descripción
POST	/api/bank/customers	Crear nuevo cliente
GET	/api/bank/customers	Listar todos los clientes
POST	/api/bank/accounts	Crear nueva cuenta
GET	/api/bank/accounts	Consultar todas las cuentas
POST	/api/bank/deposit	Realizar depósito
POST	/api/bank/withdraw	Realizar retiro
POST	/api/bank/apply-interest	Aplicar intereses a las cuentas
