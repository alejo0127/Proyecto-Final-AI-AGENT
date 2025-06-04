# Proyecto-Final-AI-AGENT
La finalidad de este documento es explicar el paso a paso de como se realizo el agente de IA, por medio de el software n8n en local, el cual presento ciertos retos a la hora de conectarse con el objetivo destino que era telegram, debido a que n8n al estar en local no recibia https, y por ende debiamos crear un tunel por medio de ngrok, pero todo esto se explicara mas adelante paso a paso : 

Paso #1 : 
Instalar n8n : en mi caso yo instale n8n por medio de debian con los docker que son los contenedores que nos daran multiples beneficios, que por mencionar algunos pueden ser la facilidad de instalacion y despliegue, nos simplifica mucho el proceso en vez de realizarlo por node.js, ademas nos ayuda con temas aislamiento y seguridad, etc.
El punto es que antes de instalar n8n, debemos tener tanto oracle virtual box que son las maquinas corriendo, y el git bash que es el simulador de la terminal de linux en windows, este utlimo sera fundamental porque las primeras acciones se realizaran desde alli.

Entonces suponiendo que tenemos descargado git bush, que es el icono que les muestro en la imagen, lo podemos buscar por medio de la venta de interaccion con windows.


![image](https://github.com/user-attachments/assets/b7d06a3e-b755-4ac7-b44e-e5476d5f6c6b)



Empezaremos por la descarga del docker y docker compose, que son los contenderos que les comente antes por medio de los siguientes comandos en bash : 


![image](https://github.com/user-attachments/assets/b4a37a66-c68c-440e-9b53-9a6bf2446856)



Al final de todo ya tendremos el hello world que nos verifica la correcta descarga del docker en nuestra maquina.

Ahora ya con el dockerfile descargado, y la imagen para debian, nos tendremos que mover a Visual Studio Code porque sera nuestra herramienta fundamental desde este paso hasta el final para poder tener nuestro tunel alojado en nuestro pc, entonces luego de que tengamos abierto Visual Studio Code vamos a trbajar desde su terminal, vamos a abrir una terminal y vamos a crear un entorno ideal para n8n por medio de los siguientes dos comandos : 

![image](https://github.com/user-attachments/assets/55d87455-2c8f-47b1-ac00-8273f5f03ce2)


Listo, teniendo el entorno de n8n en VS, ahora vamos a crear dos archivos cuyos nombres seran Dockerfile que tendra el siguiente script : 


![image](https://github.com/user-attachments/assets/7d4fad02-ea0a-49cc-89ff-a929ab18626e)



Y ahora otro archivo llamado docker-compose.yml, siendo ambos igual de imporantes, pero este segundo donde nos vamos a mover para continuar con el siguiente paso, el script de docker-compose.yml son los siguiente : 



![image](https://github.com/user-attachments/assets/7e4facee-d316-44cb-aa60-eaf250cd57da)



    

y finalizamos con el comando en el terminal : docker compose up --build (para asi ya inicar la descarga de todos los archivos de n8n, que tomaran su tiempo pero debe ser exitosa).



Listo, luego de estos pasos, cumpliriamos con exito la descarga de n8n que es como el primer paso para llegar al exito de nuestro agente IA, que pasa el link que nos redireccionara ser a un local.host5678/, ahora bien no esta del todo mal, por tood lo contrario es funcional, y tenemos ya toda la interfaz de n8n a nuestra disposicion, pero si nostros queremos llegar a conectar telegram con n8n en local no nos permite, por que ?, porque telegram nos obliga a que el dominio publico sea HTTPS, entonces la solucion mas optima, profesional y segura que podemos encontrar es utilizar ngrok que es una herramienta que nos permitira abrir un tunel HTTPS hasta nuestro local host, que ahora si nos permitira, conectar no solo telegram con libertad sino las otros triggers de n8n que nos lo impidan.

Ahora ya descargamos debian, docker y n8n, nuestro siguiente paso sera descargar e instalar ngrok en la maquina, y para esto utilizaremos el terminal de VS, asi como lo hicimos para poder descargar n8n, entonces utilizaremos los siguientes comandos : 


wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
tar -xvzf ngrok-v3-stable-linux-amd64.tgz
sudo mv ngrok /usr/local/bin/
ngrok version






Ahora, ya debemos tener descargado e instalado ngrok y para ello lo podemos comprobar poniendo ngrok version, nos debe dar como resultado ngrok version 3.22.1. Ahora ya luego de esto, tenemos que dirijirnos a la pagina de ngrok en google, crear un usuario, completas la autorizacion en dos pasos con microsoft, y luego de esto en la pagina nos arrojara lo siguiente : 

![image](https://github.com/user-attachments/assets/ee21567e-7712-4319-b908-46a32e63d34c)










