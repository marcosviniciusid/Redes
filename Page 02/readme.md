# Redes 

## Proxy direto

Um servidor proxy é um servidor que serve como um intermediário na comunicação entre dois dispositivos em uma rede. Por exemplo, quando um cliente quer falar com servidor, se existir um servidor proxy nessa rede, o cliente vai mandar o pedido para o servidor proxy. O servidor proxy por sua vez vai encaminhar esse pedido a um servidor. O servidor vai responder esse pedido ao proxy e não ao cliente proxy. O servidor proxy vai encaminhar a resposta ao cliente. No dia a dia existem duas aplicações práticas pra esse tipo de servidor: 

* Primeiro uso, Como um **sistema de Cache**.  
Um Sistema de cache serve para acelerar o carregamento de alguma coisa, no caso mais comum o carregamento de uma página web. Você navega em sua casa a internet através do seu navegador, esse navegador faz um cache em disco dos arquivos que já foram acessados. Quando você acessa um site constantemente, o browser já vê que imagem você já carregou para não carregar novamente.Ele checa com o site para saber se você já tem esse arquivo em sua máquina (na unidade de armazenamento) se os arquivos verificados forem os mesmos, não terem sido modificados, o servidor não vai "lá" no site buscar novamente esses arquivos, o servidor vai buscar na sua máquina (Local), em arquivos temporarios, por exemplo. Dessa forma ele acelera seu acesso na internet e economiza banda de internet, economiza transferencia.  
  
  Usando numa rede, você tem uma rede local e você instala um servidor proxy para servir como intermediário a todos os computadores que quer acessar a internet. Então esse servidor proxy pode servir como cache, fazer o mesmo papel do navegador por exemplo. Ele já carregou várias informações e então vai agilizar o acesso e economizar banda de internet.

* Segundo uso do servidor proxy, é para mascarar a sua origem.  
 De onde você está acessando um determinado recurso. Exemplo, você quer acessar do Brasil um servidor que está na Europa, e você quer mascarar seu IP - endereço lógico (*Pelo endereço IP dá pra rastrear de que País você está acessando*). Exemplo, você usa um servidor proxy nos Estados Unidos, o seu pedido vai sair do Brasil para o USA e do USA vai para a Europa. Do ponto de vista do servidor da Europa você está acessando do USA e não do Brasil, você colocou um intermediário no meio do caminho.  
   
   Então se o servidor da Europa tá bloqueando usuários que estão "vindo" do Brasil, na verdade você vai conseguir passar por fora, porque do ponto de vista do servidor agora, você está acessndo do servidor dos USA. Claro que, existem travas que o servidor pode colocar para não permitir acesso via servidores proxy. *(No exemplo citado, imagina que ele não tenha esse bloqueio.)*
   
   Existe dois problemas de utilizar um servidor proxy para mascarar seu acesso. O problema 1 é a lentidão, porque nesse caso ao invés de você acessar diretamente, você tem um intermediário no meio do caminho.  

No caso da rede local no primeiro exemplo de cache, não terá esse problema, pelo contrário, vai acelerar o acesso à internet. Porque o servidor proxy está na rede local, e o acesso é quase que imediato. Nesse outro caso, o servidor proxy esta no USA, pra depois você ter acesso ao do servidor da Europa. Através do servidor proxy dá pra capturar dados. Então por questão de segurança não é legal utilizar um servidor proxy terceiro.

* * *
## Proxy reverso

O proxy direto ele serve para facilitar a vida do computador cliente, o sistema de cache e burlar a limitação geografica por exemplo.

Já o servidor proxy reverso, também é um intermediário entre o cliente e servidor, só que é usado para facilitar a vida dos servidores e não mais do cliente, porém claro que ajuda o cliente também. 

Exemplos:

* **Firewall**  
É um servidor proxy reverso. Que funciona como um intermediário entre um servidor e a rede externa (*por exemplo a internet*). No ponto de vista do cliente ele tá achando que está acessando o servidor diretamente, mas tem o firewall no meio filtrando os pacotes de dados que passam de um lado para o outro.

* **Sistema de balanceamento de carga**  
O que é um balanceamento? Do ponto de vista do cliente ele vai acessar um endereço ou um servidor unico, e esse balancemaneto de carga (Servidor proxy reverso), vai distribuir esses pedidos que vão chegando para aquele endereço aquele recurso entre vários servidores. Por exemplo, quando você acessa um site muito movimentado... por exemplo o Google, quando você o acessa... Ele não tem só um servidor, existem váriosss servidores do Google, ams todos eles você acessa com um único endereço, quem responde por esse endereço é um servidor proxy reverso, chamado também de balanceador de carga, que vai pegar esse pedido e vai distribuir para um servidor desocupado (Que vai depender do mecanisco que for configurado para responder esse pedido).

* **CDN**  
(content Delivery Network) - Rede de entrega de conteudo.  
Exemplo de de empresa que usa esse recurso. CloudFlare. Do ponto de vista do usuario ele acessa um endereço unico que vai ser atendido por esse servidor proxy reverso, como no balanceamento de carga, a diferença é que o servidor que vai responder ao proxy reverse será aquele que está mais perto do usuario num sistema que é distribuido geograficamente ao redor do mundo.  
  
  Por exemplo, você tem um servidor web, um site hospedado no USA e temos clientes acessando esse site em diversos locais do Mundo, nos USA, no Brasil, no Japão, etc. Então essa rede de CDN terá servidores locais, mais próximos dos cliente. Então esses servidores locais farão um cache dos recursos mais usados do servidor original, que está lá dos USA, pra acelerar a distribuição. Já que você você vai gastar menos tempo se você tiver no Brasil acessando um servidor no Brasil do que acessando um servidor que está nos USA. Do ponto de vista do Cliente, ele vai acessar o site que está nos USA, mas o proxy reverso que está no Brasil vai responder para o servidor que fisicamente está no USA, vai servir como intermediario. Vai entregar então o conteudo que já tiver no cache do servidor, ou então se o conteudo pedido não tiver no cache ainda vai lá no servidor do USA e puxa os dados para entregar ao cliente que está no Brasil. 

*Proxy reverso como servidor de cache*

* * * 
[Próxima página - Page 03](.../../../Page%2003/readme.md)