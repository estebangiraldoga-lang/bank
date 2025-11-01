# 💰 BankApp — Proyecto de Lógica y Solución de Problemas

**Resumen**  
Aplicación bancaria desarrollada en **Java 21** y **Spring Boot 3** que simula operaciones bancarias: gestión de clientes, cuentas, depósitos, retiros y cálculo de intereses.  
El proyecto usa **archivos JSON** para persistencia (sin BD) y expone una **API REST** documentada con **Swagger**.

---

## 🧩 Estructura del proyecto

src/
├── main/java/com/logsoluprobl/appbank/
│ ├── AppbankApplication.java # Punto de entrada principal
│ ├── config/OpenApiConfig.java # Configuración de Swagger/OpenAPI
│ ├── controller/BankController.java # Controlador REST
│ ├── service/ # Lógica del negocio
│ ├── repository/ # Persistencia en JSON
│ ├── model/ # Clases del dominio (Account, Customer, etc.)
│ ├── exception/ # Excepciones personalizadas
│ └── util/ # Utilidades generales
└── resources/
├── application.properties # Configuración de Spring Boot
└── data/ # Archivos JSON con datos (clientes, cuentas)

yaml
Copiar código

---

## 🚀 Ejecución del proyecto (local)

1. Clona el repositorio:
``bash
git clone https://github.com/tu-usuario/logica-solucion-problemas-main.git
cd logica-solucion-problemas-main
Ejecuta con Maven Wrapper:

Windows PowerShell:

powershell
Copiar código
.\mvnw.cmd spring-boot:run
Linux / macOS:

bash
Copiar código
./mvnw spring-boot:run
Abre Swagger UI (documentación interactiva):

bash
Copiar código
http://localhost:8080/swagger-ui.html
Si no carga, prueba http://localhost:8080/swagger-ui/index.html o revisa OpenApiConfig.java y application.properties.

⚙️ Tecnologías utilizadas
Tecnología	Descripción
Java 21	Lenguaje principal
Spring Boot 3	Framework para desarrollo web
Maven Wrapper	Gestión de dependencias y ejecución
Swagger / OpenAPI	Documentación interactiva de la API
JSON	Formato para persistencia de datos

🧠 Capas y responsabilidades
Capa	Propósito
controller	Recibe peticiones HTTP (API REST)
service	Lógica de negocio: validaciones, operaciones
repository	Persistencia en archivos JSON
model	Entidades: Customer, Account, Transaction
exception	Excepciones de dominio
config	Configuraciones (Swagger, etc.)

🏦 Clases principales (resumen)
AppbankApplication.java — Punto de entrada (arranca Spring Boot).

OpenApiConfig.java — Configura Swagger/OpenAPI.

BankController.java — Endpoints REST (crear cliente, crear cuenta, depositar, retirar, aplicar intereses).

Account.java — Clase abstracta base; métodos: deposit(), withdraw(), applyInterest().

CheckingAccount, SavingsAccount — Implementaciones concretas.

BankService / BankServiceImpl — Lógica del negocio (usa patrón Strategy para calcular intereses).

JsonRepository — Guarda/lee datos en JSON (sin BD).

💡 Patrón de diseño
Strategy — El cálculo de intereses admite distintas estrategias:

SimpleRateStrategy → tasa fija

TieredRateStrategy → tasa por niveles

⚠️ Manejo de errores
Se usan excepciones personalizadas (DomainException.java) para controlar casos como:

Retiro mayor al saldo disponible

Cuenta inexistente

Cliente duplicado

📚 Endpoints principales (API REST)
Método	Endpoint	Descripción
POST	/api/bank/customers	Crear nuevo cliente
GET	/api/bank/customers	Listar clientes
POST	/api/bank/accounts	Crear nueva cuenta
GET	/api/bank/accounts	Listar cuentas
POST	/api/bank/deposit	Realizar depósito
POST	/api/bank/withdraw	Realizar retiro
POST	/api/bank/apply-interest	Aplicar intereses

Ejemplo de petición (Crear cliente)
http
Copiar código
POST /api/bank/customers
Content-Type: application/json

