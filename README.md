# Proyecto-Final-AI-AGENT
La finalidad de este documento es explicar el paso a paso de como se realizo el agente de IA, por medio de el software n8n en local, el cual presento ciertos retos a la hora de conectarse con el objetivo destino que era telegram, debido a que n8n al estar en local no recibia https, y por ende debiamos crear un tunel por medio de ngrok, pero todo esto se explicara mas adelante paso a paso : 

Paso #1 : 
Instalar n8n : en mi caso yo instale n8n por medio de debian con los docker que son los contenedores que nos daran multiples beneficios, que por mencionar algunos pueden ser la facilidad de instalacion y despliegue, nos simplifica mucho el proceso en vez de realizarlo por node.js, ademas nos ayuda con temas aislamiento y seguridad, etc.
El punto es que antes de instalar n8n, debemos tener tanto oracle virtual box que son las maquinas corriendo, y el git bash que es el simulador de la terminal de linux en windows, este utlimo sera fundamental porque las primeras acciones se realizaran desde alli.

Entonces suponiendo que tenemos descargado git bush, que es el icono que les muestro en la imagen, lo podemos buscar por medio de la venta de interaccion con windows.


![image](https://github.com/user-attachments/assets/b7d06a3e-b755-4ac7-b44e-e5476d5f6c6b)



Empezaremos por la descarga del docker y docker compose, que son los contenderos que les comente antes por medio de los siguientes comandos en bash : 


![image](https://github.com/user-attachments/assets/b4a37a66-c68c-440e-9b53-9a6bf2446856)


A


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






Ahora podemos empezar nuestro ultimo paso, que sera crear un archivo con el siguiente nombre : 

![image](https://github.com/user-attachments/assets/bc7cb59f-471e-473c-aba4-a29e2e094baa)


Junto con los dos que ya habiamos creado anteriormente que fueron Dockerfile y docker-compose.yml, ahora asi bien como estos dos, start.sh tambien tendra su propio script que sera de vital imporantcia, porque luego de este paso ya tendriamos nuestro tunel HTTPS hecho por medio de ngrok, ahora el script es : 


![image](https://github.com/user-attachments/assets/67b585b7-10c8-474a-b293-c1f6be233009)



Le damos permisos : 


![image](https://github.com/user-attachments/assets/c822c4fe-3e2b-4ffc-9e31-598e3221104d)




y finalmente con este comando construimos lo que sera el tunel HTTPS : 


![image](https://github.com/user-attachments/assets/3158bb41-ed22-4bbd-8956-7a4fa423d89a)


Ahora, ya como ultimo tendremos la siguiente direccion que nos llevara a una ventana en internet que nos permitira ya hacer todo lo que comente al principio, poder con tranquilidad enlazar n8n con telegram por medio de la api, y ya estaria, la direccion para dar un ejemplo seria como lo siguiente : 


![image](https://github.com/user-attachments/assets/ae587055-e3d1-469b-a48b-a190f13b92e0)



AHORA, como conclusion general este es un paso a paso un poco rapido pero con el fin de explicar el como descargar y hacer que n8n corra desde cualquier punto del mundo con HTTPS por medio de un tunel en ngrok, para conectar appi keys de telegram,discord, etc. 

La explicacion del paso a paso de la creacion del flujo de trabajo se realizara en la sustentacion del trabajo.

Para ir finalizando dare una breve explicacion del como entrar al bot luego de entender como se creo, para probar su funcionamiento en tiempo real : 

PASO A PASO : 

PASO # 1 : 

Descargar telegram si aun no esta instalado, de nuestro de nuestro dispositivo movil u ordenador.


![image](https://github.com/user-attachments/assets/0d46d605-fa2d-4807-be01-37c72db413bd)


Ahora luego de hacer la configuracion necesario con el numero de telefeno, etc, buscaremos en la pestaña buscar el nombre del bot que aparece acontinuacion : 

![image](https://github.com/user-attachments/assets/b378d33e-eb43-4df2-b201-632cbedb4fb1)

Como ultimo se nos abrira la pestaña luego de darle click y podremos preguntarle lo que sea, y si el bot no es capaz de responder debido a sus limitaciones tambien sera capaz de decirnos el por que no puede y eso seria todo, funciona como un chatbot, conectado a un IA que esta abiero a responder todas nuestras preguntas. 



creditos a : enguillem en youtube y a su pagina web, de gran ayuda para la realizacion de este proyecto.


























