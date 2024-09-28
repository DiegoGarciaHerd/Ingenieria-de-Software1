# Practica 2 - Historias de Usuario

Semana: August 26, 2024
Hecho: No
Tema: Historia de Uso
Tipo: Practica

# Historias de Usuario

- Una historia de usuario es una descripción corta y simple de un
requerimiento de un sistema, que se escribe en lenguaje común del
usuario y desde su perspectiva.
- Son utilizadas en las metodologías de desarrollo ágiles (Ejemplo: XP,
SCRUM) para la especificación de requisitos.
- La historia de usuario debe responder a las siguientes preguntas:
    - **¿ Quién se beneficia ?**
    - **¿ Qué se quiere ?**
    - **¿ Cuál es su beneficio ?**

<aside>
💡

**ID** : Identificador Univoco de la historia expresado como texto generalmente en forma de
**<verbo><sustantivo>**

TITULO:  Descripción de la historia de la forma: **Como** <rol> **quiero** <algo> **para** <beneficio>.

REGLAS DE NEGOCIO: Conjunto de reglas, normas, políticas, etc. que condicionan el modo de operación.

</aside>

![image.png](image.png)

![image.png](image%201.png)

## Ejemplo

Rol de usuarios:  

- Persona
- Matriculado

Historias de Usuario

- Matricular Persona
- Inscribir matriculado al curso
- Pagar con tarjeta

## -Tener en cuenta

- Roles de Usuario → Singular
- Historias de usuario → Verbo en infinitivo
- Cuando una historia tiene “muchos “ criterio de aceptación es una pauta para separarla en otras historias.
- Cuando varias historias tienen varios criterios de aceptación comunes deberian separarse en otras historias

---

### Matricular Persona

![image.png](image%202.png)

![image.png](image%203.png)

### Inscribir Matriculado

![image.png](image%204.png)

![image.png](image%205.png)

![image.png](image%206.png)

---

### Pagar con Tarjeta

---

![image.png](image%207.png)

![image.png](image%208.png)

![image.png](image%209.png)

## Ejemplo con Listado de cupos

- Listar cursos con cupo.
    - Si agregamos esta historia desaparece el escenario 2 de la HU “Inscribir a un curso” ya que solo se puede elegir un curso si previamente fue listado y por lo tanto tiene cupo.
    Además, si aclaramos que el botón de “Inscribirse” solo se muestra en los cursos en los que no se está inscripto previamente, también se puede eliminar el escenario 3 de la HU “Elegir un curso”. Esto mejora la experiencia del usuario, ya que de otra manera permitiríamos presionar “Inscribirse” sobre un curso al que el matriculado ya está inscripto y sabemos que fallará.

![image.png](image%2010.png)

![image.png](image%2011.png)

# Practica 1

## Problema 1 - Alquiler de mobiliario

Suponga que trabaja en una consultora la cual ha sido recientemente contactada por una empresa de alquiler de mobiliario para eventos para la realización de una app.
De las diferentes entrevistas se ha obtenido la siguiente información:
El gerente nos dijo que resulta fundamental tener una aplicación móvil que nos permita manejar la agenda de la empresa, sabiendo qué disponibilidad tenemos y permitiendo que nuestros clientes alquilen a través de la app. Para esta primera versión de la app, el gerente nos pidió que sea posible dar de alta los diferentes mobiliarios, así como la posibilidad de que los usuarios puedan realizar una reserva de alquiler desde sus dispositivos. Para el detalle de cómo se realiza la carga de los muebles, el gerente nos sugirió hablar con el encargado del departamento de mobiliario. El encargado de mobiliario nos comentó que de cada mueble se debe cargar código de inventario, tipo de mueble, fecha de creación, fecha de último
mantenimiento, estado (libre, de baja, alquilado) y el precio de alquiler. Además, no pueden existir códigos repetidos y por el contrato de la franquicia, el precio debe cargarse en dólares. Para que el encargado pueda dar de alta el mobiliario debe autenticarse en el sistema. El registro de los usuarios de carga no debe modelarse.
El encargado del departamento de alquileres no comentó acerca de las reservas de los alquileres. Por una política comercial de la marca una reserva tiene que incluir como mínimo 3 muebles. La reserva debe tener una fecha, lugar del evento, cantidad de días y mobiliario junto a su cantidad. Para realizar una reserva se debe abonar el 20% del total del alquiler. El pago de la reserva se realiza únicamente con tarjeta de crédito validando número de tarjeta y fondos a través de un servicio del banco. Luego de efectuado el pago, se emite un número de reserva único que será luego utilizado por el cliente para hacer efectivo el alquiler.

