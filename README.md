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
