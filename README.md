# AventuraHospital
Noche en el hospital
Aventura conversacional de terror para consola, escrita en Java. Despiertas de noche en un hospital y debes encontrar una salida antes del amanecer. Tus decisiones afectan las rutas, los objetos disponibles, las vidas que conservas y el final.
Requisitos
•	Java Development Kit (JDK) instalado para compilar el programa. Se recomienda una versión LTS moderna (por ejemplo, JDK 17 o posterior).
•	Una terminal: PowerShell o Símbolo del sistema en Windows, Terminal en macOS o Linux.
•	No necesita bibliotecas externas, conexión a Internet ni una interfaz gráfica.
Comprueba la instalación ejecutando java -version y javac -version. Ambos comandos deben estar disponibles; si no, instala un JDK y configura el PATH según tu sistema operativo.
Importante: nombre del archivo y de la clase
El archivo recibido se llama JuegoHospital2.java, pero contiene la declaración public class JuegoHospital. Java exige que el nombre del archivo coincida exactamente con el de la clase pública. Por eso, javac JuegoHospital2.java dará un error mientras no se corrija esa diferencia.
La solución recomendada es renombrar el archivo a JuegoHospital.java y conservar la clase tal como está. Si el archivo está en la carpeta actual, ejecuta:
Windows (PowerShell o CMD):
ren JuegoHospital2.java JuegoHospital.java
javac JuegoHospital.java
java JuegoHospital
macOS o Linux:
mv JuegoHospital2.java JuegoHospital.java
javac JuegoHospital.java
java JuegoHospital
También puedes mantener el nombre JuegoHospital2.java cambiando la declaración en el código de public class JuegoHospital a public class JuegoHospital2. Después compílalo con javac JuegoHospital2.java y ejecútalo con java JuegoHospital2. El nombre de clase usado al ejecutar debe coincidir con el nombre declarado.
Cómo jugar
El juego se desarrolla enteramente en la consola. Lee la escena y escribe el número de una opción; pulsa Enter para confirmar. Algunas decisiones no tienen consecuencias, otras consumen objetos, hacen perder vidas o cambian la ruta. Puedes volver a empezar otra partida al terminar.
Empiezas con 3 vidas. Si las pierdes todas, la partida acaba. Las opciones numéricas inválidas se vuelven a pedir. Las respuestas sí/no aceptan s, si, sí, n o no. En el ahorcado debes introducir una letra de la A a la Z que no hayas usado antes. Para continuar en la ruleta rusa, pulsa Enter cuando se te indique.
Recorrido y escenas
La historia recorre las escenas 1 a 11, con posibles saltos, y luego presenta el enfrentamiento final con el Doctor. Si superas ese duelo, llegas a la escena 12 y eliges cómo escapar.
1.	Habitación 204: puedes salir, recoger la linterna o perder una vida al arrancarte el suero.
2.	Pasillo oscuro: avanzas con cautela, sigues los carteles o tomas la silla de ruedas. La silla te hace perder una vida y, si sobrevives, te lleva directamente a las escaleras, saltándose la enfermería y al enfermero.
3.	Enfermería: puedes conseguir la tarjeta de acceso. Después te enfrenta el enfermero siniestro en pares o nones.
4.	Escaleras de emergencia: bajar a ciegas es mortal sin linterna; con ella evitas la caída, pero la gastas. Bajar despacio es seguro.
5.	Recepción: puedes revisar cámaras, probar el walkie-talkie o buscar un plano.
6.	Quirófano: algunas acciones son seguras; coger el bisturí hace perder una vida.
7.	Laboratorio: forzar la puerta con la tarjeta abre un atajo a la sala de máquinas y omite farmacia, archivo, cafetería y farmacéutico. La tarjeta se consume. Sin ella, la puerta electrificada te mata.
8.	Farmacia: puedes recoger un botiquín. A continuación te enfrentas al farmacéutico en la ruleta rusa.
9.	Archivo: buscar tu expediente o salir no causa daño; abrir el cajón de la cámara frigorífica hace perder una vida.
10.	Cafetería: la botella sin etiqueta es tóxica. El botiquín puede salvarte como antídoto y se consume; sin él, mueres.
11.	Sala de máquinas: tocar el cuadro eléctrico hace perder dos vidas; las otras opciones permiten continuar.
12.	Hall principal: tras vencer al Doctor, eliges una salida o intentas entrar en el despacho del director.
Objetos e inventario
La mochila puede contener tres objetos. El estado actual aparece en los menús:
•	Linterna: protege al bajar corriendo por las escaleras oscuras. Se consume al usarla.
•	Tarjeta de acceso: permite abrir el atajo del laboratorio o entrar al despacho del director para conseguir el final secreto. El atajo del laboratorio la consume, por lo que ya no servirá en el despacho.
•	Botiquín: cuando te falte una vida, los menús ofrecen una opción adicional para recuperar una vida. También puede usarse como antídoto en la cafetería. Se consume cuando lo usas.
Enemigos y minijuegos
•	Enfermero siniestro — pares o nones: eliges pares o nones y compites en rondas al mejor de tres. En cada ronda introduces de 0 a 5 dedos; el número del enfermero se genera al azar. Perder el duelo termina la partida.
•	Farmacéutico — ruleta rusa: un revólver tiene seis cámaras y una bala. Eliges quién dispara primero y los turnos alternan hasta que sale la bala. Si te toca a ti, pierdes; si le toca al farmacéutico, ganas. Perder termina la partida.
•	Doctor — ahorcado: adivinas una palabra aleatoria de una lista de cinco, con una pista y un máximo de seis errores. Las palabras se muestran sin tildes. Si el Doctor gana, termina la partida; si adivinas, puedes llegar al hall.
Finales
•	Final 1: Libertad (bueno): sales por la puerta principal con al menos dos vidas.
•	Final 2: Escapas con secuelas (neutral): sales por la puerta principal con menos de dos vidas, o pides rescate desde la azotea.
•	Final 3: La verdad (secreto): entras en el despacho del director usando la tarjeta.
•	Final 4: No sales del hospital (malo): mueres en una decisión o pierdes contra un enemigo.
Estadísticas
Al final de cada partida se muestra la duración total, cuándo conseguiste cada objeto, cuántas vidas perdiste y el momento aproximado de cada pérdida. También se informa de la duración de cada enfrentamiento, si venciste al enemigo y cuál fue el duelo más largo entre los que ganaste. Los tiempos se cuentan en segundos y se presentan en minutos y segundos.
Validación y funcionamiento interno
El juego lee la entrada como líneas de texto y valida las opciones antes de continuar: no usa nextInt, así que letras, símbolos, líneas vacías y números fuera del rango no rompen la lectura de menús. Las letras repetidas o que no sean una sola letra de la A a la Z tampoco se aceptan en el ahorcado. Si se cierra la entrada de consola, el programa termina con un mensaje.
Todo el programa está implementado en una única clase Java, sin dependencias externas. Usa arrays para el inventario, los datos de enemigos y las palabras con sus pistas; Math.random() determina algunos resultados de los minijuegos y la palabra del jefe.
Solución de problemas
•	`javac` o `java` no se reconoce: instala un JDK y añade su carpeta bin al PATH; abre una terminal nueva y vuelve a comprobar las versiones.
•	Error sobre el nombre del archivo: confirma que JuegoHospital.java contiene public class JuegoHospital, o renombra la clase pública a JuegoHospital2 si conservas el archivo original.
•	No encuentra el archivo: cambia la terminal a la carpeta donde guardaste el .java, o abre una terminal desde esa carpeta.
•	La consola parece esperar: el juego está esperando que escribas una opción o pulses Enter, según el mensaje que aparece.
Licencia y repositorio
El código fuente no especifica una licencia. Consulta con su autor antes de redistribuirlo. El comentario inicial contiene un marcador para añadir el enlace al repositorio GitHub cuando esté disponible.
