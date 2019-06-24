Com base num código de um protocolo para transferência de arquivos, implemente um sistema para compartilhamento de arquivos, parecido com o Dropbox e Google Drive, que será o UTFBox.

  Observação 1: Deverá ser apresentado em sala na data de entrega.
  Observação 2: Implemente uma interface gráfica, tanto no servidor, quanto no cliente, para gerenciamento do sistema.
  Observação 3: Armazene configurações locais do cliente em arquivos .properties.

O sistema deverá ser baseado na arquitetura cliente/servidor e usar sockets TCP para trasferência de arquivos, sockets UDP para verificar a data da última atualização e socket Multicast para avisar vários processos ao mesmo tempo.

O servidor gerenciará contas de usuários. Cada usuário terá uma pasta no servidor para alocar os seus arquivos.
O servidor determinará uma pasta no disco, onde as pastas dos usuários ficarão. Ex: 


UTFBox/
├── Aluno01/
├── Aluno02/
├── Aluno03/
├── Aluno04/

O servidor deverá ter um controle de alterações dos arquivos armazenados nas pastas dos usuários (utilizar uma variável de controle pelo data da última modificação na pasta em milisegundos). Quando houver uma alteração, o servidor deve enviar uma mensagem MULTICAST para o grupo, informando em qual conta de usuário e a data que houve a última alteração.

O cliente terá, basicamente, a funcionalidade de baixar os arquivos do servidor e armazenar a última versão sincronizada (data em milisegundos do servidor). 

Configure no cliente um mecanismo de verificação de novos arquivos no servidor, ou seja, uma Thread que é executada de tempo em tempo, que envia uma mensagem ao servidor pedindo a data da última alteração. Se a data da última alteração no servidor for maior que a local, então o cliente deve baixar apenas os arquivos que foram alterados.

Por fim, entregue a descrição de funcionamento do sistema.

Faça uma concepção inicial do sistema
Projete a distribuição física da aplicação: represente a abstração do sistema quanto a sua arquitetura, pensando na divisão física (centralizada com 2, 3, 4, 5... divisões em camadas físicas, multidivididas ou híbridas)
Elabore um desenho, contendo os elementos envolvidos no sistema, clientes, servidores. Identifique o papel e cada elemento envolvido.
Especifique como a comunicação será feita entre os elementos: quais os tipos de sockets que podem ser utilizados?
Projete a distribuição lógica da aplicação: se for cliente/servidor, como estarão distribuídas a parte de interface. processamento e dados entre as camadas físicas de cliente e servidor.
Demonstre por meio de uma diagrama de sequência, como ocorre os processos entre o cliente e o servidor.
