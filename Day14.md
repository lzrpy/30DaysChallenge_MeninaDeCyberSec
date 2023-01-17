# Um Analista de Defesa - Pesquisa DDOS
- Pesquise sobre um ataque DDoS, veja como é possível identificá-lo e como mitigar (pelo menos uma forma de mitigação). 
Poste um resumo do que você pesquisou.

## O que é DDOS?
- Bom, para iniciarmos o resumo de nossa pesquisa, vamos falar do que se trata a sigla DDOS. Distributed Denial of Service (DDOS), que em português significa "Negação de serviço distribuído", é um ataque muito utilizado, onde o objetivo é interromper o tráfego normal de um servidor, serviço ou rede, enviando inúmeras solicitações para o alvo com o objetivo de sobrecarregar sua infraestrutura com uma inundação de tráfego da internet. O ataque DDOS provém do DOS, um outro tipo de ataque, no qual sua sigla se dá por "Denial Of Service", que traduzindo para português significa "Negação de Serviço". DOS e DDOS são ataques parecidos, e ambos funcionam da mesma maneira e possuem o mesmo objetivo, sendo diferente somente a forma em que é realizado. Enquanto o DOS é um tipo de ataque que envia inúmeros Pacotes de solicitação por segundo de um único ponto de origem, o DDOS envia esses mesmos pacotes de solicitação, porém de vários pontos de origem diferentes.
- EX: DOS -> Pacotes enviados ao alvo somente por um computador
- EX: DDOS -> Pacotes enviados ao alvo por vários computadores em diferentes locais

## Como funciona um ataque DDOS?
- Um ataque DDOS é efetuado por redes de máquina conectadas á internet. Essas redes são formadas por computadores que foram
infectados por um malware, onde cada dispositivo infectado é adicionado a uma rede totalmente gerenciada pelo invasor,
permitindo assim que sejam controlados remotamente. Quando um dispositivo é infectado, chamamos-os de bots ou zumbis, e um grupo de bots na mesma rede, é chamado de botnet. Após uma botnet ser estabelecida, o invasor é capaz de direcionar o ataque enviando instruções remotas para cada bot na rede, ou seja, quanto mais bots compor a rede, maior será o número de solicitações enviadas ao alvo, fazendo com que o serviço, servidor ou rede fique offline (fora de serviço).

## DDOS do lado do servidor
- O servidor, serviço ou rede, por trabalhar com uma estrutura de threads, ou seja, é capaz de processar x tarefas 
concorrentemente, ao receber solicitações e todos os seus threads já estiverem processando outras tarefas, as solicitações 
que vão sendo recebidas e armazenadas em uma fila de espera, sendo lidas sequencialmente após certo thread ter finalizado o 
processamento da solicitação anterior e assim por diante. Quando temos inúmeras solicitações por segundo, como cada thread está ocupado lendo as solicitações, diversas vão sendo armazenas em fileira, causando a sobrecarga da infraestrutura.

## Como indetificar um ataque DDOS
- O sintoma mais comum de um ataque DDOS, é que um serviço fique lento ou indisponível repentinamente. Como o sintoma citado
anteriormente pode ocorrer devido ao grande tráfego normal, é necessário uma análise mais profunda para averiguação da situação.
As ferramentas de análise de dados de tráfego, como o TCPDump, Wireshark entre outros, podem nos ajudaro a detectar alguns 
desses sinais de um ataque de DDoS:
- Uma grande quantidade de tráfego vindo de um único endereço de IP, ou de uma mesma faixa de endereços IP
- Grande número de tráfego de usuários com o mesmo tipo de dispositivo, geolocalização ou versão do browser
- Um aumento de solicitações de certa página ou ponto em específico
- Padrões de tráfego em comuns, como grandes solicitações em horários incomuns ou padrões de x em x minutos
- Grande número de tráfego de IP's de outros países

## Principais tipos de ataques DDOS
- UDP Flood -> sobrecarrega portas aleatórias de um alvo com pacotes UDP
- NTP Flood -> envia pacotes válidos, porém falsificados de NTP a um alvo
- SYN Flood -> a memória de conexão do servidor é sobrecarregada devido ao alto número de pacores recebidos por uma comunicação TCP
- VoIP Flood -> envia inúmeras solicitações falsas, originadas de vários Ip's diferentes, atingindo protocolos do tipo VoIP
- POD - afeta diretamente os protoclos IP, enviando a quantidade máxima de pacotes de dados que os IP's conseguem suportar

## Como se proteger de um ataque DDOS
- Não existe uma fórmula definitva para impedirmos um ataque DDOS, porém tem diversas maneiras de eviarmos o ataque e mitigá-lo
- Usar um Firewall para gerenciar as conexões
- Utilizar um servidor de hospedagem como defesa adicional (Cloudflare)
- Integrar um sistema de reCAPTCHA em páginas de formulários
- Disponibilizar cada componente do serviço em vários servidores distintos (Site em um servidor, Banco de dados em outro etc)
- Utilizar um servidor de DNS Secundário
- Criação de regras para bloqueio de IP's que atingirem x solicitações em um curto período de tempo
- Análise do Tráfego com uso de ferramentas adequadas, como citadas acima ( Wireshark, TCPDUmp, netstat etc)
