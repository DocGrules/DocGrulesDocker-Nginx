# DocGrulesDocker-Nginx
Repositório para documentação e testes com docker e balanceamento com Nginx

Nginx vs Apache
Em termos de mundo real de casos de uso, uma das comparações mais comuns entre Apache e Nginx é a maneira em que cada servidor lida com solicitações de conteúdo estático e dinâmico.

O Apache é uma ferramenta muito completa para conteúdo dinâmico e o nginx possui uma performance incrível para conteúdo estático. Contudo, ambos possuem desvantagens: o Apache consome uma grande quantidade de memória e o Nginx não é bom o bastante, quando se trata de conteúdos dinâmicos.

Eles não são necessariamente "concorrentes", Apache e Nginx podem trabalhar juntos!

Deste modo, podemos combinar o melhor dos dois mundos, usando Nginx para servir conteúdo estático e o Apache para servir conteúdo dinâmico.

Instalando é configurando o Nginx com HTTPS
Versão estável Nginx - 1.8.0 - 2015-04-21

1. Atualizar o repositório do Linux:

sudo apt-get update

2. Instalar o Nginx:

sudo apt-get install nginx

3. Verificar se o serviço esta rodando:

sudo /etc/init.d/nginx status

Caso o serviço esteja parado, execute o comando abaixo:

sudo /etc/init.d/nginx start

4. Verificar se o serviço está ativo na porta padrão:

sudo netstat -pan | grep :80

Caso o serviço não esteja ativo na porta padrão, entre no arquivo de configuração e acrescente as linhas abaixo ou modifique a porta.

sudo vim /etc/nginx/sites-available/default

listen   80;
listen   [::]:80 default ipv6only=on;

5. Criar o certificado SSL:

$ sudo mkdir /etc/nginx/ssl
$ cd /etc/nginx/ssl
$ sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt

6. Configurar o Nginx para usar o SSL:

sudo vim /etc/nginx/sites-available/default