---

Rol de usuarios: 

- Cliente
- Encargardo de mobiliario

Historias de Usuario: 

- Cargar mueble
- Reservar muebles
- Pagar con Tarjeta

### Cargar Mueble

ID: Cargar Mueble

TITULO: Como encargado de mobiliario quiero ingresar un mueble a la app para que los clientes pueden realizar su reserva

REGLAS DE NEGOCIO: 

- No pueden existir codigos repetidos
- El precio debe cargarse en dolares

---

Criterios de aceptacion: 

Escenario 1: Carga de mueble exitosa
**Dado** que el codigo 1234 no existe en el sistema y el precio se ingreso en dolares
**Cuando** el encargado de mobiliario ingresa el codigo de inventario 1234 , tipo de mueble mesa , fecha de creacion 1/1/2024 , fecha ultimo mantenimiento 20/08/2024 , estado libre, y el precio de alquiler 100 $ 
**Entonces** se registra correctamente el mueble en el sistema.

Escenario 2: Carga de mueble fallida por codigo repetido

Dado que el codigo 1235 ya se encuentra registrado en el sistema 
Cuando el encargado de mobiliario ingresa el codigo de inventario 1235, tipo de mueble mesa, fecha de creacion 1/1/2024, fecha de ultimo mantenimiento 20/08/2024, estado libre, y el precio de alquiler 100$
Entonces se registra correctamente el mueble en el sistema.

Escenario 3: Carga de mueble fallida por divisa incorrecta

Dado que el codigo 1234 no existe en el sitema y el precio se ingreso en pesos
Cuando el encargado de mobiliario ingresa el codigo de inventario 1234 , tipo de mueble mesa , fecha de creacion 1/1/2024, fecha ultimo mantenimiento 20/08/2024, estado libre , y el precio de alquiler 100$ 
Entonces el sistema informa que el precio debe ser ingresado en dolare

---

### Reservar Muebles

FRENTE 

ID : Reservar Muebles

TITULO: Como cliente quiero reservar un mueble para un evento

REGLAS DE NEGOCIO: 

- La reserva debe incluir como minimo 3 muebles.
- Debe haber Stock
- Pago con tarjeta

---

Criterios de Aceptación : 

Escenario 1: Reserva exitosa

Dado que la reserva incluye 3 muebles , hay stock y la tarjeta es valida

Cuando se ingresa el numero de muebles 3 y los datos de la tarjeta valida

Entonces el sistema realiza la reserva y emite un numero de reserva unica

Escenario 2 : Fallo reserva cantidad de muebles invalida

Dado que la reserva incluye 2 muebles , hay stock y la tarjeta es valida

Cuando se ingresa el numero de muebles 2 y los datos de la tarjeta valida

Entonces el sistema responde que la cantidad de muebles es invalida

Escenario 3: Fallo reserva por falta de stock

Dado que la reserva incluye 3 muebles , no hay stock y la tarjeta es valida

Cuando se ingresa el numero de muebles 3 y los datos de la tarjeta valida

Entonces el sistema responde que no queda stock

Escenario 4 : Fallo de reserva por numero de tarjeta invalido

Dado que la reserva incluye 3 muebles, hay stock y el numero de tarjeta es invalido

Cuando se ingresa el numero de muebles 3 , el numero de tarjeta invalida

Entonces el sistema responde que la tarjeta es invalida

---

### Pagar con Tarjeta

ID : Pagar con Tarjeta

Titulo : Como cliente/usuario quiero pagar con tarjeta para poder reservar mobiliario

REGLAS DE NEGOCIO:

- Se debe abonar el 20% del alquiler

---

Criterios de aceptación:

Escenario 1: Pago exitoso

Dado que se abona el 20% del alquiler ,la conexion con el banco es exitosa y el nro de tarjeta 1234 es valido y la tarjeta tiene saldo
Cuando el cliente ingrese el numero de tarjeta 1234,

Entonces el sistema registra el pago y retorna un resultado de exito

Escenario 2: Pago rechazado por no abonar 20% del alquiler

