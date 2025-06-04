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

Ahora ya con el dockerfile descargado, y la imagen para debian, nos tendremos que mover a Visual Studio Code porque sera nuestra herramienta fundamental desde este paso hasta el final para poder tener nuestro tunel alojado en nuestro pc, entonces luego de que tengamos abierto Visual Studio Code vamos a trbajar desde su terminal, vamos a abrir una terminal y vamos a crear un entorno ideal para n8n por medio de los siguientes dos comandos : 

mkdir -p ~/Docker/n8n-debian
cd ~/Docker/n8n-debian



Listo, teniendo el entorno de n8n en VS, ahora vamos a crear dos archivos cuyos nombres seran Dockerfile que tendra el siguiente script : 

FROM debian:12

RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    git \
    build-essential \
    python3 \
    libreoffice \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g n8n

ENV TZ=Europe/Madrid

CMD ["n8n"]




Y ahora otro archivo llamado docker-compose.yml, siendo ambos igual de imporantes, pero este segundo donde nos vamos a mover para continuar con el siguiente paso, el script de docker-compose.yml son los siguiente : 

version: '3.7'

services:
  n8n:
    build: .
    ports:
      - "5678:5678"
    environment:
      - GENERIC_TIMEZONE=Europe/Madrid
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=admin123
      - WEBHOOK_URL=${WEBHOOK_URL}
    volumes:
      - ./n8n-data:/home/node/.n8n