{
  "id": "c1",
  "name": "Juan Perez",
  "email": "juan.perez@example.com"
}
Ejemplo de respuesta
json
Copiar código
{
  "status": "success",
  "data": {
    "id": "c1",
    "name": "Juan Perez",
    "email": "juan.perez@example.com"
  }
}
🧪 Postman (pruebas)
Archivo incluido: postman_collection.json (importar en Postman → File → Import).

La collection usa la variable {{baseUrl}} con valor por defecto:

bash
Copiar código
http://localhost:8080/api/bank
Ejecuta cada request y guarda las respuestas o usa el Runner para correr la colección.

🖼️ Evidencias (requerimiento obligatorio)
Debes incluir capturas de Swagger y Postman para cada endpoint.
Convención obligatoria de nombres (para garantizar unicidad y mostrar fecha/hora):

makefile
Copiar código
YYYYMMDD_HHMMSS_endpoint_descripcion.png
ejemplo: 20251030_125122_swagger_create_customer.png
Qué subir a evidence/ (mínimo por endpoint):

Captura desde Swagger UI (PNG).

Captura desde Postman (PNG).

Archivo JSON con la respuesta (.json) — generado por test_endpoints.sh o exportado desde Postman.

INTERES
![imagencap1](./aplicar%20intereses%20a%20una%20cuenta%20bancaria%20específic.png)
![consultar el historial de transacciones de una cuenta bancaria específica](./consultar%20el%20historial%20de%20transacciones%20de%20una%20cuenta%20bancaria%20específica.png)

CONSULTAS DATOS DE UN CLIENTE
![consultar los datos de un cliente específico](./consultar%20los%20datos%20de%20un%20cliente%20específico.png)

CONSULTAS DETALLES DE CUENTAS
![consultar los detalles de una cuenta bancaria específic](./consultar%20los%20detalles%20de%20una%20cuenta%20bancaria%20específic.png)

CREACIÓN DE CUENTA BANCARIA
![crear una nueva cuenta bancaria asociada a un cliente específic](./crear%20una%20nueva%20cuenta%20bancaria%20asociada%20a%20un%20cliente%20específic.png)
![crear una nueva cuenta bancaria asociada a un cliente específico](./crear%20una%20nueva%20cuenta%20bancaria%20asociada%20a%20un%20cliente%20específico.png)

LISTA DE CLIENTES EN EL SISTEMA
![obtener la lista completa de clientes registrados en el sistema bancario](./obtener%20la%20lista%20completa%20de%20clientes%20registrados%20en%20el%20sistema%20bancario.png)

DEPOSITO
![realizar un depósito de dinero en una cuenta bancaria específic](./realizar%20un%20depósito%20de%20dinero%20en%20una%20cuenta%20bancaria%20específic.png)
![realizar un depósito de dinero en una cuenta bancaria específica](./realizar%20un%20depósito%20de%20dinero%20en%20una%20cuenta%20bancaria%20específica.png)

TRANFERENCIA
![realizar una transferencia de dinero desde una cuenta origen hacia una cuenta destin](./realizar%20una%20transferencia%20de%20dinero%20desde%20una%20cuenta%20origen%20hacia%20una%20cuenta%20destin.png)
![realizar una transferencia de dinero desde una cuenta origen hacia una cuenta destino](./realizar%20una%20transferencia%20de%20dinero%20desde%20una%20cuenta%20origen%20hacia%20una%20cuenta%20destino.png)

REGISTRO DE CLIENTE
![registrar un nuevo cliente en el sistema bancari](./registrar%20un%20nuevo%20cliente%20en%20el%20sistema%20bancari.png)
![registrar un nuevo cliente en el sistema bancario](./registrar%20un%20nuevo%20cliente%20en%20el%20sistema%20bancario.png)

REGISTRO DE DINERO
![retirar dinero de una cuenta bancaria específic](./retirar%20dinero%20de%20una%20cuenta%20bancaria%20específic.png)
![retirar dinero de una cuenta bancaria específica](./retirar%20dinero%20de%20una%20cuenta%20bancaria%20específica.png)









