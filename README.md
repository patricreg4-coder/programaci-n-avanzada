# Proyecto playa de estacionamiento automático con IOT

Logica del sistema de reserva<br>
Los tres escenarios posibles:<br>

Totalmente Libre: El LED verde se enciende, la pantalla LCD dice "Hay lugar!" y cualquier auto que se pare frente al sensor ultrasónico de entrada hará que la barrera se abra.
Prioridad de Reserva: Si la capacidad es de 3 autos, hay 2 autos estacionados y 1 persona reservó desde su casa o en el camino , la pantalla física mostrará "Disponibles: 0" y "Completo/Reserv.".
Bloqueo por Reservas: Si la capacidad máxima es 3, hay 2 autos físicos y 1 reserva activa. Aunque físicamente veas un lugar vacío, el sistema lo considera lleno. Si un auto común se detiene en la entrada, el ultrasónico lo detecta pero el código evalúa la condición y no le abre la barrera, mostrando en la LCD "SOLO RESERVAS".


Estado Completo: Cuando los autos físicos llegan a la capacidad máxima (autos == capacidadMax), el sistema bloquea tanto el ingreso físico como la posibilidad de seguir reservando desde la app.
Acceso Seguro: Cuando el usuario que reservó llegue a la entrada, presionará el botón asignado a V4 en su celular: la barrera se levantará con el mensaje "CHECK-IN RES.", sumará 1 al contador físico de autos y restará 1 al contador de reservas pendientes.

¿Qué pasa cuando alguien reserva desde Blynk?
El usuario presiona "Reservar" en la app.
Las plazas disponibles disminuyen en 1 (el lugar queda guardado).
Se genera un "Token o Permiso de Entrada" (un botón especial en la app ).
Cuando el usuario llega físicamente al estacionamiento, presiona un botón en su app ("Abrir mi Reserva") que valida su entrada, levanta la barrera y cambia el estado de "Reservado" a "Ocupado".

Se agrego foto de los datastream creados en la app:

<img width="670" height="1218" alt="WhatsApp Image 2026-07-04 at 10 58 26" src="https://github.com/user-attachments/assets/8c093558-59ef-481a-883d-c8df362a6ec7" />


Seguridad
Se envía un mensaje de advertencia a la pantalla de tu celular:
para ello en la consola web de Blynk, entramos a Template y luego a "Eventos". 
Se agrego un nuevo evento con el nombre de código: alerta_intruso.
Se configuro lo configuro como tipo de evento Critical (Crítico) y activa las casillas de (Enviar notificación a la aplicación móvil).

<img width="1600" height="1200" alt="WhatsApp Image 2026-07-04 at 15 19 10" src="https://github.com/user-attachments/assets/fd27af16-b7a9-46c3-9f9c-0523292881d2" />