Dado que no se abona el 20% del alquiler , la conexion con el servidor del banco es exitosa y el numero de tarjeta 2333 es valido y la tarjeta tiene saldo
Cuando el cliente ingrese el numero de tarjeta 2333 

Entonces el sistema informa que la cantidad abonada es incorrecta y no registra el pago

Escenario 3: Pago rechazado por numero de tarjeta invalido

Dado que se abona el 20% del alquiler, la conexión con el servidor del banco es exitosa y el numero de tarjeta 4444 es invalido

Cuando el cliente ingrese el numero de tarjeta 4444

Entonces el sistema informa que la tarjeta es invalida y no registra el pago

Escenario 4 : Pago rechazado por conexion con el servidor fallida

Dado que no se puede establecer conexion con el servidor

Cuando el cliente quiere realizar el pago 

Entonces el sistema informa que no se pudo realizar conexion con el servidor del banco

Escenario 5 : Pago rechazado por saldo insfuciente

Dado que se abona el 20% del alquiler, la conexion con el servidor del banco es exitosa ,el numero de tarjeta 5555 es valida y la tarjeta no tiene salgo

Cuando el cliente ingrese el numero de tarjeta 5555

Entonces el sistema informa que el saldo en la tarjeta es insuficiente y no registra el pago.

## Problema 2 - Posgrado

Suponga que trabaja en el área de sistemas de la Facultad de Informática y se le solicitó la automatización del pago de carreras de posgrado. Inicialmente se coordinó una reunión con el director del posgrado y se obtuvo la siguiente información:
Ya que no se desea seguir cobrando el dinero en la secretaría, es necesario que los alumnos puedan pagar las carreras vía web. Como el director de posgrado no realiza tareas administrativas nos recomendó hablar con el secretario académico.
De la entrevista con el secretario académico se obtuvo la siguiente información:
Es necesario cargar las carreras a un sistema. En esta primera versión del sistema sólo se nos pidió esta funcionalidad, sin la modificación ni eliminación. De cada carrera se conoce: nombre de la carrera (no puede repetirse), duración en años (a partir de la consulta del estatuto de posgrado se obtuvo que como máximo son 5 años), costo y cantidad máxima de cuotas
para el pago. La carga de las carreras no la realiza el secretario académico sino un empleado administrativo. Al preguntarle por la dinámica del sistema, el secretario académico nos derivó con el jefe del área administrativa, con el cual hicimos otra entrevista y pudimos obtener la siguiente información:
El requerimiento fue que el alumno ingrese a la web de posgrado y pueda registrarse ingresando: nombre, apellido, nombre de usuario (único) y contraseña (más de 6 dígitos). Cualquier alumno previamente registrado, puede iniciar sesión.con su nombre de usuario y contraseña, habilitándose la inscripción a alguna de las carreras. Para ejemplificar esta
funcionalidad nos otorgaron acceso al sistema SIGEF, el cual realiza funcionalidades similares para las carreras de grado.
Para inscribirse, el alumno deberá seleccionar la carrera, ingresar la cantidad de cuotas a pagar, ingresar el número de tarjeta y, en caso de que la tarjeta sea válida y tenga fondos, se hará efectivo el cobro y la inscripción. La tarjeta de crédito se valida a través de un servicio del banco con el cual la universidad tiene convenio. Luego de efectuado el cobro, el sistema debe imprimir dos comprobantes, uno de inscripción y otro de pago. La única forma que tiene el alumno de pagar es con tarjeta de crédito.

---

Rol de usuarios:

- Alumnos
- Empleado administrativo
- Usuario

Historias de Usuario

- Pagar Carrera
- Cargar carrera
- Registrar usuario
- Iniciar sesion
- Validar Tarjeta

---

### Cargar carrera

ID : Cargar carrera

TITULO: Como empleado administrativo quiero poder cargar las carreras para que los alumnos puedan inscribirse

REGLAS DE NEGOCIO:

- Carrera no puede tener una duracion de mas de 5 años

---

Criterios de aceptación

Escenario 1: Carga de carrera exitosa

Dado que el nombre de carrera ‘Lic en Informatica’ no se encuentra en el sistema y la duracion de 5 años es valida

Cuando el empleado ingrese nombre de Carrera Lic en informatica y duracion 5 años
Entonces el sistema registra la carrera en el sistema y retorna un resultado exitoso

Escenario 2: Carga de carrera fallida por nombre repetido

