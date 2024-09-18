- Criaria uma Rede com  Vlan's para criar uma isolamento por classe de dispositivo

- Criar escopo DHCP no windows server


       definir faixa de IP que será distribuída, máscara de sub-rede, gataway e DNS.

- Para o controle de acesso por MAC address utilizaremos **switchport port-security** nos switch para que cada porta aprenda dinamicamente um MAC e nao aceitei outro

todos os comandos usado em cada porta

       Switch(config)# interface f0/1
       Switch(config-if)# switchport mode access
       Switch(config-if)# switchport port-security
       Switch(config-if)# switchport port-security maximum 1
       Switch(config-if)# switchport port-security mac-address stick
       Switch(config-if)# switchport port-security violation shutdown


- Configurar entrada e saída da rede no firewall que se trafegue o necessário para o funcionamento do projeto, restringindo portas e protocolos.


- Habilitar SNMP nos switch para monitorar no zabbix server