#### 1 - Levantamento dos recursos inicias para o provisionamento da instancia na cloud (vCPU,  RAM, armazenamento)

#### 2 - Criacao da instancia na cloud

#### 3 - Criar regras no firewall da cloud para restringir  o acesso publico  a instancia apenas nas portas 80 e 443

#### 4 - Criar uma vpn para acesso do ip publico da empresa no projeto onde a instacia foi criada

#### 5 - Deploy da instancia na cloud
 - update dos resitorios 


#### 6 - Instalar docker seus plugins adicionais 
 - colocar para iniciar com o SO
 - configurar se necessario a rede default usada pelo docker no daemon.json
 - inciar o servico do docker

#### 7 - Instalar zabbix agent 2 
 - colocar para inciar com o  SO 
 - configuar o envio para o zabbix server
 - iniciar o  zabbix agent
 - adicionar o usuario do zabbix ao grupo do docker para fazer o monitoramento dos containers 

#### 8 - Criar docker compose  para o deploy da aplicacao 
 - container do nginx 
    portas usadas 80 e 443

  Obs: como sugestao servicos em container teria como usar traefik no lugar no nginx, ele é mais enficiente nesse casos pois renova os certificados automaticamente e nao precisa reiniar para incerir novos servicos 
 - container do novo serviço

 #### 9 - Criar rotinas de Backup a depender do nivel de prioridade da aplicacao (backup full, incremental e snapshots)

 #### 10 - Documentacao
  https://docs.google.com/document/d/1Q9Lg_NQVEo90XzOF3JlfGJTgVlG6Y56lbztANXAiizY/edit?usp=sharing