Dado que el nombre de carrera ‘ Lic en sistemas ‘ ya esta cargado en el sistemy la duracion de 5 años es valida

Cuando el empleado ingrese el nombre de carrera Lic en Sistemas y duracion 5 años

Entonces el sistema retorna que la carrera ya se encuentra registrada en el sistema

Escenario 3: Carga de carrera fallida por duracion invalida

Dado que el nombre de carrera ‘ Ing en computación ‘ no se encuentra en el sistema y la duracion de 6 años es invalida

Cuando el empleado ingrese el nombre Ing en computación y duración 6 años

Entonces esl sistema retorna que la duracion de la carrera es invalida

---

### Registrar Usuario

ID : Registrar usuario

TITULO : Como alumno quiero poder registrarme como usuario para poder pagar una carrera

REGLAS DE NEGOCIO:

- Contraseña debe tener mas de 6 digitos

---

Criterios de aceptación:

Escenario 1: Registro de usuario exitoso

Dado que el nombre ‘diegogh’ es unico y la contraseña ‘diego1234’ tiene mas de 6 digitos

Cuando el alumno ingrese nombre de usuario ‘diegogh’ y la contraseña diego1234 

Entonces se registra el usuario en el sistema y retorna que el registro fue exitoso

Escenario 2: Registro de usuario fallido por nombre repetido

Dado que el nombre MessiGOAT no es unico y la contraseña ‘messi1234’ es valida

Cuando el alumno ingrese nombre de usuario MessiGOAT y la contraseña messi1234

Entonces el sistema retorna que el nombre de usuario ya esta elegido

Escenario 3: Registro de usuario fallido por contraseña invalida

Dado que el nombre pepito1234 es unico y la contraseña 12345 tiene menos de 6 digitos

Cuando el alumno ingrese nombre de usuario pepito1234 y la contraseña 12345 

Entonces el sistema retorna que la contraseña es invalida

---

### Iniciar Sesión

ID : Iniciar Sesión

TITULO: Como usuario quiero iniciar sesion para poder ver/pagar las carreras

REGLAS DE NEGOCIO:

---

Criterios de aceptación 

Escenario 1: Inicio de sesion exitoso

Dado que el nombre ‘diegogh’ se encuentra registrado en el sistema y la contraseña diego1234 es la correspondiente

Cuando se ingrese nombre diegogh y contraseña diego1234

Entonces se iniciara la sesion correctamente

Escenario 2: Inicio de sesion fallido por nombre no registrado

Dado que el nombre ‘timmy’ no se encuentra registrado en el sistema

Cuando se ingrese el nombre timmy y contraseña timmythekid

Entonces el sistema informara que el nombre de usuario no existe

Escenario 3: Inicio de sesion fallido por contraseña incorrecta

Dado que el nombre ‘jimmy’ se encuentra registrado en el sistema y la contraseña 12dknfd es incorrecta

Cuando se ingrese el nombre jimmy y contraseña 12dknfd

Entonces el sistema informara que la contraseña es incorrecta.

---

### Pagar Carrera

ID : Pagar carrera

TITULO: Como alumno quiero poder pagar una carrera para poder cursarla

REGLAS DE NEGOCIO:

- Se debe pagar con tarjeta de credito

---

Criterios de aceptación :

Escenario 1: Pago de carrera exitoso

Dado que la tarjeta de credito es validada correctamente

Cuando se ingrese las cuotas a pagar 12 y numero de tarjeta 12345 con saldo suficiente

Entonces se registra el pago y el sistema imprimie dos comprobantes, uno de inscripción y otro de pago

Escenario 2 : Pago de carrera fallido por tarjeta invalida

Dado que la tarjeta de credito es invalidada

Cuando se ingrese a pagar en 12 cuotas y numero de tarjeta 99999 

Entones se no se registra el pago y se informa que la tarjeta es invalida

---

### Validar Tarjeta

ID : Validar Tarjeta

TITULO: Como servicio de banco quiero validar una tarjeta de credito para que se pueda efectuar un pago

REGLAS DE NEGOCIO:

---

Criterios de aceptación:

Escenario 1 : Validacion de tarjeta exitosa

Dado que se establece la conexion con el servidor, el numero de tarjera 1234 es valido y la tarjeta tiene saldo

Cuando se ingrese numero de tarjeta 1234

Entonces el banco envia una señal de que la tarjeta es valida

