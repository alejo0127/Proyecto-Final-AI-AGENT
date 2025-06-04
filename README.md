# Proyecto-Final-AI-AGENT
La finalidad de este documento es explicar el paso a paso de como se realizo el agente de IA, por medio de el software n8n en local, el cual presento ciertos retos a la hora de conectarse con el objetivo destino que era telegram, debido a que n8n al estar en local no recibia https, y por ende debiamos crear un tunel por medio de ngrok, pero todo esto se explicara mas adelante paso a paso : 

Paso #1 : 
Instalar n8n : en mi caso yo instale n8n por medio de debian con los docker que son los contenedores que nos daran multiples beneficios, que por mencionar algunos pueden ser la facilidad de instalacion y despliegue, nos simplifica mucho el proceso en vez de realizarlo por node.js, ademas nos ayuda con temas aislamiento y seguridad, etc.
El punto es que antes de instalar n8n, debemos tener tanto oracle virtual box que son las maquinas corriendo, y el git bash que es el simulador de la terminal de linux en windows, este utlimo sera fundamental porque las primeras acciones se realizaran desde alli.

Entonces suponiendo que tenemos descargado git bush.
![image](https://github.com/user-attachments/assets/b7d06a3e-b755-4ac7-b44e-e5476d5f6c6b)


Empezaremos por la descarga del docker y docker compose, que son los contenderos que les comente antes por medio de los siguientes comandos en bash : 

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker $USER
su - $USER
docker run hello-world


Al final de todo ya tendremos el hello world que nos verifica la correcta descarga del docker en nuestra maquina.

