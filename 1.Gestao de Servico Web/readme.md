#### 1 - Enviar email para saber qual aplicação será usada e os recursos iniciais para o provisionamento da instância na cloud (vCPU,  RAM, armazenamento)

#### 2 - Criação da instância na cloud

#### 3 - Criar regras no firewall da cloud para restringir  o acesso público  a instância apenas nas portas 80 e 443

#### 4 - Criar uma vpn para acesso do ip público da empresa no projeto onde a instância foi criada

#### 5 - Deploy da instância na cloud
 - update dos repositórios


#### 6 - Instalar docker seus plugins adicionais
 - colocar para iniciar com o SO
 - configurar se necessário a rede default usada pelo docker no daemon.json
 - iniciar o serviço do docker

#### 7 - Criar docker compose  para o deploy da aplicacao
 - container do nginx
	portas usadas 80 e 443

  Obs: como sugestão serviços em container teria como usar traefik no lugar no nginx, ele é mais eficiente nesse casos pois renova os certificados automaticamente e não precisa reiniciar para inserir novos serviços
 - container do novo serviço coloque o nome da imagem a ser usada em image: e adicione o volume que será usado no container do novo-servico.

#### 8 - Instalar zabbix agent 2
 - colocar para iniciar com o  SO
 - configurar o envio para o zabbix server
 - iniciar o  zabbix agent
 - adicionar o usuário do zabbix ao grupo do docker para fazer o monitoramento dos containers

 #### 9 - Criar rotinas de Backup a depender do nível de prioridade da aplicação (backup full, incremental e snapshots)

 #### 10 - Documentação
  https://docs.google.com/document/d/1Q9Lg_NQVEo90XzOF3JlfGJTgVlG6Y56lbztANXAiizY/edit?usp=sharing