Escenario 2: Validacion de tarjeta fallida por falla en la conexion con el servidor

Dado que no se puede stable la conexion con el servidor del banco

Cuando se intente validar la tarjeta

Entonces el banco envia que no se puede establecer conexion con el servidor

Escenario 3: Validacion de tarjeta fallida por numero de tarjeta invalido

Dado que se establece la conexion con el servidor del banco y el numero de tarjeta 2323 es invalido

Cuando se intente validar la tarjeta 2323

Entonces el banco envia que el numero de tarjeta es invalido

Escenario 4: Validacion de tarjeta fallida por saldo insuficiente

Dado que se establa la conexion con el servidor del banco y el numero de tarjeta 3433 es valido y no tiene saldo suficiente

Cuando se intente validar la tarjeta 3433

Entonces el banco envia que el saldo es insuficiente.

---

## Problema 3 - Contratos SIN TERMINAR

Suponga que trabaja en un grupo en el área de sistemas de una organización y está por comenzar un nuevo proyecto para desarrollar un sistema que depende del departamento contable.
El sistema deberá administrar los contratos realizado con terceros. En una de las reuniones con el jefe de departamento nos dijo que él no usará el sistema pero que recibirá listados del personal contratado ya que deberá firmarlos para elevarlos a las autoridades.
Para obtener más información generamos una reunión con el empleado de mesa de entradas. Nos contó que el problema que tienen actualmente es que realizan todas las minutas a mano por lo cual desean automatizar esta tarea. Las minutas son el paso previo a un contrato. Para confeccionar una minuta, el empleado de mesa de entradas debe ingresar nombre y número de CUIT de una persona a contratar, tipo de contrato, fecha de comienzo, duración y monto, a lo que el sistema le asociará un número de minuta automáticamente. Nos recomendó leer la reglamentación vigente acerca de contratos de la que obtuvimos que los montos de los mismos no pueden superar los $25.000 y que la duración debe ser como máximo de
6 meses. Una vez confeccionada la minuta por parte del empleado de mesa de entradas, la misma queda pendiente de aprobación. El que puede aprobar una minuta es el empleado de rendiciones. Realizamos una reunión con él y nos contó que su tarea consiste en evaluar las minutas para determinar su aprobación. También nos dijo que en otro trabajo que tiene usan un sistema llamado MiMiNuTa al que nos puede dar acceso para ver como hacen esa tarea. Después del análisis de este sistema, se concluyó que para aprobar una minuta necesitaría ingresar un número de minuta y que el sistema muestre los datos de la misma para poder aprobarla. Nos dijo que no puede aprobar la minuta si la persona a contratar tiene 3 contratos vigentes (minutas aprobadas) ni tampoco si el CUIT de la persona a contratar está inhabilitado por la AFIP. Actualmente se comunica telefónicamente con la AFIP para realizar esta verificación, pero sabe que ésta provee un servicio para aplicaciones que permite hacer la verificación en línea. Esto último nos obligó a generar una reunión con el administrador de servidores de la AFIP. Nos dijo que para poder conectarnos con un servidor de la AFIP, el sistema debe mandar un token (código que identificará de manera única a nuestra aplicación) y CUIT, si el token es correcto, el servidor responde si el CUIT está habilitado o no.
Por último el empleado de rendiciones será el responsable de imprimir los listados con las minutas aprobadas, es decir, un listado con el personal contratado para poder dárselo al jefe de departamento para que lo firme.

---

Rol de usuarios:

- Empleado de mesa de entradas
- Empleado de rendiciones

Historias de usuario: 

- Confeccionar Minuta
- Aprobar Minuta
- Conectar con AFIP
- Imprimir minutas aprobadas

### Confeccionar Minuta

ID: Confeccionar Minuta

TITULO: Como empleado de mesa de entradas quiero confeccionar una minuta para que pueda ser aprobada

REGLAS DE NEGOCIO: 

- Monto no puede superar $25000
- Duración maxima de 6 meses

---

Criterios de aceptación 

**Escenario 1** : Confección de minuta exitosa

Dado que el monto de 25000 es valido y la duracion de 6 meses es valida

Cuando el empleado de mesa de entradas ingrese el nombre  ‘ Oppie’ , CUIT  ‘1234’ , tipo de contrato ‘A’  , fecha de comienzo 11/09/24 , duración de 6 meses y monto 25000

Entonces el sistema registra la minuta e informa el exito en la operación.

