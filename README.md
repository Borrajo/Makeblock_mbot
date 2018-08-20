# Makeblock_mbot
Fiirmware modification for Makeblock mBot upgrading features.

links:
+ mBot : https://www.makeblock.com/steam-kits/mbot
+ mBlock3 : http://www.mblock.cc/software/
+ Placa MeStepper : http://www.spc-makeblock.es/productos-spc-makeblock/piezas/driver-para-motor-paso-a-paso-me-v1/

## Descripcion
El mBot no posee la posibilidad de conectar motores PaP. 
Se modificó el firmware para que esto sea posible.

Se pueden poner hasta 4 stepper (uno en cada puerto) 

La unica limitacion radica en que el hardware del mBot no puede darle la tension necesaria a los motores, asique en caso de usar una placa oficial de makeblock habria que hacer alguna modificacion* (más adelante se hará).

este repositorio contiene el firmware modificado y la interfaz para el mBlock

## Firmware

### instalacion 
	Para instalar el firmware debe abrir el archivo firmware/mbot_firmware_stepper.ino con Arduino
	Conectar el mBot por USB a la PC
	Seleccionar en Herramientas->Placa : Arduino UNO
	Seleccionar Puerto y Cargar el sketch.
	(va a informar que está a un 97% de su capacidad y que podría ser inestable. Aun no ha sucedido nada).

### funcionamiento
	El motor se conecta a un A4988 y este se controla mediante solo 2 pines: uno de direccion y otro de pasos.
	El pin de direccion trabaja con 0/1 para indicar sentido horario o antihorario. Es el Slot1
	El pin de 'pasos' trabaja enviando pulsos, por cada pulso el motor da un paso. Es el Slot2

## Interfaz de mBlock

	Changelog:
	+ Se agregó el bloque 'parar' para los motores
	+ Se agregó la opcion 'set output' para usar el RJ25 como salidas
	+ Se agregó el bloque 'set Stepper' para funcionar con motores PaP
	
	Para actualizar la interfaz del mBlock solo hay que pegar el archivo mBot.s2e y la carpeta js en la siguiente ruta: 
	C:\Users\XXXXX\AppData\Roaming\com.makeblock.Scratch3.4.11\Local Store\mBlock\libraries\mbot donde XXXXX es el usuario actual