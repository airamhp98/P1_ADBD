# MODELO ENTIDAD/RELACIÓN. FARMACIA
- Airam Herrera Plasencia
- Enrique Hernández Cabrera
## Descripción de las entidades definidas
Entidades Definidas:
### Cliente
Atributos:
- **NIF:** Número de identificación fiscal del cliente.
  - Dominio: Cadena alfanumérica con un formato específico, como 12345678X.
  - Ejemplo: 98765432A
- **Nombre:** Nombre del cliente.
  - Dominio: Cadena de texto alfabética. No puede estar vacía.
  - Ejemplo: Juan Pérez
- **Crédito:** Estado del crédito del cliente (con o sin crédito). 
  - Dominio: Valores limitados, {Con Crédito, Sin Crédito}.
  - Ejemplo: Con Crédito
- **D. Bancarios:** Información sobre cuentas bancarias del cliente.
  - Dominio: Cadena numérica con el formato de cuenta bancaria o IBAN.
  - Ejemplo: ES7600810001200001234567
- **F. Pago:** Forma de pago usada por el cliente (crédito, etc.).
  - Dominio: Valores predefinidos {Tarjeta, Transferencia, Efectivo, Crédito}.
  - Ejemplo: Tarjeta
### Farmacia
Atributos:
- **ID:** Identificador de la farmacia.
  - Dominio: Cadena alfanumérica única que identifica a cada farmacia.
  - Ejemplo: FAR-1001
- **Nombre:** Nombre de la farmacia.
  - Dominio: Cadena de texto no vacía que representa el nombre de la farmacia.
  - Ejemplo: Farmacia El Sol
- **Dirección:** Ubicación de la farmacia.
  - Dominio: Cadena de texto que contiene dirección física.
  - Ejemplo: Calle Mayor, 123, Madrid
- **Teléfono:** Número de contacto de la farmacia.
  - Dominio: Número de teléfono en formato nacional o internacional.
  - Ejemplo: +34 915123456
### Medicamento
Atributos:
- **Familia:** Categoría del medicamento.
  - Dominio: Categorías predefinidas de medicamentos, {Antiinflamatorios, Analgésicos, etc.}.
  - Ejemplo: Antiinflamatorios
- **Código:** Código de identificación del medicamento.
  - Dominio: Cadena alfanumérica que identifica al medicamento, único en el sistema.
  - Ejemplo: MED-12345
- **Nombre:** Nombre del medicamento.
  - Dominio: Cadena de texto que indica el nombre comercial del medicamento.
  - Ejemplo: Ibuprofeno 600mg
- **Tipo:** Tipología de medicamento.
  - Dominio: Categorías de presentación del medicamento, {Tableta, Cápsula, Jarabe, Inyección}.
  - Ejemplo: Tableta
- **Precio:** Precio del medicamento.
  - Dominio: Número decimal positivo que indica el precio en euros.
  - Ejemplo: 9.99 EUR
- **Unidades:** Cantidad de unidades disponibles o vendidas.
  - Dominio: Número entero positivo que indica la cantidad de unidades disponibles o vendidas.
  - Ejemplo: 100 unidades
- **Fecha de compra:** Cuándo se realizó la compra del medicamento.
  - Dominio: Cadena del tipo date que representa una fecha válida
  - Ejemplo: 07/10/2024
- **Forma de venta:** Forma de venta del medicamento.
  - Dominio: Cadena de caracteres que representa cómo se vendió el medicamento.
  - Ejemplo: Efectivo
### Laboratorio
Atributos:
- **Código:** Código de identificación del laboratorio.
  - Dominio: Cadena alfanumérica que identifica de manera única al laboratorio.
  - Ejemplo: LAB-789
- **Nombre:** Nombre del laboratorio.
  - Dominio: Cadena de texto no vacía que representa el nombre del laboratorio.
  - Ejemplo: Laboratorios Genéricos S.A.
- **Teléfono:** Número de contacto del laboratorio.
  - Dominio: Número de teléfono en formato nacional o internacional.
  - Ejemplo: +34 916543210
- **Dirección:** Dirección del laboratorio.
  - Dominio: Cadena de texto que contiene la dirección física del laboratorio.
  - Ejemplo: Avenida Industria, 45, Barcelona
- **Fax:** Fax del laboratorio.
  - Dominio: Cadena numérica que contiene un número de fax.
  - Ejemplo: +34 917123456
- **Nombre persona:** Nombre de la persona responsable del laboratorio
  - Dominio: Cadena de texto que representa el nombre del responsable.
  - Ejemplo: Roberto Hernández
## Relaciones Definidas:
### Cliente Compra Medicamento
Cardinalidad: Un cliente puede comprar muchos medicamentos (1,N), y un medicamento puede ser comprado por muchos clientes (N,N).
Descripción: Relación entre clientes y medicamentos, indicando qué medicamentos ha comprado cada cliente.
### Medicamento Es Vendido por Farmacia
Cardinalidad: Una farmacia puede vender muchos medicamentos (1,N), y un medicamento puede ser vendido por muchas farmacias (N,N).
Descripción: Relación entre farmacia y medicamento, mostrando los medicamentos que una farmacia vende.
### Medicamento Es Fabricado por Laboratorio
Cardinalidad: Un laboratorio fabrica muchos medicamentos (1,N), y un medicamento puede ser fabricado por un laboratorio (N,1).
Descripción: Relación que conecta laboratorios con los medicamentos que producen.
### Cliente Usa Crédito
Cardinalidad: Un cliente puede tener una opción de crédito (1,1), indicando si tiene o no crédito.
Descripción: Relación que define si un cliente tiene la opción de realizar compras a crédito o no.
### Medicamento Sustituye a Otro Medicamento
Cardinalidad: Un medicamento puede sustituir a otros medicamentos (1,N), y un medicamento puede ser sustituido por otros medicamentos (N,1).
Descripción: Relación que indica si un medicamento puede ser sustituido por otro en caso de no estar disponible.

## Restricciones Semánticas Propuestas:
-Clientes sin crédito no pueden realizar compras a crédito: Esta restricción asegura que solo los clientes que tienen crédito asignado puedan optar por este método de pago.
-Un medicamento solo puede ser fabricado por un único laboratorio a la vez: Asegura que cada medicamento tiene un fabricante exclusivo, eliminando ambigüedades en la producción.
-Un medicamento no puede sustituirse a sí mismo: Impide que un medicamento esté registrado como su propio sustituto.
-El precio del medicamento no puede ser negativo: Para garantizar la validez de los datos, se debe asegurar que el precio de cualquier medicamento sea un valor positivo.
-Una farmacia no puede vender medicamentos que no tenga en inventario: Restricción que verifica que una farmacia solo pueda vender medicamentos que están disponibles en su inventario.
