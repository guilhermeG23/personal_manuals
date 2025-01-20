## FreeBSD -> Resumo geral
### Aquele manual básico para firmar estudos

&nbsp;

___
&nbsp;


### Introdução

Manual simples e resumido sobre o FreeBSD feita com base na documentação do FreeBSD, dispónivel neste endereço: https://docs.freebsd.org/en/books/handbook/, forá demais pesquisas feitas com o intuito de melhorar este documento.

&nbsp;

___

&nbsp;

### P.S

Qualquer contribuição ao manual é bem vinda, se conter erros e demais coisas, fique a vontade para mexer, isso ajuda a comunidade como um todo.

&nbsp;

___

&nbsp;

### Sigla

BSD (Berkeley Software Distribution)

&nbsp;

___

&nbsp;

### Curiosidades interessantes 

* Totalmente free -> Licença BSD -> Sua licença é totalmente aberta, isso é, pode usar para qualquer coisa e pode ser trancado caso aquele que fez o fork queira.
* A primeira versão do FreeBSD foi a 1.0 em 1993, depois de problemas de código com a Novell, em 1994, grande parte do código interno foi alterado para de própria autoria do projeto, levando a versão 2.0 que possuia a versão Lite por não estar completo até data de lançamento.
* A equipe do BSD além de fechar a distribuição do BSD com uma fabricante de Discos CD em 1993, recebeu a oportunidade de possuir um computador com internet para a disponibilização do projeto.
* Possibilita o porte para o sistema ARM, exemplo o raspberry.
* O FreeBSD vem com o usuário ```root``` sem senha, já configurado no sistema, mesmo em modo live.

&nbsp;

___

&nbsp;

### Hardware

* Compátivel com processadores AMD64, X86 e ARM;
* Necessidade de mémória vária do uso do equipamento com a distro, porém é recomendo o minimo de 96MB de memória (pessoalmente, 1GB de memória é o suficiente para testes);
* Espaço de armazenamento mínimo é 2GB interno;

&nbsp;

___

&nbsp;

### Tipos de instaladores

* Installer Images -> Imagens de instaldores do FreeBSD.
* Virtual Machine Images -> Imagens prontas para máquinas virtuais.
* SD Card Images -> Imagens para cartão SD, possívelmente estruturas ARM em maioria.

&nbsp;

___

&nbsp;

### Dicas para criar uma mídia de boot 
###### P.S: Totalmente pessoal esse ponto

&nbsp;

Particularmente utilizo o Etcher Balena e o Rufus, ambos me atendendo super bem, para o caso de já estar utilizando alguma distro Linux, é possível usar o comando ```dd``` para gerar o disco bootavel externo ou mesmo o Etcher, se está utilizando o Windows, recomendo o uso do Rufus, segue abaixo os Links para o download dos arquivos e do sistema operacional:

* Rufus: https://rufus.ie/pt_BR/
* Etcher: https://www.balena.io/etcher/
* FreeBSD: https://www.freebsd.org/where/

Exemplo fornecido pelo próprio site do FreeBSD Documentation do uso do DD:

```
dd if=Image-FreeBSD-*.img of=/dev/da0 bs=1M conv=sync
```

###### P.S: Recomendo que esteja ciente dos trechos acima antes de realizar a criação (Para não perder tempo) da mídia, forá que se for instalar em alguma máquina, lembre-se de realizar o BK na mesma caso necessário.

&nbsp;

___

&nbsp;

### Sistemas de arquivos compátiveis

* MBR (Master boot record) -> 4 partições primárias máximas, porém pode se converter em partições lógicas, somente necessitando de uma partição primária para o sistema;
* GPT (GUID Partition Table / Tabela de partição GUID) -> Possui até 128 partições, eliminando a necessidade de partições lógicas como a MBR

&nbsp;

___

&nbsp;

### BIOS

Bom lembrar que existem dois tipos de BIOS utilizadas atualmente, a legancy e a UEFI, sendo a primeira a mais antiga e genérica e a segunda uma versão bolatada entre da Microsoft e a Intel que se espalhou para demais fabricantes e hardwares.

&nbsp;

___

&nbsp;

### Entrando no BSD

&nbsp;
___

&nbsp;


### Boot BSD

Iniciando a instalação do FreeBSD.

![bootbsd](img/bootbsd.png)
<center><small>Tela de boot de BSD, tanto para a instalação quando pós a instalação.</small></center>

&nbsp;

Quando carregada essa tela, ele tem um contador embaixo da tela, para parar esse contador é só pressionar qualquer tecla que não acione alguma função listada.

&nbsp;

Menu de boot:
* ```Multi user``` -> Iniciar sistema com capacidade de multiplos usuários;
    * Aperte ```1, B ou Enter```  para entrar neste modo;
    * Vale comentar que quando essa opção é escolhida, será feito o Boot do S.O já existente ou entra na tela de instalação;
        * Se quebrar o instalador, você entra em modo live, para quebrar o básico ```Ctrl+C```;
* ```Single``` ->  Modo de entrada de prompt para a recuperação do sistema, pelo menos segundo a página do BSD;
    * Aperte ```1 ou b``` para iniciar esse modo;
* ```Escape``` -> Abre um prompt limitado com somente alguns comandos, utilizado para reparo dentro do sistema;
    * Aperte ```3 ou Esc``` para entrar no modo;
* ```Reboot``` -> Reiniciar o sistema; 
* ```Cons``` -> Altera a constante do vídeo -> Tenho que entender melhor esse ainda;

&nbsp;

![#bootoptions](img/bootoptions.png)

&nbsp;

Menu de opções:
* ```Kernel``` -> Seleciona o kernel (nucleo) do sistema que será utilizado no boot do S.O (Sistema operacional);
* ```Boot Options``` -> Opções de boot, para acionar as ações neste menu é só clicar nos valores que a opção faz referência ou na tecla onde a letra está BOLD:
    * 1 -> Para retornar ao menu principal é só teclar o ```1 ou backspace```;
    * 2 -> Recarregue as opções padrões do sistema, aperte ```2 ou d```; 
    * 3 -> ACPI: Se o sistema travar, altere essa opção, é para a gestão de energia do sistema sobre o hardware, aperte ```3 ou A```;
    * 4 -> Safe mode: Se o sistema persistir em travar, mesmo com o ACPI off, coloque este em ```ON``` (Não há muitos detalhes no handbook);
    * 5 -> Single user: Limita a quantidade de usuários a um uúnico para o boot  
    * 6 -> Verbose só libera um maior detalhamento dos command-lines na ação do sistema, aperte o ```6 ou v```;

&nbsp;

___

&nbsp;

### Install BSD

&nbsp;

![freebsdinstaller](img/freebsdinstaller.png)
<center><small>Menu de instalação caso não tenha um BSD já firmado na máquina ou queria instalar um.</small></center>

&nbsp;

Quando usado o instalador do FreeBSD, ele te dá 3 opções, sendo essas:

* ```Install``` ->  Inicia o processo de instalação;
* ```Shell``` -> Abre um Shell para manipular o computador ou fazer operações pré-instalação;
* ```Live CD``` -> Aqui é o famoso modo live, onde você pode usar o sistema de forma experimental, já que o mesmo só está em memória;

&nbsp;

Uma dica do site do handbook BSD é apertar ```s``` nessa tela para abrir um prompt e dar o comando ```more /var/run/dmesg.boot``` para verificar o boot e o hardware detectado.

&nbsp;

___

&nbsp;

### Esc and Ctrl+C in install

&nbsp;

![ctrlcscriptbsd](img/ctrlcscriptbsd.png)
<center><small>Olha um Esc ou Ctrl+C em ação.</small></center>

&nbsp;

Use o usuário ```root``` para entrar no modo live, vale comentar tambem que "ás vezes" ele pede a senha, nesse caso é só dar outro ```Esc ou Ctrl+C``` e tentar entrar denovo como ```root```, possivelmente irá funcionar, já que forá feitos testes.



&nbsp;

___

&nbsp;

### Agora é o install mesmo

&nbsp;

O menu de instalação da distro freeBSD é chamado de bsdinstall, a primeira parte da instalação é a detecção do tipo de teclado utilizado, Ex:

![freebsdkeymap](img/freebsdkeymap.png)
<center><small>Seleção de teclado.</small></center>

&nbsp;

Aqui você seleciona o teclado para o sistema, neste caso, após a seleção, ele te leva ao ```test keymap``` para confirmar que o teclado está correto.

&nbsp;

###### P.S: Selecione o ```Brazilian (withoud accent keys)``` pois funcionou maioria do meu teclado... bem, depois que ler mais um pouco, mais prafrente eu faço funcionar o ```Alt GR + Q``` para gerar o ```\```.

&nbsp;

Bem, depois de escolher e testar o teclado, caso tenha selecionado o ```default```, será o ``` americado ISO-8859-1```, será a tela de configuração do **hostname**, ai você pode colocar o nome que quiser para identificação do host na sua rede, Ex:

![hostnamebsd](img/hostnamebsd.png)
<center><small>Olha o hostname selecionado... eu sei, nada criativo, más bem, são testes mesmo, então tanto faz.</small></center>

&nbsp;

Agora a coisa fica mais interessante, pois nessa tela temos as opções de instações de pacotes opcionais para o sistema.

![pacotesbsd](img/pacotesbsd.png)
<center><small>Escolha sabiamente</small></center>

&nbsp;

Os pacotes listaos são:
* ```base``` -> Ferramentas básicas de sistema como ```CAT, LS, DIR``` e demais;
* ```Kernel``` -> Kernel e módulos com símbolos de depuração ativados;
* ```Lib32-dpg``` -> Bibliotecas para funcionamento de aplicativos 32bits em sistema 64 com símbolos de depuração ativados;
* ```Lib32``` -> O mesmo que o acima, porém sem a parte de símbolos;
* ```Ports``` -> Coleção de Ports BSD para automatizar download, compilação e instalação de pacotes terceiros, só lembrando que o Ports não verifica espaço em disco durante a instalação, isso é, o mesmo ocupa 500Mb a mais durante a instalação, lembre-se disso caso selecionar essa opção e do seu armazenamento.
* ```src``` -> Código-fonte do BSD para o Kernel e usuário, utilizado por alguns Ports e para o próprio desenvolvimento do BSD, lembrando, ele é utilizado para desenvolvimento e requer 1GB em armazenamento, forá mais 5GB para a recompilação de todo o S.O BSD; 
* ```test``` -> pacotes de teste do BSD;

&nbsp;

Bem, após a seleção dos pacotes, você precisa fazer o download deles para instalar caso tenha optado por manter atualizado ou se você pegou uma versão CD de boot, de qualquer forma será apresentada essa tela.

![redebsd](img/redebsd.png)
<center><small>Olha o aviso de instalação de pacotes via rede.</small></center>

&nbsp;

Ao que se segue agora, é a preferência de rede do BSD para a instalação de pacotes via rede, segue abaixo a configuração da placa de rede para o download dos pacotes.

&nbsp;

Há, existe uma parte do handbook sobre configuração da rede do BSD, porém, durante esse manual, BSD foi instalado em um virtualbox e está usando uma placa de rede NAT, então deixei a config mais simples... 

&nbsp;

##### P.S: volto a melhorar essa parte depois com mais testes.

&nbsp;

![placaderedebsd](img/placaderedebsd.png)
<center><small>Selecionar placa de rede.</small></center>
&nbsp;

![ipv4bsd](img/ipv4bsd.png)
<center><small>Decido ou não aceitar o uso do IPV4, esse eu marquei que sim.</small></center>
&nbsp;

![ipv4dhcpbsd](img/ipv4dhcpbsd.png)
<center><small>Aqui eu falo que se quero ele estático ou DHCP... Fui no DHCP para economizar tempo.</small></center>
&nbsp;

![ipv6bsd](img/ipv6bsd.png)
<center><small>Decido ou não aceitar o uso do IPV6, esse eu marquei que não.</small></center>
&nbsp;

![dnsbsd](img/dnsbsd.png)
<center><small>Configuro o DNS que o host vai usar.</small></center>
&nbsp;

![mirrorbsd](img/mirrorbsd.png)
<center><small>Aqui é de onde ele vai baixar os pacotes.</small></center>
&nbsp;

Ufa.... com isso é o fim da configuração do download dos pacotes, há, lembrando, isso aqui é mais para quem quer deixar os pacotes atualizados ou baixou uma versão mais "lite" do FreeBSD por assim dizer.

&nbsp;

Ai, agora é hora de rolo, hora de otimizar ou só taca no automatico e vai.

![formadeinstalarbsd](img/formadeinstalarbsd.png)
<center><small>Aqui é de onde ele vai baixar os pacotes.</small></center>
&nbsp;

Aqui é a configuração de forma de instalação do BSD no armazenamento interno, segue abaixo os tipos de instalação:

* ```Auto``` -> Aqui é a formatação automático via ```UFS``` do sistema de arquivos;
* ```Manual``` -> Aqui é a criação manual das partições para a instalação do S.O;
* ```Shell``` -> Esse abre um Shell para a criação de partições utilizando as ferramentas de sistema, Ex: ```Gpart, Fdisk, BsdLabel``` e outros;
* ```Auto``` -> (ZFS)O particionamento cria um sistema root-on-ZFS com suporte de criptografia GELI opcional para ambientes de inicialização... ***(Esse aqui eu não entendo bem... tenho que dar uma olhada mais fundo)***; 

&nbsp;

___
***Aqui sinceramento eu pulei os demais métodos e fui direto para o modelo Auto de instalação, neste eu selecionei o sistema de arquivos MRB... bem, eu volto mais tarde para tentar realizar a instalação nestes modelos.***
___


&nbsp;

Abaixo segue a instalação dos pacotes opcionais e do sistema.


###### P.S: Antes de continuar, deixo avisado para eu não ser julgado, somente é por convivencia com discos HD..., Não tenho contato, nem mesmo conheco alguém do ramo, más não importa para quem tu reza ou se nem reza, tenha um SSD no seu hardware para ganhar tempo de vida.

&nbsp;

![instalandopacotesbsd](img/instalandopacotesbsd.png)
<center><small>Aqui é o download dos pacotes externos que foram selecionados no opcionais.</small></center>

&nbsp;

Primeiramente... Depois de você ter criado a partição, agora elas seram utilizadas primeiramente para a criação do sistema de arquivos, em seguida o download dos pacotes opcionais, sendo que, se a instalação for do tipo DVD, todos os opcionais já vão estar dentro do disco, se não, exemplos os ```bootonly media, CD, mini memstick e demais```, ele precisa fazer o download dos pacotes, por isso a seleção do Mirror antecipadamente foi útil.... OK, em resumo sobre isso, ele confere a lista selecionada, baixa os pacotes opcionais, confere se os mesmos não estam corrompidos e seguidamente os passa ao instalador do sistema.

&nbsp;

![instalandoosistemabsd](img/instalandoosistemabsd.png)
<center><small>Aqui é a instalação dos pacotes do sistema em si.</small></center>

&nbsp;

Como dito, os pacotes opcionais são obtidos e deixados para serem instalados por esse processo de extração.

###### P.S: Como comentando no handbook, o tempo de instalação vária muito, quantidade de pacotes, velocidade de internet se você precisar dela para baixar pacotes, o hardware em si, como quantidade de memória, CPU e principalmente o armazenamento

&nbsp;

Bem, bem, depois do processo de extração, será requisitada a criação de senha para o literal usuário mais importante do sistema, o ```root```, neste caso, peço só que lembre da senha... sério, se não depois passa um apertado para pegar a senha devolta ou descobrir a mesma.

&nbsp;

![timezonebsd](img/timezonebsd.png)
<center><small>Aqui você seleciona o time-zone do sistema, no caso, aqui foi de américas, Brasil e agora a seleção do estado.</small></center>

&nbsp;

Depois de selecionar o time-zone, vem uma tela para configurar os horários locais... ai vai de você no caso, só acertar o relógio ou selecionar o ```skip```.

###### P.S: Recomendo configurar corretamente o horário para não ter problemas a acesso de pacotes externos.

&nbsp;

![servicesbsd](img/servicesbsd.png)
<center><small>Esses são os serviços default da instalação do BSD... aqui tem que escolher oque será iniciado junto ao sistema.</small></center>

&nbsp;

Depois de tudo isso, vem agora você tem que selecionar os serviços que serão iniciados durante o boot, todos esses serviços são opcionais, não necessários para o funcionamento do sistema, esse é outro ponto para deixar no automático ou personalizar, ai vai da necessidade de cada um.

&nbsp;

Más bem, segue abaixo um pouco de detalhamento dos serviços:

* ```local``` -> Ative o serviço de DNS local, vale comentar que esse é somente para o host e não valido a toda a rede, caso seja esse o seu objetivo, é recomendado instalar o resolvedor DNS, no caso, esse: ```dns/unbound```.
* ```sshd``` -> Habilita o SSH (daemon Secure Shell), que possibilita um acesso remoto criptografado ao host.
* ```moused``` -> Serviço de mouse para o console do sistema;
* ```ntpdate``` -> Habilite um serviço de NTP para sincronizar o relógio do host durante o boot.
* ```ntpd``` -> Habilita o NTP para buscar de servidores do mesmo para a sincronização do relógio do host;
* ```powerd``` -> Serviço para controle de energia do hardware caso o mesmo permita ou tenha esse controle, serve para ajustar frequência do CPU e demais outras peças;
* ```dumpdev``` -> Habilita os despejos de memória, isso é, limpar a memória de coisas que deram problemas e demais;

&nbsp;

![segurancabsd](img/segurancabsd.png)
<center><small>Esses são os serviços default da instalação do BSD... aqui tem que escolher oque será iniciado junto ao sistema.</small></center>

&nbsp;

Ok, depois de selecionar os serviços, ta na hora de escolher o sistema de segurança do BSD, que comecem os jogos:

* ```hide_uids``` -> Oculta UID de processos em execução para usuários sem permissão;
* ```hide_gids``` -> Oculta processos em execução pertencendos a outros grupos;
* ```hide_jail``` -> Oculta processos em execução nas ```jail's``` para usuários sem permissão;
* ```read_msgbuf``` -> Retira a permissão de leitura do buffer de mensagem do kernel para usuários sem privilégios, basicamente desativa o dmesg para alguns usuários e tira a permissão de leitura dos arquivos que contém essas infos;
* ```proc_debug``` -> Desabilitar possibilidade de depuração dos processo para usuários sem privilégios, basicamente quase todos os processo do sistema e demais linguagens ficam desabilitados o depurador para esse usuário;
* ```random_pid``` -> Randomize o PID de processos recém-criados.
* ```clear_tmp``` -> Limpa o diretorio ```/tmp``` quando o sistema da boot;
* ```disable_syslogd``` -> Desative a abertura do soquete da rede syslogd, claro, existe mais detalhes, porém tem que confirmar na configuração personalizada do BSD sobre o serviço;
* ```disable_sendmail``` -> Desative o agente de transporte de correio sendmail;
* ```secure_console``` -> Quando esta opção é ativada, o prompt solicita a senha de ```root``` para entrar no modo de usuário único.
* ```disable_ddtrace``` -> O DTrace pode ser executado de forma destrutiva para o kernel em execução, para mais detalhes, tem que conferir a funcionabilidade do programa e seus parâmetros.

&nbsp;

Ótimo, depois de todos esses passos, chegamos ao final, que é adicionar um usuário ao BSD sem ser o ```root```, para isso, selecione o ```yes``` na tela de adicionar mais um usuário ao sistema, se selecionar o ```no```, pronto, o sistema irá terminar o processo de instalação, aplicar as alterações e fechou, um BSD totalmente instalado.

Agora, esse é um usuário já criado no BSD, Ex:

![usuariobsd](img/usuariobsd.png)
<center><small>Esse usuário é bem default, sem qualquer customização, forá a senha.</small></center>

&nbsp;

As informações do usuário são:

* ```Username``` -> Nome do usuário, boas práticas para isso são:
    * Sem espaçamento;
    * Sem caracteres especiáis;
    * O sistema é case-sensitive, então o mesmo diferença de maiúsculo de minúsculo;
    * Todo nome de usuário deve ser único;
* ```Full name``` -> Nome completo do usuário, aqui é um campo de descrição, então pode digitar sem medo dos descritos acima;
* ```Uid``` -> ID do usuário e esse é normamente deixado por conta do sistema, a mesmo que você saiba quais ID's ainda estão disponíveis;
* ```Login group``` -> O grupo que o usuário irá pertencer e aqui também é normal deixar em branco, poiso grupo se torna o nome do usuário.
* ```Invite user into other groups?``` -> Grupos adicionais, isso é, grupos a qual o usuário pode pertencer, como grupos que tem permissões especiais e demais;
    * Se o usuário precisar de ```root```, digite: ```wheel``` neste campo;
* ```Login class``` -> Normalmente deixado em branco para o padrão ***(Sinceramente não sei nem oq é, tenho que ver isso depois)***;
* ```Shell```-> Seleciona qual shell o usuário utilizará por padrão;
* ```Home directory``` -> O diretório do ```\home``` do usuário, normalmente, o default já preenche corretamente;
* ```Home directory permissions``` -> Permissões no diretório ```\home``` do usuário.
* ```Use password-based authentication?``` -> Aqui pergunta se o usuário quer usar o password para entrar no usuário;
* ```Use an empty password?``` -> Aqui decide se o usuário vai usar uma senha ou se será um campo em branco, é melhor colocar uma, afinal, você não vai usar um BSD para acessar email do google né;
* ```Use a random password?``` -> Favor usar o ```no``` aqui, se gerar uma senha aleatória e você esquecer... bem, espero que saiba onde fica armazenado as senhas do sistema;
* ```Enter password``` -> Aqui você digita uma senha para o usuário;
* ```Enter password again``` -> Agora você repete aquela mesma senha aqui para efetivar a senha do usuário;
* ```Lock out the account after creation?``` -> Por default é um ````no```, pois ai o usuário fica trancado e não pode acessar;


&nbsp;

Agora, depois de tudo isso, é só dar um ```OK``` para finalizar a criação do usuário... Ufa, cabou , bem, nem tanto, depois que você terminar de criar o usuário aparecerá uma pergunta para adicionar um novo outro usuário ou não, nesse caso, ai vai de sua vontade ou necessidade.

&nbsp;

Por fim, agora que foi feito tudo o de neessário, aparecerá essa tela:

![teladetodasopcoesbsd](img/teladetodasopcoesbsd.png)
<center><small>Tela para efetivar tudo e sair, ou alterar alguma coisa antes de aplicar.</small></center>

&nbsp;

Como dito na descrição da imagem, aqui é possível alterar as configurações antes de aplicar e finalizar totalmente a instalação do sistema.

Com isso está terminado a parte da instalação do sistema BSD, para finalizar, aperte a opção do ```EXIT``` e pronto... más e os demais? ... Bem, eles já foram vistos de forma seguida, más para deixar de forma mais didática, eles são:

* ```Add User``` -> Adicionar usuários.
* ```Root Password``` -> Definição da senha do ```root```.
* ```Hostname``` -> Definir o nome do host.
* ```Network``` -> Configurações da's interface's de Rede .
* ```Services``` -> Ativação de serviços .
* ```System Hardening``` -> Opções de segurança de proteção .
* ```Time Zone```-> Definição do fuso horário .
* ```Handbook``` -> Baixe e instale o Manual do FreeBSD.

&nbsp;

___

&nbsp;

### Problemas durante a instalação

Segundo o pessoal do handbook e como comentado anteriormente, o BSD vem com o ACPI ligado, isso é, gerenciamento de energia inteligente ao hardware, porém tem BIOS ou Firmware's de placas mãe's que ainda são incompátiveis ou apresentão problemas, dessa forma é recomendado fazer:

* Desabilitar nas opçõe savançadas durante a instalação;
* Digitar em modo shell o comando: ```set hint.acpi.0.disabled="1"``` para desabilitar a opção;
* Ou por fim, alterar o arquivo ```/boot/loader.conf``` adicionando a linha ```hint.acpi.0.disabled="1"``` ao mesmo e recarregando o arquivo no sistema de instalação;

&nbsp;

___

&nbsp;

### Primeiro login

&nbsp;

```
FreeBSD/amd64 (teste_freebsd) (ttyv0)

login:
```

&nbsp;

Depois de toda a tela de verbose após iniciar o sistema que é exatamente igual a tela de bootinstall, o sistema para na tela de login entrando as informações de:

* Versão: amd64;
* Hostname: teste_freebsd;
* Console virtual: ttyv0;

&nbsp;


O login é a entrada de usuários que foram registrados durante a instalação, com exemplos desses podemos logar no ```root``` e no ```teste``` criados durante a instalação da versão em uso.

Após o login, uma mensagem será printada no terminal console, sendo essa o ```MOTD```, que entrada várias informações, Ex:

![modtbsd](img/modtbsd.png)
<center><small>MOTD BSD após o login no usuário root.</small></center>

Para editar esse ```MODT```, é necessário ter as permissões necessárias para editar o arquivo que fica no ```/etc/motd```.

&nbsp;

___

&nbsp;

### Consoles virtuais

&nbsp;

Isso é algo comum, normalmente só utilizamos um único terminal por ver, isso é, um único console por ver, cada console é nomeado de ```ttyv*```, indo de 0 a 8, podendo ser alterado com o uso dos comandos ```Alt+F*``` de 1 a 8.

&nbsp;

O local onde fica as configurações de consoles virtuais é no ```/etc/ttys```, aproveitando, é bom orientar que:

* Não comente a linha ```ttyv0```, afinal é o default;
* O ```ttyv8``` é normalmente utilizado pelos programas que geram interfaces gráficas, no caso o Xorg.


Veja a imagem abaixo para você ter uma idéia da configuração dos consoles virtuais.

&nbsp;

![ttysbsd](img/ttysbsd.png)
<center><small>Configuração dos TTYSV do BSD.</small></center>

&nbsp;

___

&nbsp;

### Boot single user

&nbsp;

Lembra que foi comentado sobre o boot de usuário unico era para reparar o sistema operacional, sabe, lá no inicio.... bem, é isso mesmo, más olha a sacada, dentro desse modo, o unico usuário disponivel é o ```root``` e sem senha... sentiu o medo né, tipo e um acesso remoto... sem senha com o usuário com maior permissão dentro do sistema... vai dar ruim né!? Nops, olha o pq.

Esse modo abre o terminal com o usuário ```root``` sem senha, porém bloqueia acesso externo a rede, necessitando de interação física ao equipamento para o exercicio da tarefa, sendo assim, você pode manipular o sistema totalmente, porém tem que ter acesso ao mesmo, forá que esse modo além de ser usado para reparação, é usado também para redefinir a senha do ```root``` caso a mesmo tenha sido perdida.

Para ficar ciente, quando você faz um boot de single user, os ttyv são a base para o acesso, seguindo a mesma regra, onde o default é o ```ttyv0```, o fato de você acessar o mesmo sem precisar da senha é porque ele está com o ```secure``` afirmado no fim da linha, isso é, se estiver ```insecure```, mesmo em modo single user, será necessário colocar a senha do usuário ```root``` para ter acesso e isso leva o perigo que, se você esta entrando nesse modo para recuperar a senha de root perdido... bem, vai dar não, entao sempre tenha cuidado e zelo pelas senhas utilizadas nos sistemas e aplicações.

&nbsp;

___

&nbsp;

### Configuração de vídeo


&nbsp;

___

&nbsp;

### Contas e usuários

Primeiramente, existem que tipos de contas dentro do sistema BSD? Segue abaixo uma lista dos tipos:

* ```daemon```;
* ```operator```;
* ```bind```;
* ```news```;
* ```www```;
* ```nobody```;

Forá demais outras, os litados são um exemplo, cada tipo de conta tem um limite de agir dentro do sistema, sendo assim, cada um tem um nível de prioridade, vamos supor que o ```nobody``` é o tipo predominante dentro do sistema e esse grupo for comprometido de alguma forma, bem, isso vai gerar uma grande perda, já que todos os arquivo deste mesmo tipo estão igualmente comprometidos.

Vale tambem comentar que a ```nobody``` é a conta genérica do sistema e que não possiu privilégios.

&nbsp;

___


&nbsp;

### Usuário típico

&nbsp;

Cada conta dentro de um S.O tem suas caracteristicas, sendo assim, o mesmo vale para o BSD, segue abaixo as caracteristicas de um usuário do sistema:

&nbsp;

* ```Nome do usuário``` -> Nome único de acesso a uma conta dentro do S.O, existem muitas padronizações deste, sendo essas:
    * Usuário em letras maiusculas;
    * Primeira letra do primeiro nome e usar o segundo nome para completar o restante dos caracteres;
    * Limitar a quantidade de caracteres a 8;
    * Além de outras demais...
* ```Senha``` -> Aqui é só colocar uma senha para proteger seu usuário;
* ```ID (UID)``` -> Número único de identificação do usuário;
    * Recomendado usar um ```UID``` menor que ```65535``` para não haver conflitos com softwares;
* ```GID``` -> ID do grupo, o BSD usa esse método em vez do ```UID``` para diminuir significativamente o tamanho dos arquivos de configuração das aplicações;
    * Recomendado usar um ```GID``` menor que ```65535``` para não haver conflitos com softwares;
    * Usuários podem pertencer a mais de um grupo, isso é, o grupo que libera acessos as aplicações, assim se um usuário pertencer a determinado grupo, ele terá direito de usar as mesmas aplicações;

&nbsp;

Como comentado dentro do handbook, os usuários BSD não tem tempo de expiração, isso é, sua vida útil é ilimitada, necessitando de um utilitário para dar fim a mesma ou alguma configuração personalizada que realize a ação.

&nbsp;

___

&nbsp;

### Cuidados com o ROOT!!!!

&nbsp;

Acho que já deu para entender que o ```root``` é literalmente o cara que manda em tudo no S.O... sim, ele é o usuário com acesso irestrito a todo o S.O, por isso deve ser protegido a 7 chaves e não deve ser usado de forma leviana, isso é, não trabalhe como ```root``` se não for necessário.

&nbsp;

Para que você fique ciente, uma forma fácil de saber se você tá em ```root``` é:

&nbsp;

* Diferenças visuais do shell como:
    * \# -> Usuário root tem esse símbolo no shell;
    * $ -> Usuário comum tem esse símbolo no shell;
    * O usuário é sempre mostrado no shell na command line, Ex: ```teste@hostname:diretorio$```
* Por comandos, pode se usar o:
    * ```whoami``` -> Utilitário que fala qual é o usuário em uso no momento;
    * ```cd ~``` + ```pwd``` -> Isso é, o ```cd``` vai mandar seu command line para o diretório do usuário atual e ```pwd``` é um utilitário que mostra em qual diretório você está no sistema, no caso, o diretório do seu usuário;

&nbsp;

Vale comentar que o usuário pode se tornar ```root``` utilizando o comando ```su```, más para isso, existem duas etapas, sendo essas:

&nbsp;

* O usuário que vai receber permissão ```root``` tem que estar no grupo ```wheel``` como já comentado uma vez;
* Saber a senha do usuário ```root``` para obter seus privilégios;

&nbsp;

Um exemplo de como liberar acesso ao ```root``` a um usuário comum, lembrando que isso será comentando com mais detalhes a frente:

&nbsp;

![adicionandoowheelbsd](img/adicionandoowheelbsd.png)
<center><small>Adicionando o wheel a um usuário comum.</small></center>

&nbsp;

![setornandorootbsd](img/setornandorootbsd.png)
<center><small>Se tornando root via usuário comum que está no grupo wheel.</small></center>

&nbsp;

Há, o ```su -``` é só entrar no usuário com maior permissão e no caso, com o ```-```, é entrar já na estrutura de diretório do usuário alvo.

&nbsp;

___

&nbsp;

### Gerenciamento de usuários

&nbsp;

Sabe o mais pra frente que eu falei... bem, é agora, sendo essas as ferramentas para gerenciamento dos usuários do sistema:

* ```adduser``` -> Adicionar usuários;
* ```rmuser``` -> Deletar usuários;
* ```chpass``` -> Alterar informações do usuário;
* ```passwd``` -> Alterar a senhas dos usuários;
* ```pw``` -> Utilitário para modificar totalmente o usuário;

&nbsp;

#### ***ADDUSER***

A ferramenta é utilizada e recomenda para adicionar novos usuários dentro do sistema, para fazer isso, primeiramente você precisa de acesso de superusuário, o ```root``` para ser mais especifico ou qualquer usuário com igual poder..., más certo, oqê acontece quando vamos adicionar um novo usuário? Isso aqui:

&nbsp;

* É criado um diretório no ```/home``` que irá pertencer ao novo usuário;
* É atualizado o ```/etc/passwd``` para o novo usuário;
* É atualizado e alterado os grupos no arquivo ```/etc/group```;
* O diretório do novo usuário irá receber as configurações padrão que vem do ```/usr/share/skel```;

&nbsp;

É valido comentar que, a tela do ```adduser``` é exatamente a mesma de quando criado um usuário no install do BSD.

Se não acredita em mim, veja o ```adduser pastel``` abaixo:

&nbsp;

![addpasteluserbsd](img/addpasteluserbsd.png)
<center><small>Fiquei com fome nas print...</small></center>

&nbsp;

###### P.S: Acho que se já notou, más quando é digitado senhas, para entrar, criar ou modificar alguma coisa ou mesmo o usuário, ela não aparece na tela... então, cuidado com isso quando criar o usuário, se você tiver o root, até se salva, más mesmo assim, é um transtorno a mais.

&nbsp;

Há, por fim... pra você que ficou pensando "E se eu adicionar um usuário com um nome que já existe, afinal, o que conta de verdade é o UID e o GID né?"... Bem, não é assim támbem, como vai de exemplo na imagem abaixo, o nome influencia na criação do diretorio e demais, más foi mais por curiosidade mesmo, afinal o handbook não comentou sobre esse ponto ***(Mesmo que pareça óbvio que iria dar errado)***.

&nbsp;

![erroradduserbsd](img/erroradduserbsd.png)
<center><small>Erro ao adicionar novos usuários.</small></center>

&nbsp;

___

&nbsp;

#### ***RMUSER***


&nbsp;

Já falamos sobre adicionar, agora vamos ao deletar, lembrando que para você criar, eliminar ou qualquer coisa, você precisa ter as permissões necessárias, isso é, vai fazer em ```root``` ou qualquer usuário com poderes iguais, más bem, segue abaixo as ações do ```rmuser```:

* Remove as configurações de crontab do usuário -> Caso existir;
* Finaliza todos os ```jobs``` em execução do usuário;
* Mata todos os processos do usuário;
* Remove as configurações do ```/var/mail``` do usuário;
* Elimina todos os arquivos no ```/tmp``` pertencentes ao determinado usuário;
* Elimina o usuário dos grupos a quais ele pertence, isso no arquivo ```/etc/group```.
* Se um grupo não tiver nenhum usuário e ele tiver o mesmo nome do usuário, o grupo é eliminado;
* O diretório no ```/home``` do usuário não é eliminado sumáriamente, ele precisa ser requisitado no momento do rm;

&nbsp;

Bem, como eu fiquei com fome depois do usuário pastel, melhor eliminar ele, só pra eu esquecer do pastel e me concentrar aqui.

&nbsp;

![rmpasteluserbsd](img/rmpasteluserbsd.png)
<center><small>Lá se foi o pastel.... ainda com fome.</small></center>

&nbsp;

Ok, chega de piadas neste ponto, na imagem, foi expresso meu desejo por eliminar o usuário e eliminar o diretório no ```/home``` deste usuário, com isso, o usuário está totalmente eliminado do sistema, as únicas provas do mesmo serão arquivos pertencentes a ele forá do ```/home``` ou logs por exemplo.



&nbsp;

___

&nbsp;

#### ***CHPASS***

&nbsp;

Esse é um utilitário que pode ser utilizado pelo próprio usuário sem a permissão ```root``` ou qualquer superusuário, a função deste comando é alterar a base de dados do determinado usuário alvo, podendo ser feita de duas formas:

&nbsp;

* ```chpass``` -> Isso vai abrir um editor num arquivo contendo informações do usuário atual;
* ```chpass <usuario>``` -> Isso vai abrir um editor num arquivo contendo informações do usuário alvo e esse precisa do superusuário, afinal, você está alterando informações de um terceiro;

&nbsp;

Más de forma mais simples de se entender, o ```chpass``` abre um editor de texto para você alterar o banco de dados do usuário de forma que o mesmo fique correto ou que algo sejá alterado, lembrando que há a necessidade de recarregar essas informações.

&nbsp;

![chpasstestebsd](img/chpasstestebsd.png)
<center><small>Lá se foi o pastel.... ainda com fome.</small></center>

&nbsp;

___

&nbsp;

#### ***PASSWD***

&nbsp;

Comemorei cedo demais e aparece outro que não precisa de superusuário para ser acionado, neste caso, o ```passwd``` é para alterar o campo da senha do usuário atual ou alvo, sabe aquele campo que se viu na imagem acima, o ```Password```, é exatamente isso que o ```passwd``` vai mexer, além de o mesmo já deixar a senha já cifrada.

&nbsp;

Assim como o ```chpass```, o ```passwd``` tem duas formas de funcionar, a primeira é pelo próprio usuário, onde o sistema requisita a senha antiga para alterar há uma nova e a segunda é utilizando o comando e direcionando a um determinado usuário, onde lá, não será requisitado a senha antiga e sim, somente colocar a nova e finalizar o problema, segue imagens sobre as ocorrências abaixo:

&nbsp;

![passwdbsd1](img/passwdbsd1.png)
<center><small>Aqui foi feito pelo próprio usuário, onde é necessário digitar a senha antiga para conseguir alterar para uma nova.</small></center>

&nbsp;

![passwdbsd2](img/passwdbsd2.png)
<center><small>Aqui foi feito pelo próprio superusuário, onde ele simplesmente falou, coloque a nova senha, sem a necessidade da senha antiga já existente ao usuário.</small></center>


&nbsp;

###### P.S: É com esse comando que você concerta o problema sobre usar senha randomica no usuário, esquecer a senha de demais usuários ou alterar... lembrando, nunca esqueça a senha do root, senão é entrar em modo recuperação e ir ajustar como usuário único e torcer para a sessão ser segura. 


&nbsp;

___

&nbsp;

### Gerenciador de grupos via PW

&nbsp;

Um grupo é o conjunto de um ou mais integrantes que podem realizar determinada tarefa com base na permissão desse grupo, esses grupos ficam listados no arquivo ```/etc/group``` do BSD.

&nbsp;

Se o usuário tem o ```UID```,  o grupo tem o ```GID```, que consiste do nome e identificação, para a realização de processos do sistema, se é usado tanto o ```UID``` para saber quem está realizando tal coisa e o ```GID```, que confirma se um usuário pode realizar a determinada ação corretamente.

&nbsp;

Exemplos de uso do ```PW``` na realidade:

&nbsp;

![permissionamentopwbsd](img/permissionamentopwbsd.png)
<center><small>Aqui um grupo é criado, mostrado suas informações gerais e um usuário já é integrado neste grupo.</small></center>

&nbsp;

O uso da opção ```-M``` é para substituir membros já existentes ou adicionar membros a grupos vazios, isso é, se esse cara for usado, todos os antigos usuários que pertenciam a este grupo seram retirados e somente será colocado o novo usuário, Ex:

&nbsp;

![groupmodm1bsd](img/groupmodm1bsd.png)
<center><small>Olha o exemplo prático de um erro que pode f***** seu dia.</small></center>

&nbsp;

Agora vai o exemplo do ```-m```, que em vez de substituir, ele adiciona usuários ao grupo, Ex:

&nbsp;

![groupmodm2bsd](img/groupmodm2bsd.png)
<center><small>Agora é só um incremento, menos pior se for ver... bem, depende do problema.</small></center>

&nbsp;

Há, lembrando, quando utilizado a ferramenta ```pw```, somente é alterado o arquivo do ```/etc/groups```, o arquivo ```/etc/passwd``` fica intocado.

&nbsp;

___


&nbsp;

### Permissões

&nbsp;

Aqui chega o famoso 666... mentira, dá pra ir até 777... oquê é isso? Se você está se perguntando isso, lhe respondo que é a permissão de arquivos, diretórios e demais dentro do S.O.

&nbsp;

Numa explicação simples, um arquivo possui três capacidade e três tipos de acessos, forá o proprio tipo do arquivo, Ex:

&nbsp;

|Tipo|Permissão do criador|Permissão do grupo do criador|Permissão de demais usuários|
|---|---|---|---|
|-|rw-|r--|r--|

&nbsp;

Ainda confuso? Se sim, olhe esse:

&nbsp;

|Tipo do arquivo|Permissão do criador|Permissão do grupo do criador|Permissão de demais usuários|
|---|---|---|---|
|-|6|4|4|

&nbsp;

Agora você entendeu? Não? Más é a mesma coisa as duas tabelas!... Ainda confuso né, bem, olhe isso, agora vai ficar mais explicadinho:

&nbsp;

|Tipo do arquivo|Permissão do criador|Permissão do grupo do criador|Permissão de demais usuários|
|---|---|---|---|
|-|rw-|r--|r--|
|-|6|4|4|

&nbsp;

Primeiro, o arquivo exemplificado tem a permissão ```rw-r--r--``` ou ```644```, isso é, ```[Leitura, escrita][Leitura][Leitura]```, vejá o do pq:

&nbsp;

* ```r``` -> Símbolo de ```read```, que possui o valor de 4;
* ```w``` -> Símbolo de ```write```, que possui o valor de 2;
* ```x``` -> Símbolo de ```exec```, que possui o valor de 1;

&nbsp;

Se algo tem a permissão de ```777``` é pq esse algo é equivalente há ```rwxrwxrwx``` ou ```[Leitura, escrita, execução][Leitura, escrita, execução][Leitura, escrita, execução]```

&nbsp;

De forma mais simples, a soma entre os valores gera as permissões por valor, Ex:

&nbsp;

![permissaoarquivosbsd](img/permissaoarquivosbsd.png)
<center><small>Exemplo de permissão de um diretório.</small></center>

&nbsp;

Agora, vamos fazer a tabela detalhada do ```pastel```, veja:

&nbsp;

|Tipo do arquivo|Permissão do criador|Permissão do grupo do criador|Permissão de demais usuários|
|---|---|---|---|
|d|rwx|r-x|r-x|
|d|4-2-1|4-0-1|4-0-1|
|d|7|5|5|

&nbsp;

Sim, ```0``` é o equivalente ao ```-```, que dentro das permissões, significa que a permissão foi vetada, porém ele ainda ocupa um espaço de permissão que pode ser eventuamente alterado.

&nbsp;

Agora seguem algumas dúvidas, sendo essas:

&nbsp;

* E os dispositivos conectados ao S.O?
    * Todos os dispositivos são tratados como arquivos de determinado nível de acesso e normalmente esses dispositivos ficam montados dentro do ```/dev```;

&nbsp;

* Se o primeiro simbolo é o tipo de arquivo e ele tem permissões, oq é um diretório com permissão executável?
    * Ele é ligeiramente diferente dos arquivos normais mesmo que ainda sejá um arquivo como todos os outros, a permissão de execução a ele, permite que o mesmo possa receber chamadas via ```cd```, permitindo que esse diretório pode ser utilizado pelo coletivo.
    * Para ler as informações dentro de um diretório, o mesmo tem que ter permissão de leitura, isso é, um ```4 ou r``` na permissão;
    

&nbsp;

___

&nbsp;

### Permissão simbólica

&nbsp;

Utiliza caracteres em vez de valores octais para atribuir permissões, no esquema de (quem)(ação)(permissões), seguindo a tabela abaixo:

|Tipos|Letra|Representa|
|---|---|---|
|(quem)|u|Usuário|
|(quem)|g|Grupo|
|(quem)|o|Outros|
|(quem)|a|Todos forá o prórpio|
|(ação)|+|Adicionar permissão|
|(ação)|-|Remover permissão|
|(ação)|=|Definir permissões|
|(permissão)|r|Leitura|
|(permissão)|w|Escrita|
|(permissão)|x|Execução|
|(permissão)|t|Bit fixador|
|(permissão)|s|Set UID ou GID|

&nbsp;

___

&nbsp;

### Bandeiras do BSD

&nbsp;

Esse é um nível a mais de segurança aos arquivos dentro do BSD, não é valido aos diretorios, somente aos arquivos, porém, com essa funcionabilidade, até mesmo um superusuário como o ```root``` pode ser impedido de realizar açõs sobre arquivos de dentro do sistema.

 
&nbsp;

![chflagsbsd](img/chflagsbsd.png)
<center><small>Onde está marcado de vermelho, é onde está a permissão da flag.</small></center>

&nbsp;

Como demonstrado, o ```chflags``` tem a capacidade de aumentar a segurança e limitar ações sobre arquivos, sendo que até mesmo impediu um superusuário de deletar um arquivo, mesmo com a opção ```-f``` que era para forçar a ação.

&nbsp;
___

&nbsp;

### Chmod -> Definindo permissões

&nbsp;

Agora que já foi visto o valores, letras e até bandeiras, tá na hora de alguns exemplos sobre a alternancia de permissão entre os usuários sobre arquivos:

&nbsp;

![chmodexemplobsd](img/chmodexemplobsd.png)
<center><small>Alterando permissões via chmod</small></center>

&nbsp;

O comando ```chmod``` é utilizado para alterar o permissionamento dos arquivos e suas caracteristicas de acesso.

&nbsp;

___

&nbsp;

### Permissões ```setuid```, ```setgid``` e ```sticky```

&nbsp;

Esses três fazem parte somente de operações expecificas dentro do S.O BSD, para entender seus significados, tem de primeiro explicar oq é um ID real de um ID efetivo de usuário.

&nbsp;

* ***Real*** -> É o ```UID``` que inicia ou do dono do processo;
* ***Efetivo*** -> É o ```UID``` do usuário que está executando processo;

&nbsp;

Um exemplo de alternancia entre os valores é, utilizando o comando ```passwd```, onde mesmo executando como usuário comum, seu permissionamento é de ```root```, veja o exemplo nas imagens abaixo:

&nbsp;

![passwdtty1bsd](img/passwdtty1bsd.png)
<center><small>Entrando como outro usuário e pedindo para alterar a senha.</small></center>

&nbsp;


![psauxgreppasswdpermissao](img/psauxgreppasswdpermissao.png)
<center><small>Mostrando a permissão que o outro usuário possui quando executa o comando passwd.</small></center>

&nbsp;

Aplicando permissões ```setuid```, ```setgid``` e ```sticky``` nos arquivos:

&nbsp;

![permissoesespeciaisbsd](img/permissoesespeciaisbsd.png)
<center><small>Usando o chmod para conceder permissões especiais ao arquivo.</small></center>

&nbsp;

Para a aplicação de qualquer um dos listados, é necessário o superusuário ou ```root```.

&nbsp;

* ```setuid``` -> Permissão ```4``` para o arquivo, isso fará que o arquivo tenha permissão de ```root``` quando executado;
* ```setgid``` -> Basicamente a mesma coisa que o ```setuid```, porém esse é para grupos e seu valor de referência é ```2```;
* ```sticky``` -> Esse é diferente dos demais, servindo par aumentar a proteção, trancando o arquivo/diretório a somente o proprietario poder deletar o arquivo, o valor desse é ```1```;

&nbsp;

Agora fazendo uma pequena revisão sobre esse ponto, enquanto o ```setuid``` e o ```setgit``` server para elevar a permissão de um determinado arquivo a superusuário, mesmo sendo executado por usuários com menos permissão, o ```sticky``` serve como uma ferramenta de segurança, travando o arquivo e evitando sua alteração por outros que não sejá o próprio usuário.

&nbsp;

___

&nbsp;

### Tipos de arquivos

&nbsp;

Segue listado os tipos possíveis de arquivos dentro do sistema BSD:

&nbsp;

|Símbolo|Descrição|
|---|---|
|-|Arquivo comum|
|d|Diretório|
|c|Dispositivo de caracteres|
|b|Dispositivo de blocos|
|l|Link simbólico|
|p|Pipe|
|s|Socket|

&nbsp;

___

&nbsp;

### Estrutura de Diretório

&nbsp;

Segue abaixo uma tabela com o esquema de diretórios do sistema FreeBSD, lembrando que o diretório principal é a raiz do sistema, o ```/```.

&nbsp;

| Diretório | Descrição | 
|---|---|
|/| Raiz do sistema|
|/bin|Utilitários fundamentais para usuário único ou multiusuário|
|/boot|Programas e configurações utilizadas para o boot do sistema|
|/boot/defaults|Arquivos de configuração de inicialização padrão.|
|/dev|Conexões com dispositivos de hardware, como impressoras e discos, além de demais outros.|
|/etc|Arquivos e scripts de configuração do sistema.|
|/etc/defaults|Configuração padrão do sistema S.O.|
|/etc/mail|Configuração para softwares de email.|
|/etc/periodic|Scrips que serão executados pela crontab.|
|/etc/ppp|Arquivos de configuração do protocolo de ponto a ponto ```(PPP)```.|
|/mnt|Diretório vazio com utilidade de ser utilizado para montagem de unidades externas, em rede ou demais.|
|/proc|Sistema de arquivos de processo.|
|/rescue|Softwares para recuperação do sistema.|
|/root|Diretório da conta ```root```.|
|/sbin|Programas e utilitários fundamentais para o funcionamento do sistema.|
|/tmp|Arquivos temporários que geralmente não são preservados durante a reinicialização do sistema pois é montado durante tempo de execução, então fica em memória.|
|/usr|A maioria dos utilitários e aplicativos do usuário.|
|/usr/bin|Utilitários, ferramentas de programação e aplicativos comuns.|
|/usr/include|O padrão C de arquivos incluidos.|
|/usr/lib|Biblioteca dos arquivos em geral.|
|/usr/libdata|Arquivos de dados de utilitários diversos.|
|/usr/libexec|Daemons do sistema e utilitários do sistema executados por outros programas.|
|/usr/local|Executáveis ​​e bibliotecas locais, que também é usado como destino padrão para o framework de ports, dentro do próprio do / usr / local , o layout geral esboçado por hier (7) para / usr deve ser usado. As exceções são o diretório man, que está diretamente em / usr / local em vez de em / usr / local / share , e a documentação do ports está em share / doc / port .|
|/usr/obj|Diretório produzido pela construção do diretório /usr/src|
|/usr/ports|Coleção de ports do FreeBSD|
|/usr/sbin|Daemons do sistema e utilitarios executados pelo usuário|
|/usr/share|Arquivos independentes de arquitetura|
|/usr/src|BSD e/ou arquivos de origem local|
|/var|Arquivos diversos e de multiuso, como logs, spool, valores fixos do sistema e demais, esse diretório só existe em tempo de execção, já que é montado em memória|
|/var/log|Arquivos de log diversos|
|/var/mail|Caixa de correio|
|/var/spool|Arquivos de spool|
|/var/tmp|Arquivos temporários que são preservados após a reinicialização do S.O|
|/var/yp|Mapas NIS ***(Conferir melhor esse ponto depois)***|

&nbsp;

Segue um exemplo da raiz do FreeBSD, lembrando que essa foi uma instalação ```default``` e sem qualquer alterações:

&nbsp;

![raizbsd](img/raizbsd.png)
<center><small>Toda a raiz simples de um BSD sem customizações.</small></center>

&nbsp;

Fica abaixo um exemplo do uso do local do ```/usr/local``` após qualquer instalação de um programa externo ao que já forá adicionado durante a instalação.

&nbsp;

![userlocalhtopbsd](img/userlocalhtopbsd.png)
<center><small>Demonstração de um /usr/local com a instação de somente o componente htop dentro do S.O.</small></center>


&nbsp;

___

&nbsp;

### Organização dos discos

&nbsp;

Caracteristicas:

&nbsp;

* Menor unidade de busca do sistema é o nome;
* O sistema não é case-sensitive, Ex: ```teste``` é diferente de ```testE``` e outras demais diferenças;
* A extensão de um arquivo não define que tipo de arquivo é o mesmo;
* Diretórios são arquivos, os mesmo podem conter de nada a centenas de arquivos do mesmo, ou demais arquivos, além deste tipo de arquivo permitir uma hierarquia;
* Diferenças entre endereços completos  de arquivos dentro do BSD, Ex: ```/teste/t1.txt``` é de um BSD/Unix/Linux, de um windows é assim ```C:\teste\t1.txt```;
* Diretórios de nível superior são o inicio do sistema de arquivo que se inicia no ```/```, todos os discos fisicos montados ficam sobre o sistema de arquivo superior, são todos tratados como diretórios dentro do S.O;
* Sistemas de arquivos diferentes podem ter diferentes opções de montagem,  isso é, é possível montar partes do sistema de arquivos que possuem diferentes caracteristicas;

&nbsp;

Caracteristicas do FreeBSD:

&nbsp;

* O BSD otimiza automaticamente o layout do sistema de arquivos;
* O sistema de arquivos do BSD é resistente a perda de energia ou finalização inesperada, porém não infalivel, uma forma de garantir maior integridade, é dividir o sistema de arquivos em outras partições, facilitanto  uma manutenção ou desativação de determinadas partições de forma a manter o sistema estável;
* O sistema de aarquivo são fixos desde o momento de instalação, não sendo simples o aumento do espaço de disco;
* O BSD pode usar partições com tag's de definição entre A a H, forá uma dessas partições é utilizada como memória reserva, o swap;
* Pode haver no máximo 4 partições fisicas no máximo, forá que pode haver várias partições lógicas;
    * Toda partição fisicia do sistema terá como identificação a siglas do hostname, com o prefixo de s e o valor da partição que se inicia no 1, Ex: hostname pastel vai ter as partições ````ps1``` e demais;
* O BSD identifica os discos como, seu tipo e os nomeando e depois colocando uma valor, Ex: ```ada0```;

&nbsp;

Associação das tag's com as partições

&nbsp;

|partição|Uso|
|---|---|
|a|Partição que normalmente fica a raiz ```/```|
|b|Partição de swap|
|c|Partição de slices para reparação do S.O|
|d|Antigamente tinha uma função especial relacionada a essa partição, porém, atualmente, é uma partição qualquer|

&nbsp;

Nome de dispositivos de disco

&nbsp;

|Tipo|Identificação|
|---|---|
|Discos rígidos SATA e IDE|ada / ad|
|Discos rígidos SCSI ou armazenamento USB|da|
|Drive CD-ROM SATA e IDE|cd / acd|
|CD-ROM SCSI|cd|
|Disquete|fd|
|CD-ROM não padrão|mcd (Mitsumi) / scd (Sony)|
|Fita SCSI|sd|
|Fita IDE|ast|
|RAID|aacd (Adaptec) / mlxd e mlyd (mylex) / amrd (MegaRAID) / idad (Compaq) / twed (3Ware) |

&nbsp;

___


&nbsp;

### Montagem de sistema de arquivos

&nbsp;

Uma analogia comum é que o S.O é ramificado que nem uma árvore, possuindo diversos galhos que vão se extendendo, como visto anteriormente, um sistema de arquivos possui diversos diretorios que fazem coisas diferentes no S.O.

&nbsp;

Alguns desses diretórios possuem caracteristicas diferentes e por isso devem ser tratados de formas diferentes, exemplo é montar o ```/var``` em outro sistema de arquivos por motivos que o mesmo tente a crescer e se crescer no raiz, pode acabar prejudicando todo o sistema.

&nbsp;

A capacidade de montar e desmontar sistemas de arquivos são enomres, já que permitem maior flexibilidade ao sistema.

&nbsp;

Vale por fim comentar que alguns sistemas de arquivos não são montadas por motivos de ter a tag ```noauto```, isso é mostrado abaixo no ```fstab```

&nbsp;

___

&nbsp;

### Fstab

&nbsp;

Arquivo que mostra os sistemas de arquivos montados durante a inicialização.

&nbsp;

![userlocalhtofstabbsdpbsd](img/fstabbsd.png)
<center><small>Arquivo FSTAB</small></center>

&nbsp;

* ```device``` -> Nome do dispositivo;
* ```mount-point``` -> Diretorio alvo a se montar o sistema de arquivos;
* ```fstype``` -> Tipo do sistema de arquivo (No BSD o padrão é ```ufs```);
* ```options``` -> Opção de como montar o sistema de dados;
* ```dumpfreq``` -> Sinaliza se um sistema de arquivos precisa de dump (Um BK do sistema de arquivo);
* ```passno``` -> Verificação da integridade do sistema de arquivos;
    * Uma norma utilizada é que, o sistema de arquivos que contem o S.O deve ter a tag de 1, para ser a primeira;
    * Sistemas de arquivos como o SWAP não necessita dessa tag pois não há necessidade de verificação;
    * Demais sistemas de arquivos devem possuir a tag de forma crescente como 2,3,4 e assim por diante, não sendo recomendado colocar a mesma tag em mais de um S.A pois o S.O vai fazer a verificação em paralelo;

___

&nbsp;

### Mount

&nbsp;

Comando utilizado para montar partições para o S.O trabalhar ou o usuário se utilizar, Ex:

&nbsp;

* ```-a``` -> Monta todos os sistemas de arquivos listados no ```/etc/fstab``` com excessão de:
    * Todos marcados como ```noauto```;
    * Excluidos pelo ```-t```;
    * Já montados;
* ```-d``` -> É usado em conjunto com o ```-v``` para simular a montagem de um sistema de arquivos;
* ```-f``` -> Força a montagem ou trocar da atual permissão de um sistema de arquivos;
* ```-r``` -> Monta o sistema de arquivo somente para leitura, é igual ao ```-o ro```;
* ```-t``` -> Especifica o sistema de arquivos que ser´´a montado;
* ```-u``` -> Atualiza as opções de montagem;
* ```-v``` -> Modo verbose da operação;
* ```-w``` -> Monta o sistema com permissão leitura/escrita;

&nbsp;

___

&nbsp;

### Umount

&nbsp;

Comando para desmontar sistemas de arquivos/Partições do S.O, Ex: 

&nbsp;

* ```-a``` -> ```-a``` é para a desmontagem de um ponto e ```-A``` é a demontagem do nome do dispositivo;
* ```-f``` -> Força a desmontagem do sistema de arquivos;
* ```-v``` -> Modo verbose, mais detalhamento;
* ```-t``` -> Desmonta todos os sistemas de arquivos;


&nbsp;

___

&nbsp;

### Processos e daemons

&nbsp;

O sistema BSD é um S.O multitarefa, onde cada programa em execução é chamado de processo, o programa pode ser diversas coisas, Ex: Shell's em execução, programas instalados, execuções de scripts e demais, porém, tudo gera minimamente um unico processo no sistema ou mais.

&nbsp;

Cada processo possui um ID (PID), esse é o número de identificação dos processos, como visto até agora, tudo dentro do sistema tem um nível de acesso e permissionamento, os processos não são diferentes, os processos são sempre iniciados na execução de algo, esses processos podem ser unicos, pais ou filhos e cada um tem sua identificação.

&nbsp;

Somente o processo do ```init``` será de PID 1, já que é o primeiro processo do sistema quando ele da boot.

&nbsp;

![grepinitbsd](img/grepinitbsd.png)
<center><small>O primeiro processo do sistema.</small></center>

&nbsp;

Existem dois tipos de processos, o primeiro sendo o normal, onde ele é iniciado, executado e finalizado e existe o processo persistente, no caso os *deamons* (Termo grego que se refere a entidade que realiza trabalhos uteis sem conceitos de bom ou mal), programas desse tipo costumam serem nomeados com um ```d``` no final, exemplos são o apache que o processo é marcado como ```httpd```, o spool é ```lpd``` e demais outros.

&nbsp;

___

&nbsp;

### Processos

&nbsp;

Processos são extremamente importantes, por motivos que o os mesmo são responsaveis por todo o funcionamento do S.O, sendo assim, é importante ficar cientes do mesmo e ter um bom controle sobre eles, assim garantido a saúde do S.O.

&nbsp;

Segue abaixo um pouco sobre listar os processos do S.O:

&nbsp;

* ```ps``` -> Lista os processos de forma estática, seu significado é ```process status```;
* ```top``` -> Abre um gerenciador de tarefas em tempo real, seu signicado é tela atualizada de informações sobre o consumo da CPU;

&nbsp;

Primeiramente, o comando ```ps``` lista por padrão os processos que o usuário está executando no momento ou que são de prioridade do mesmo.

&nbsp;

![psbsd](img/psbsd.png)
<center><small>Processos relacionados ao usuário via ps.</small></center>

&nbsp;

Para entender melhor:
* ```PID``` -> ID unico do processo;
* ```TT``` -> Sessão TTy em uso;
* ```STAT``` -> Estado do processo;
* ```TIME``` -> Tempo que o programa esteve em execução no CPU;
* ```COMMAND``` -> Comando que é usado para iniciar o processo;

&nbsp;

![psauxwwbsd](img/psauxwwbsd.png)
<center><small>Usando o ps -auxww.</small></center>

&nbsp;

Esse comando traz os parametros:

* ```a``` -> Informações dos processos em execução;
* ```u``` -> Detalha mais o processo e seu consumo;
* ```x``` -> Mostra todos os processos;
* ```ww``` -> Linha de comando do processo;

&nbsp;

![psubsd](img/psubsd.png)
<center><small>Diferença entre um ps com e sem o parametro u.</small></center>

&nbsp;

O comando ```top``` é um tela atualizada sobre as tarefas e estados do sistema, divida em duas telas, sendo que a primeira são as informações do ```header```, que são:

&nbsp;

* ```last pid``` -> Ultimo processo do sistema;
* ```load averages``` -> Carga do sistema, a carga é calculada de 1,5,15 minutos e essa carga é formulada por quantidade de processos por recursos;
* ```uptime``` -> É o tempo desde o boot e depois é a hora atual;
* ```process``` -> Quantidade de processos, ativos, parados e zumbis;
* ```CPU``` -> Mostra a carga do CPU que está em uso;
* ```Mem``` -> Mostra a carga do uso de memória;
* ```ARC``` -> Se estiver utilizado um sistemas de arquivo ZFS, essa linha irá demonstrar a quantidade de dados que foram lidas do cache da memoria;
* ```Swap``` -> Quantidade de memória SWAP em uso no sistema;

&nbsp;

![topbsd](img/topbsd.png)
<center><small>TOP demais.</small></center>

&nbsp;

Depois do ```header``` vem o ```body``` que são compostos por colunas de informações dos processos do sistema, segue as informações das colunas:

&nbsp;

* ```PID``` -> Identificação do processo;
* ```USARNAME``` -> Nome do usuário que está executando o processo;
* ```THR``` -> ;
* ```PRI``` -> Prioridade do processo;
* ```NICE``` -> Influenciador de prioridade;
* ```SIZE``` ->  Quantidade total de memória consumida;
* ```RES``` -> Memoria atualmente alocada para o processo;
* ```STATE``` -> Status do processo;
* ```C``` -> Numero do processo que está em execução;
* ```TIME``` -> Tempo de uso do processador;
* ```WCPU``` -> Necessidade de uso do processador;
* ```COMMAND``` -> Comando que está em execução;

&nbsp;

___

&nbsp;

### KILL... os procesos tá

&nbsp;

O ato de matar o processo é enviar um sinal para que esses processos sejam finalizados, existem vários tipos de sinais que podem ser utilizado, forá que existe várias permissões para reaizar esse ato.

&nbsp;

O ```root``` é o único usuário com permissão total de finalizar qualquer processo do sistema, normalmente, um usuário só pode finalizar processos a qual o mesmo tenha criado.

&nbsp;

Outros sinais são:

&nbsp;

* ```SIGSEGV``` -> "Segmentation violation" ou acesso indevido a memória;
* ```SIGTERM``` -> Finalização correta do processo, fecha os logs do mesmo e finaliza o processo;
* ```SIGKILL``` -> Mata o processo de forma brusca;
* ```SIGHUP, SIGUSR1 e SIGUSR2``` -> Sinais de finalidade geral que são interpretados de forma diferente por diferentes programas;

&nbsp;

Exemplo de um sinal de ```kill``` ao processo:

&nbsp;

![pgreptopbsd](img/pgreptopbsd.png)
<center><small>Pegando o PID do processo.</small></center>

&nbsp;

![killprocessbsd](img/killprocessbsd.png)
<center><small>Matando um processo via PID.</small></center>

&nbsp;

É valido comentar que se o ```PID``` não existir, o processo de ```kill``` simplesmente falha, além de que, se o ```PID``` estiver incorreto ou não existir, ainda se pode matar um processo pro meio do nome dele utilizando o ```killall```, Ex:

&nbsp;

![killallbsd](img/killallbsd.png)
<center><small>Matando um processo via nome.</small></center>

&nbsp;

#### Observação!

&nbsp;

Todo o shell tem seus ```alias```, o ```kill``` não é excessão e pode até carregar parametros no mesmo, sendo assim, é recomendado verificar o tratamento do shell sobre os comandos, além de, uma forma de evitar que o shell execute o comando com parametros não desejado, é mais facil executar o programa pelo caminho completo, exemplo é usar o utilitário direto do ```/bin```.

&nbsp;

Por fim é valido dar algumas recomendações, não mate os processos do sistema caso não os conheça, a menos que o ambiente que esteja usando sejá descartavel ou para esses meios.

&nbsp;

___

&nbsp;

### Shells 

&nbsp;

O shell é a interface de meio de campo entre o usuário e o sistema operacional, os shell's carregam várias coisas com sigo, como váriaveis de ambiente, abtenção dos arquivos e demais, o BSD em si, vem com vários modelos de shell's juntos, como o ```shell bourne (sh)``` e ```shell C extendido (tcsh)```.

&nbsp;

Existem outros demais shell's como:

&nbsp;

* ZSH;
* Bash;
* CSH;

&nbsp;

Em geral, os shells tem as mesmas utilidades, sendo mais uma questão de gosto e funcionabilidades extras para definir a utilização de cada qual.

&nbsp;

O shell tem a capacidade de utilizar váriaveis de ambiente, sendo alguns já definidos pelo sistema, seguem abaixo alguns exemplos:


&nbsp;

|Váriavel|Descrição|
|---|---|
|USER|Nome do usuário|
|PATH|Diretórios que contém executaveis|
|DISPLAY|Display Xorg disponíveis|
|SHELL|Shell em uso|
|TERM|Software terminal em uso|
|TERMCAP|Funções do terminal em uso|
|OSTYPE|Tipo do S.O|
|MACHTYPE|Arquitetura do CPU|
|EDITOR|Editor de texto preferencial do usuário|
|PAGER|Utilitário padrão para visulização de arquivos|
|MANPAHT|Locais de manuais do S.O|


&nbsp;

![variaveisambientebsd](img/variaveisambientebsd.png)
<center><small>Segue exemplos dos echo's dos valores de váriaveis globais.</small></center>


&nbsp;

Você pode usar qualquer shell, porém, como dito, cada uma tem suas caracteristicas, um exemplo disso é que para setar váriaveis de ambiente ou global, o processo é diferente dependente os shell's, segue o exemplo prático:

&nbsp;

![setenvexportbsd](img/setenvexportbsd.png)
<center><small>Diferença entre criar váriaveis de ambiente entre um CSH e um SH.</small></center>

&nbsp;

___

&nbsp;

### Caracteres especiais

&nbsp;

Aqui é mais um aviso, o shell interpreta caracteres especiais e pode até dar uso em alguns, como exemplo a imagem abaixo:

&nbsp;

![caracterespecialbsd](img/caracterespecialbsd.png)
<center><small>Um LS diferente...</small></center>

&nbsp;

Para você evitar o uso de caracteres especiais dentro do shell, você tem que escapar, Ex:

&nbsp;

![escapebsd](img/escapebsd.png)
<center><small>Usando um escape de caracteres...</small></center>

&nbsp;

___

&nbsp;

### Alterando o shell do usuário

&nbsp;

Tem algumas formas de alterar o shell do sistema, que são:

* Alterando a váriavel de ambientedo ```$SHELL```;
* Usando o comando ```chsh```;
* Executar um novo shell na sessão atual;

&nbsp;

Veja a seguir a demonstração dos mesmos:

&nbsp;

![shbsd](img/shbsd.png)
<center><small>Usando o CHSH para trocar de shell..</small></center>

&nbsp;

Arquivo que lista todos os ```SHELL's``` instalados no sistema, esse arquivo é automaticamente atualizando quando um shell novo é instalado via PKG:

&nbsp;

![etcshellsbsd](img/etcshellsbsd.png)
<center><small>Arquivo /etc/shells que lista todos os shells que o sistema possui e pode se utilizar.</small></center>

&nbsp;

___

&nbsp;

### Usando direcionadores

&nbsp;

Usos mais avançados do shell são de intercalação de comandos, uso de direcionadores e demais, Exemplo é a imagem que vai a seguir:

&nbsp;

![exemplodesaidashellbsd](img/exemplodesaidashellbsd.png)
<center><small>Demonstrando o uso de um direcionador e seu resultado.</small></center>

&nbsp;

Direcionador:
* ```>``` -> Direciona a saída para a criação de um arquivo ou substituição total de um já existente;
* ```>>``` -> Incrementador e/ou criador, quando utilizado, o mesmo atualiza o contéudo de um arquivo, adicionando no final do mesmo as novas linhas, caso o arquivo não exista, será criado um novo arquivo pela ação;

&nbsp;

Intercalar:
* ```|``` -> Pipeline faz com que a saída de uma operação seja jogada para outra operação;
* ```&&``` -> Condição de ```AND```, mais conhecido como E, onde o mesmo somente apresenta resultados se a condição for verdadeira, isso é, ambos os lados tivrem suas operações retornando um resultado aceitavel;
* ```||``` -> Condição de ```OR```, mais conhecido como OU, essa é uma condição onde somente um dos lados da operação deve ser verdadeiro para a amostra dos resultados;


&nbsp;

![condicaoebsd](img/condicaoebsd.png)
<center><small>Usando uma codição de AND.</small></center>

&nbsp;

![condicaooubsd](img/condicaooubsd.png)
<center><small>Usando uma codição de OU.</small></center>

&nbsp;

___

&nbsp;

### Editores de texto

&nbsp;

O FreeBSD possui vários editores de arquivos pelo próprio sistema, Ex:

&nbsp;

* ```vi```
* ```ee```
* ```nano```

&nbsp;

É bom conhecer o mínimo de cada um, já que há chances da necessidade de alteração de arquivos do sistema ou qualquer do tipo, necessitando de uma ferramenta que não sejá por interface gráfica.

&nbsp;

O conhecimento e uso de um editor de texto é necessário a todos os usuários, já que os mesmos podem economizar tempo em tarefas e támbem pelo fato que sem a alteração de arquivos, ficará extremamente limitado a atuação dentro do S.O.

&nbsp;

###### P.S: Existem demais outros editores de texto, porém tem que utilizar do PKG para instalar os mesmos, um exemplo é o ```vim```, que é uma versão melhorada do ```vi``` normal.

&nbsp;

___

&nbsp;

### DMESG

&nbsp;

Durante o boot do kernel do BSD, você deve ter visto um monte de mensagens durante o start do sistema, essas mensagens ficam armazenadas no ```/var/run/dmesg```.

&nbsp;

___

&nbsp;

### Dispositivos e nós

&nbsp;

Todos os dispositivos são montados em ```/dev```, cada dispositivo tem uma sigla e um número de identificação, Ex: 

&nbsp;

* ```ada0``` -> Disco SATA;
* ```kbd0``` -> Teclado;

&nbsp;

___

&nbsp;

### Manual

&nbsp;

Quase todo o comando dentro do sistema ou instalado, possui um manual, Ex:

&nbsp;

```
man ls
```

&nbsp;

Partes do manual:

* 1° -> Comnados do usuário;
* 2° -> Chamadas do sistema e números de erro;
* 3° -> Funções nas bibliotecas C;
* 4° -> Drivers de dispositivo;
* 5° -> Formatos de arquivo;
* 6° -> Jogos e outras diversões;
* 7° -> Informações diversas;
* 8° -> Comandos de manutenção e operação do sistema;
* 9° -> Interfaces do kernel do sistema;

&nbsp;

![manmanbsd](img/manmanbsd.png)
<center><small>Aquele cômico man do man... bugou né</small></center>

&nbsp;

Alguns comandos:

&nbsp;

* ```man -k``` -> Mostra partes que fazem refêrencia a procura, Ex:

&nbsp;

![mankpsbsd](img/mankpsbsd.png)
<center><small>Usando um -k para achar todas as refêrencias</small></center>

&nbsp;

* ```man -f comando``` -> Faz uma emulação da base de dados do ```whatis```, Ex: 

&nbsp;

![emulatedwhatisbsd](img/emulatedwhatisbsd.png)
<center><small>Emulando um whatis</small></center>

&nbsp;
___


&nbsp;

### Pacotes

&nbsp;

O FreeBSD fornece duas ferramentas diferentes para a instalação de pacotes:

&nbsp;

* Coleção dos ports;
* Pacotes pré-compilados;

&nbsp;

Exemplo de instalação de arquivos terceiros ao sistema:

&nbsp;

* 1 -> Encontre o software e o baixe (código-fonte ou binário);
* 2 -> Descompacte o software para o mesmo ser utilizado;
* 3 -> Os arquivos descompactados normalmente possuem um diretório ```doc/``` que auxilia na instalação;
* 4 -> Se for um código-fonte, necessita compilarr;
* 5 -> Teste o compilado e instale;

&nbsp;

O ```port``` é toda uma coleção de arquivos para otimizar o processo de instalação de um código-fonte, servindo para baixar, extrair, corrigir, compilar e instalar aplicativo.

&nbsp;

Existem mais de 24 mil pacotes já preparados para o BSD, caso necessite de um pacote que não exista no BSD, é necessário compilar o mesmo utilizando as ferramentas do sistema para seu funcionamento.

&nbsp;

Vale comentar que todos os pacotes e ports do sistema, são gerenciaveis pelas ferramentas de tratamento de software do sistema.

&nbsp;

Tanto para pacotes quanto  ports sofrem um mesmo problema, isso é, dependencias, esses são partes extras necessárias para o funcionamento de determinados programas, um exemplo simples é que, um programa pode nessecitar de uma Lib em C para funcionar.

&nbsp;

Caracteristicas entre os dois sistemas:

* tarball compactado de um pacote é menor que um código-fonte;
* Pacotes não requerem tempo de compilação;
* Pacotes não requerem entendimento do processo de compilação;
* Aplicativos podem requerer alterações durante a compilação, por motivos de possuirem extras ou demais funcionabilidades;
* Algumas aplicações por motivos de licenças não podem ser distribuidas via pacote, necessitando ser via código-fonte;
* Aplicações em código-fonte são totalmente aberta a leitura e alteração antes da compilação e instalação;
* Código fonte é utilizado para aplicação de patches personalizados;

&nbsp;

___

&nbsp;

### Encontre os softwares para o BSD

&nbsp;

Segue uma lista de locais que se podem encontrar softwares para a plataforma BSD:

&nbsp;

* No site do [FreeBSD](https://www.freebsd.org/ports/);
* Dan Langille mante o site [FreshPorts](https://www.freshports.org/), esse site possui diversar funcionabilidades, sendo essas:
    * Envio de email com base em alterações em pacotes marcados;
    * Atualidade conforme os pacotes;
* Plataformas terceiras, como exemplo o github;

&nbsp;

Segue um exemplo de como saber os pacotes binários de uma aplicação, Ex:

&nbsp;


![pkgsearchbsd](img/pkgsearchbsd.png)
<center><small>Pacotes binários do subversion</small></center>

&nbsp;

O retornado é:
* Os pacotes necessários que foram compilados para uso do programa;
* Versionamento dos pacotes;
* Descrição dos pacotes;

&nbsp;

![pkgosearchbsd](img/pkgosearchbsd.png)
<center><small>Usando o -o como parametro</small></center>

&nbsp;

Com o parametro -o, ele lista a origem do pacote, exemplo é que alguns dos listados vieram do ```devel```, outros do ```java``` e assim por diante.

&nbsp;

Uma forma de procurar por programas dentro do sistema utilizando o ```whereis```, Ex:

&nbsp;

![whereisbsd](img/whereisbsd.png)
<center><small>Procurando programas dentro do sistema e conferindo se o mesmo existe.</small></center>

&nbsp;


&nbsp;

___


&nbsp;

### Comando SU

&nbsp;

![exemplocomandosu](img/exemplocomandosu.png)
<center><small>Exemplo da troca de usuário em tempo real via comando su no shell SH BSD.</small></center>

&nbsp;

___

&nbsp;

### Shutdown

&nbsp;

Para o desligamento do sistema BSD, é feito os seguintes passos:

&nbsp;

* Comandos de desligar ou reiniciar o sistema requisitarão o shell ```/etc/rc.shutdown```;
* Após acionar o shell, todos os processos receberam um sinal de ```TERM```, aqueles que não responderem em tempo hábil, receberam um ```KILL```;

&nbsp;

Para o desligamento do sistema em arquiteturas que suportam o controle de ACPI, é necessário os comandos:

```
shutdown -p now
init 0
halt -p
```

&nbsp;

Para reiniciar o sistema use:

```
shutdown -h now
reboot
halt -q
```

&nbsp;

Lembrando somente os membros do grupo ```operator``` ou o próprio ```root``` tem capacidad de reiniciar ou desligar.

&nbsp;

___

&nbsp;

### Compilar um PORT

&nbsp;

Para compilar uma porta, você simplesmente muda para o diretório do programa que deseja instalar, digite make installe deixe o sistema fazer o resto. 

&nbsp;

___

&nbsp;

### Agradecimentos

&nbsp;

Há, aqui vai coisa ainda para ser feita, más agradeço a própria documentação do BSD e todos os sites buscados durante o desenvolvimento deste mini-manual. 

&nbsp;
___