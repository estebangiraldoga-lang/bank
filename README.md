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
```bash
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

Ejemplo de inclusión en README:

markdown
Copiar código
### Crear cliente
Fecha: `2025-10-30 12:51:22`  
![Crear cliente - Swagger](evidence/20251030_125122_swagger_create_customer.png)

Fecha: `2025-10-30 12:51:22`  
![Crear cliente - Postman](evidence/20251030_125122_postman_create_customer.png)

Respuesta (archivo): `evidence/20251030_125122_create_customer.json`
⚙️ Script para generar respuestas con timestamp
Incluido: test_endpoints.sh — ejecuta curl a endpoints y guarda .json en evidence/.

Uso:

bash
Copiar código
chmod +x test_endpoints.sh
./test_endpoints.sh
Los archivos generados tendrán nombres YYYYMMDD_HHMMSS_<endpoint>.json.

✅ Checklist de entrega
 Repositorio público en GitHub con código fuente

 README.md claro y con evidencias timestamped en evidence/

 postman_collection.json en la raíz del repo

 Swagger funcionando y documentado

 Todas las pruebas ejecutadas y capturadas (Swagger + Postman + JSON)


<img width="1366" height="768" alt="primera captura del codigo" src="https://github.com/user-attachments/assets/387b25a2-e908-4413-b532-80065c4ed2f8" />

## 📸 Evidencia del código

A continuación se muestra una captura del código fuente principal de la aplicación:
---

## 🧪 Evidencias de funcionamiento

A continuación se muestran las pruebas realizadas en **Swagger UI** y **Postman**, con fecha y hora registradas en cada ejecución.  
Cada evidencia valida el correcto funcionamiento de los endpoints principales del sistema bancario.

---

### 🧾 Crear nuevo cliente
📅 **Fecha:** 30/10/2025 — 🕓 **Hora:** 4:25 p. m.  
📍 **Endpoint:** `POST /api/bank/customers`  
📋 **Descripción:** Se crea un nuevo cliente con su identificador, nombre y correo electrónico.

**Resultado esperado:** Respuesta `201 Created` con los datos del cliente registrado.

![Evidencia — Crear cliente](evidence/obtener-la-lista-completa-de-clientes-registrados-en-el-sistema-bancario.png "Evidencia en Swagger UI — Creación de cliente")

---

### 💳 Obtener lista de clientes
📅 **Fecha:** (coloca la fecha/hora exacta de tu captura)  
📍 **Endpoint:** `GET /api/bank/customers`  
📋 **Descripción:** Muestra todos los clientes registrados en el sistema.

![Evidencia — Listar clientes](evidence/nombre-de-la-captura-listar-clientes.png "Evidencia en Swagger UI — Lista de clientes")

---

### 💰 Realizar depósito
📅 **Fecha:** (fecha/hora)  
📍 **Endpoint:** `POST /api/bank/deposit`  
📋 **Descripción:** Permite ingresar dinero a una cuenta existente.

![Evidencia — Depósito](evidence/nombre-de-la-captura-deposito.png "Evidencia en Swagger UI — Depósito exitoso")

---

### 🏦 Aplicar intereses
📅 **Fecha:** (fecha/hora)  
📍 **Endpoint:** `POST /api/bank/apply-interest`  
📋 **Descripción:** Aplica las tasas de interés según el tipo de cuenta (ahorros o corriente).

![Evidencia — Intereses](evidence/nombre-de-la-captura-intereses.png "Evidencia en Swagger UI — Aplicación de intereses")

---