Escenario 2 : Confección de minuta fallida por monto invalido

Dado que el monto 27000 es invalido y la duración de 6 meses es valida

Cuando el empleado de mesa de entradas ingresa el nombre ‘Jose ‘ , CUIT ‘321’ , tipo de contrato B , fecha de comienzo 11/04/24 , duración de 6 meses y monto 27000

Entonces el sistema informa que el monto es superior al maximo.

**Escenario 3**: Confeccion de minuta fallida por duracion invalida

Dado que el monto 24000 es valido y la duración de 7 meses es invalida

Cuando el empleado de mesa de entradas ingresa el nombre ‘Martin‘ , CUIT ‘3421’ , tipo de contrato B , fecha de comienzo 11/04/24 , duración de 7 meses y monto 24000 

Entonces el sistema informa que la duración es superior al maximo.

### Aprobar Minutas

ID : Aprobar Minutas

TITULO: Como empleado de rendiciones quiero evaluar una minuta para poder determinar su aprobación

REGLAS DE NEGOCIO: 

- Personas con menos de 3 minutas aprobadas
- Persona con CUIT habilitado por AFIP

SIN TERMINAR  ¿ Conectar con AFIP Deberia ser otra historia de usuario ?

Codigo repetidp rela de negocio o condición?

## Problema 4 - Venta de bebidas SIN TERMINAR

Se desea modelar un sistema para el manejo de venta de bebidas alcohólicas en linea. Para poder empezar a comprar en el sitio, es necesario que las personas se registren ingresando nombre, apellido, mail (será utilizado como nombre de usuario por lo tanto debe ser único) y edad. Solo se permite que se registren al sitio personas mayores a 18 años, de lo contrario el
sistema debe mostrar en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores. Si el registro es exitoso el sistema genera una contraseña que es enviada al mail ingresado en el registro. Para comprar el usuario debe iniciar sesión y una vez logueado el sistema muestra una lista de bebidas, una vez que el usuario selecciona todos los productos que desea comprar, si el usuario es premium se le hace un descuento del 20% y se informa en pantalla el total menos el 20%. Ademas si el usuario seleccionó productos por un monto superior a los $4500 se le hace un 10% de descuento y se informa en pantalla el total menos el 10%. Tenga en cuenta que si el usuario es premium y compra por un monto superior a $4500 se deben aplicar ambos descuentos.

### Registrar usuario

ID : Registrar Usuario

TITULO: Como cliente quiero poder registrarme como usuario para poder comprar bebidas

REGLAS DE NEGOCIO: 

- Usuarios mayores de 18 años

---

Criterios de aceptación: 

Escenario 1: Registro de usuario exitoso

Dado que la edad es mayor a 18 años y el mail [diegogarciaherd@gmail.com](mailto:diegogarciaherd@gmail.com) es unico 

Cuando el empleado ingresa bkbknblk

Escenario 2 : Registro de usuario fallido por edad menor a 18

Dado 

Cuando 

Entonces

Escenario 3: Registro de usuario fallido por email ya registrado

Dado 

Cuando

Entonces

---

### Iniciar sesión

ID : Iniciar sesión

TITULO: Como usuario quiero iniciar sesion para poder ver la lista de bebidas

REGLAS DE NEGOCIO:

---

Criterios de aceptación

Escenario 1: Inicio de sesion exitoso

Escenario 2: Inicio de sesion fallido por email no registrado

Escenario 3: Inicio de sesion fallido por contraseña incorrecta

---

### Cerrar sesión

### Comprar bebidas

### Comprar bebidas premium

---

SIN TERMINAR - ¿ Como modelo comprar hacer los descuentos segun si es premium o no ?

---

## Problema 5 - Casa de fotografía

Se desea desarrollar un sistema para la impresión de fotos para una casa fotográfica. Los clientes pueden subir sus fotos, pagar por internet y luego ser retiradas personalmente por el local.
Para subir las fotos la persona debe registrarse en el sitio, ingresando sus datos personales, nombre, apellido, email, domicilio, nombre de usuario y contraseña.
Una vez autenticado, el usuario puede subir un máximo de 50 fotos para ser impresas. Las fotos se ingresan de a una. Una vez subidas, el usuario debe abonar el monto total (el valor de cada foto es de $15). El pago se realiza con tarjeta de crédito, ingresando los datos de la misma (número de tarjeta, código de seguridad y nombre del titular), la cual debe ser validada a través del sistema del banco. Una vez que se realiza el pago se le otorga al cliente un código
único que le servirá posteriormente para retirar las fotos.
Un cliente debe acercarse a la sucursal para retirar las fotos enviadas previamente. Para esto debe presentar el código único a un empleado. Este registra el código, la fecha de retiro y entrega las fotos al cliente.

