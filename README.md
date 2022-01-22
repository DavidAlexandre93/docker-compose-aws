# docker-compose-aws
Rodando API NodeJS no servidor Docker(docker-compose) e AWS com CLI 


Após baixar o codigo utilize dos seguintes comandos para teste em sua máquina:
docker-compose up -d (rodar a aplicacao sem precisar ficar com o terminal aberto utilizando o -d)

Com o comando abaixo você pode checar a maquina no docker rodando a aplicação:
docker ps


Utilizando AWS cli para criar o ambiente na nuvem:
Com o comando abaixo você instala o awscli para Windows:
pip install awscli --user 

O comando abaixo fara a configuração da variavel de ambiente na sua maquina:
export PATH=~/.local/bin:$PATH 

Observação: Ter o Python instalado na sua máquina

Comando abaixo fara a o inicio da configuração de acesso ao console na AWS
aws configure 

Instalar o docker descktop: Onde fara o provisionamento na nuvem utilizando o docker-machine
https://docs.docker.com/desktop/windows/install/

Testar o docker-machine esta realmente instalado:
docker-machine -h

Comando abaixo ira criar uma instancia na AWS EC2 e em sequencia voce dara um nome:
docker-machine create --driver amazonec2 aws01

Os comando abaixo ira enviar toda sua estrutura da aplicação para a instancia criada:
docker-machine env aws01
eval $(docker-machine env aws01)

Observação: Configurar a liberação de porta 3000 na sua instancia EC2 em security group

O comando abaixo ira rodar a aplicação na AWS sem precisar ficar com o terminal aberto utilizando -d:
docker-compose up -d

Com o comando abaixo você irá rodar sua aplicação na AWS utilizando do -f traefik para realizar o trafico reverso de portas para utilizar das portas 80 e 8080 em inumeras aplicações:
docker-compose -f docker-compose.yml -f docker-production.yml up -d -- rodar a aplica com traefik substituindo as configuracoes de portas

Observação: Configurar a liberação de porta 80 e 8080 na sua instancia EC2 em security group

Com o comando abaixo você ira retornar para o Docker:
val $(docker-machine env -u) 
