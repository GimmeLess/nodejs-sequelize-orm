* Projeto criado devido a sugestão de utilização da tecnologia blockchain na disciplina de Construção de Software do Mestrado da UNB.

# Blockchain

## Órgão

PMDF

## Problema

Controle das fichas pessoais e criminais de todos os cidadãos.

## Soluções já utilizadas

Cada órgão de segurança pública, assim como várias unidades dentro da própria PMDF possuem dados diferentes das pessoas. Alguns possuem foto, outros possuem o endereço desatualizado, outros possuem RG, assim como os dados criminais também podem não ser compartilhados entre os estados do Brasil.

Devido a esse problema, o Ministério da Justiça, criou o sistema Infoseg, com a proposta de integrar os dados de várias bases de dados, como: Receita Federal, Detran’s, Tribunais de Justiça dos Estados dentre outros, porém o sistema continua sendo ineficiente, pois depende da “boa vontade” das instituições com a atualização dos dados, disponibilidade dos serviços web e firmarem e atualizarem os convênios entre as instituições.

Como resultado, frequentemente o sistema fica indisponível para algumas funcionalidades, algumas funções deixam de funcionar por falta de atualização do convênio e alguns dados continuam desatualizados porque não são confrontados entre as diferentes bases de dados.

Além de todas essas características, existe o risco de dados pessoais e criminais simplesmente sumirem!

## Por que usar o blockchain?

Devido ao blockchain ser imutável, irrefutável e auditável, essa tecnologia será muito muito útil para o desenvolvimento desse controle de ficha pessoal e criminal, pois os dados serão sempre atualizados e os dados anteriores não serão perdidos, o sistema estará sempre disponível, pois existirão vários nós na rede.

Apesar de ser uma rede privada, será uma rede muito grande, pois todos os policiais de todos os estados podem ter acesso a esses dados e os dados de instituições diferentes seriam compartilhados em uma base única, além de que não teria o problema de dados sumirem devido a validação que é feita por todos os nós da rede e rastreado para identificar quem os modificou.


# Proposta de solução do problema

Controle de ficha pessoal e criminal usando blockchain

Configure seu blockchain usando [Multichain](http://www.multichain.com/) com [Vagrant](https://www.vagrantup.com/)

* Clone o repositório usando os comandos abaixo:

        $ git clone https://github.com/unb-ppca-construcao-de-software-2017/fichaPessoal.git
        $ cd fichaPessoal

* Acesse a pasta servidor e via terminal crie a máquina virtual do servidor e acesse usando os comandos abaixo:

        $ cd servidor
        $ vagrant up
        $ vagrant ssh

* Acesse a pasta cliente em outro terminal crie a máquina virtual do cliente e acesse usando os comandos abaixo:

        $ cd cliente
        $ vagrant up
        $ vagrant ssh

* Dentro da VM do servidor, crie o blockchain:

        $ multichain-util create fichaPessoal

* Dentro da VM do servidor inicialize o blockchain:

        $ multichaind fichaPessoal -daemon

* Dentro da VM do cliente acesse o blockchain do servidor:

        $ multichaind fichaPessoal@10.4.4.4:4401 -daemon

* Dentro da VM do servidor, adicione as permissões de conexão:

        $ multichain-cli fichaPessoal grant <CHAVE_DO_CLIENTE> connect,send,receive
        
        Exemplo de comando com a chave do cliente: permissao-ficha 1F6km6qxta5p5gqtFF3XMCspKT1cCsDDeCADuS

* Dentro do servidor do cliente, tente conectar novamente:

        $ multichaind fichaPessoal@10.4.4.4:4401 -daemon

* Acesse o modo interativo do blockchain fichaPessoal:

        $ multichain-cli fichaPessoal
        fichaPessoal: getinfo
        {
            "version" : "1.0 alpha 16",
            "protocolversion" : 10003,
            "chainname" : "fichaPessoal",
            "description" : "MultiChain fichaPessoal",
            "protocol" : "multichain",
            "port" : 4401,
            "setupblocks" : 60,
            "nodeaddress" : "fichaPessoal@192.1.2.46:4401",
            "burnaddress" : "1XXXXXXWsXXXXXXXRXXXXXXXZxXXXXXXat6JD4",
            "walletversion" : 60000,
            "balance" : 0.00000000,
            "blocks" : 55,
            "timeoffset" : 0,
            "connections" : 2,
            "proxy" : "",
            "difficulty" : 0.00001526,
            "testnet" : false,
            "keypoololdest" : 1457004398,
            "keypoolsize" : 2,
            "paytxfee" : 0.00000000,
            "relayfee" : 0.00000000,
            "errors" : ""
        }
# Criando e recuperando os dados no blockchain

Obs.: Todos os valores informados são em hexadecimal, exceto a chave da ficha, que nesse exemplo é o CPF, nossa chave de recuperação dos dados.

CPF de exemplo: 123456789-10

* Cria um registro para o cpf informado:

        $ create stream 12345678910 true
        
* Atribui um valor para o campo nome da ficha com o cpf informado:
        
        $ publish 12345678910 nome 416e646572736f6e204a6566666572736f6e20436572717565697261
             
* Lista todos os registros de todas as pessoas que constam no blockchain:
        
        $ liststreams
        $ subscribe 12345678910
        
* Lista todos os itens do cpf informado:
        
        $ liststreamitems 12345678910
        
* Cria um campo endereço com um valo