---

Rol de usuarios :

- Clientes
- Empleado

Historias de usuario

- Registrar usuario
- Subir fotos
- Pagar con tarjeta
- Retirar fotos

---

### Registrar Usuario

ID : Registrar usuario

TITULO: Como cliente quiero registrarme como usuario para poder ingresar al sitio 

REGLAS DE NEGOCIO:

---

Criterios de aceptación:

Escenario 1: Registro de usuario exitoso

Escenario 2: Registro de usuario fallido por usuario ya ingresado

### Iniciar Sesión

### Cerrar sesion

### Subir fotos

ID : Subir fotos

TITULO: Como usuario quiero poder subir mis fotos para poder imprimirlas

REGLAS DE NEGOCIO:

- Maximo 50 fotos de a una
- Fotos de a una

---

Criterios de aceptacion

Escenario 1 : Foto subida con exito

Escenario 2: Fallo subir foto porque el usuario supero el maximo de fotos subidas

Escenario 3: Fallo subir foto porque el usuario sube mas de una foto al mismo tiempo

---

### Pagar con tarjeta

### Retirar fotos

## Problema 6 - Biblioteca

La biblioteca de una escuela primaria realiza su trabajo de forma manual y requiere un sistema informático que automatice su funcionamiento.
La bibliotecaria recibe libros por donaciones de los padres de los chicos que asisten a la escuela. De un mismo libro se pueden tener varios ejemplares.
Para que un alumno pueda asociarse debe presentar el DNI y certificado de alumno regular. Una vez asociado, se le otorga un carnet con su correspondiente número de socio.
Los préstamos se realizan exclusivamente a socios habilitados, que no posean más de tres préstamos vigentes y no tengan préstamos vencidos. La bibliotecaria presta libros que se encuentren en buen estado. Cuando un libro se encuentra deteriorado ya no se presta.
Cuando el socio retorna un libro se verifica si el préstamo se encuentra vencido. En este caso, la bibliotecaria suspende al socio, que por 15 días no podrá solicitar nuevos préstamos.

Rol de usuarios: 

- Alumno
- Socio habilitado

Historias de Usuario:

- Asociar alumno
- Realizar prestamo
- Retornar Libro

---

### Asociar alumno

ID : Asociar alumno

TITULO: Como alumno quiero asociarme a la biblioteca para poder pedir prestamos de libros.

REGLAS DE NEGOCIO:

- Certificador de alumno regular

---

Criterios de aceptación:

Escenario 1 : Alumno asociado exitosamente

Dado que el dni 43243543 no se encuentra registrado en el sistema y el certificado de alumno regular es vigente

Cundo el alumno presenta su dni 43254624 y su certificado de alumno regular

Entonces se le otorga al alumno el carnet correspondiente.

Escenario 2 : Fallo de asociacion de alumno por dni ya registrado

Dado que el dni 23322334 ya se encuentra registrado en el sistema

Cuando 

Escenario 3 : Fallo de asociacion por no presentar certificado de alumno regular

---

### Pedir prestamo

ID: Pedir prestamo

TITULO: Como alumno quiero pedir un prestamo para poder accerder un libro

REGLAS DE NEGOCIO: 

- Socios habilitados
- No mas de 3 prestamos vigentes
- Sin prestamos vencidos
- Libros en buen estado

---

Criterios de aceptacion:

Escenario 1 : Prestamo realizado con exito

Dado que el alumno con dni 32323323 esta habilitado , tiene 3 prestamos vigentes, no tiene prestamos vencidos y el libro que ha pedido esta en buen estado

Cuando el socio solicita el prestamo del libro ‘Crimen y castigo’

Entonces el sistema registra el prestamo del libro Crimen y lo añade a los prestamos vigentes del socio.

Escenario 2 : Fallo en el prestamo por alumno no asociado

Dado que el alumno con dni 56666666 no se encuentra asociado al sistema

Cuando el alumno solicite el prestamo de Habitos atomicos

Escenario 3: