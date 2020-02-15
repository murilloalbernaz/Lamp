# Lamp
Configuração Lamp
1. passo1: abre terminal coloca comando: sudo apt update(atualiza o indice do pacote local) 
2. passo2: coloca senha
3. passo3: coloca comando: sudo apt install apache2(instala apache pacote 2)
4. passo4: Verifique os ufw perfis de aplicativos disponíveis com comando: sudo ufw app list
5. passo5: ativar o perfil mais restritivo que ainda passopermitirá o tráfego que você configurou, permitindo o tráfego na porta 80 comando:sudo ufw allow 'Apache'
6. passo6: Verifique com o systemdsistema init para garantir que o serviço esteja sendo executado, digitando:sudo systemctl status apache2. ##(Apache instalado).
## Dicas:
### os principais arquivos vao estar em etc/apache2 onde vai encontrar: 
- ports.conf: serve para configurar as portas. 
- apache2.conf: que pode alterar o nome do servidor entre outras configurações gerais.
### pasta de conf-available que tem varios arquivos dentre os mais importantes o de segurança:  
- security.conf  
- charset: charset.conf. 
- ir a pasta /var e alterar as permissões da pasta www com: chmod -R 777 www
-voce irar ter que hosperdar paginas html dentro da pasta var/www/html.
## Configurando um host virtual no Apache
1. Crie um diretório para o host virtual. com o comando: sudo mkdir "Local da pasta que vai conter os html"
2.  Altere o dono e o grupo do diretório para que o usuário comum possa realizar alterações.(pegar pasta para o usuario: sudo chown –R $USER:$USER "caminho da pasta" e definindo permissões: sudo chmod –R 755 "caminho da pasta")
3. Voce pode criar um arquivo index.html dentro da pasta de diretorio do seu host virtual.(essa pagina index sera aberta automaticamente quando acessar o server, sem ter que colocar o nome do arquivo).
4. crie um arquivo de configuração do seu host dentro da pasta /etc/apache2/sites-avaible com a seguinte configurações:</br>
    <VirtualHost *:80>  
      ServerAdmin murilloalbernaz92@gmail.com  
      ServerName murillo.com  
      ServerAlias www.murillo.com  
      DocumentRoot /var/www/Teste  
      ErrorLog ${APACHE_LOG_DIR}/error.log  
      CustomLog ${APACHE_LOG_DIR}/acess.log combined  
    </VirtualHost>
5. Ative seu host atraves do comando: sudo a2ensite "nome do arquivo que criamos acima"
6. Como não temos um DNS configurado iremos contornar configurando o arquivo hosts na pasta /etc colocando para que a requisição do serve seja feita atraves do local host, comando: 192.168.10.44 thiagogmta.com(escrever dentro do arquivo mencionado e salvar).
7. Reinicie o Servidor apache atraves do comando: sudo service apache2 restart.
8. Se foi feito tudo corretamente seu servidor será reiniciado e você ja pode acessar a pagina index atraves do ServerName ou ServerAlias.

