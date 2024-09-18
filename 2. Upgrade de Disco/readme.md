Algumas perguntas teriam que ser respondidas antes de iniciar o upgrade do disco.

- quem ou qual equipe é responsável pela aplicação?

- quanto de espaço de disco ainda resta? E quanto tempo a aplicação leva para consumir o espaço restante?
      
       a partir da resposta teríamos um prazo definido

- quanto de espaço estão solicitando?

- tem backup do host sendo feito regularmente?

      faria um teste para ver em quanto tempo é possível subir o host a partir de um backup

## 

- a partir do prazo e tempo de restore definido, planejaria um dia, horário em que a aplicação ficasse ociosa, de preferência um final de semana ou feriado, onde teria um tempo extra para dar rollback de se necessário.

- primeiro faria um snapshot do VM

- Se o disco tá cheio vou adicionar um novo disco na VM para fazer uma dump do banco
## Backup do banco

listando discos

     fdisk -l
     fdisk /dev/sdb #criar um

adicionando uma nova partição

       Command (m for help): n
       Partition type
          p   primary (0 primary, 0 extended, 4 free)
          e   extended (container for logical partitions)
       Select (default p): p
       Partition number (1-4, default 1):
       First sector (2048-10485759, default 2048):
       Last sector, +sectors or +size{K,M,G,T,P} (2048-10485759, default 10485759):

       Created a new partition 1 of type 'Linux' and of size 5 GiB.

escrevendo alterações

       Command (m for help): w
       The partition table has been altered.
       Calling ioctl() to re-read partition table.
       Syncing disks.

formatando  o novo disco e criando um diretório para o dump do banco

    mkfs.xfs /dev/sdb1
    mkdir /backup

adicionar montagem no fstab

    UUID=d3964f9a-1fa4-4852-81eb-bc1adc777385 /backup       xfs     defaults        0 0

reiniciar o systemd e montando todos os pontos de montagem

    systemctl daemon-reload
    mount -a

dump

    mysqldump -u <usuario> -p<senha> mysql > /backup/mysql.sql

copio o dump para outro servidor

   scp /backup/mysql.sql  <usuario>@<ip>:<caminho>

## Upgrade do disco

- adicionei um novo disco na VM com o tamanho solicitado

com o novo disco listo ele no SO

    fdisk -l

verificar o ponto de montagem do banco


     df -h

verifico o vg

    vgdisplay db

adicionar novo disco ao vg

    vgextend db /dev/sdc

após adicionar no vg o tamanho do disco adicionado vai aparecer livre e para agregar ao lv do  banco

    lvextend -l +100%FREE -r /dev/db/banco

Com isso o tamanho do lv do nosso banco foi aumentado com o espaço que estava livre no volume group dele.
