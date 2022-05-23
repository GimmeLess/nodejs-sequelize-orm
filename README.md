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

* De