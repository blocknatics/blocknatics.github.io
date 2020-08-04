---
layout: page
title:  "Blockchain, quebrando o gelo!"
date:   2020-07-01 08:00:00 -0300
categories: blockchain intro
---
<span class="paragraph">Cada vez mais se fez necessário rapidez na comunicação entre os processos e operações. Mesmo com as distâncias já encurtadas pela telefonia, em 25 de dezembro de 1990, Tim Berners Lee com a ajuda de mais algumas pessoas haviam completado a primeira comunicação via HTTP com sucesso, surge então a internet. Mesmo assim a evolução não pode ser contida, nem medida. A internet abriu portas para novas possibilidades, em agosto de 1994 então é feita a primeira compra com cartão de crédito via site de comércio eletrônico. Desde então não preciso nem comentar o quanto se tornou cada vez mais natural e necessário o aprimoramento dos pagamentos e serviços digitais.<br/>
<span class="paragraph">O fato é que para se gerenciar estes pagamentos necessita-se de terceiros, temos então as instituições financeiras que fazem este serviço. Mas  o tempo, custo gasto para manter estas transações financeiras não são baixos, sem falar no nível de confiança e integridade das informações sendo trocadas a todo momento.<br/>
<span class="paragraph">Em 2008 Satoshi Nakamoto, uma identidade desconhecida, publica um artigo nomeado “Bitcoin: A Peer-to-Peer eletronic Cash System”, um artigo que no ano seguinte daria início a uma nova revolução, que até o dia em que escrevo este artigo continua em crescimento para todas as áreas da sociedade. 
Não irei entrar em mais detalhes sobre Bitcoin, mas o que precisamos entender é que, ele só consegue existir em sua essência, pela tecnologia que o compõe por trás dos holofotes. Estamos então falando agora do Blockchain, que podemos entender como uma rede de computadores que opera em formato peer-to-peer, rodando regras pré-estabelecidas para armazenar transações de maneira decentralizada e distribuída.

## <strong>Entendendo de maneira simplificada
<span class="paragraph">Para exemplificar de maneira mais fácil esse conceito imagine o compartilhamento de arquivos via P2P, como eMule por exemplo. Quando alguém deseja baixar algum arquivo, conecta-se à rede pelo aplicativo, onde torna-se um integrante servindo-a então tanto como cliente ou servidor.
Entenda então que nesse caso todos que estão conectados à rede estão contribuindo para seu funcionamento.<br/>
<span class="paragraph">Você pode então baixar algum arquivo, que consequentemente é uma cópia do que está com outros usuários da rede. Veja então que no final das contas, todos estão trabalhando com cópias de uma informação qual seja.<br/>
<span class="paragraph">Da mesma forma Blockchain se assemelha a este exemplo, logicamente com suas características próprias. Mas mantendo nosso foco em como as informações são compartilhadas na rede, podemos entender seu funcionamento já que Blockchain é uma rede P2P.<br/>
<span class="paragraph"> Segundo Don Tapscott em seu livro “Blockchain Revolution”, Satoshi Nakamoto não tinha ideia da proporção que seu artigo poderia alcançar em outras áreas, já que sua visão era limitada ao dinheiro e não a um objetivo maior de criar uma nova geração da internet. O fato é que Blockchain além de manter funcionando uma rede de confiança tão grande como Bitcoin, só mostrou inicialmente como poderia ter seu potencial utilizado para melhorar ou trazer novos processos, que até então não eram imaginados.<br/>
<span class="paragraph">Para que se entenda melhor como o  blockchain pode ser utilizado, é necessário conhecer um pouco mais sobre a ledger, e as características da rede, que foram ponto de partida para sua aplicabilidade.

## <strong>A ledger<strong>
<span class="paragraph">Para que entremos em mais detalhes sobre Blockchain e suas características é necessário que haja um entendimento sobre o que é a ledger.
Ledger nada mais é do que o coração de uma rede Blockchain, todas as transações são adicionadas nela em forma de blocos.<br/>
<span class="paragraph">Nada pode chegar até seu nível antes de passar por uma série de processos de validação anteriores, portanto esta é última camada de uma rede Blockchain.<br/>
Da mesma forma nada pode ser alterado na ledger sem que impacte sua consistência, por isso para que alguma informação seja alterada é necessário que uma nova transação seja enviada, e logicamente depois de validada será então adicionada na ledger como uma versão mais recente. Mas entenda que a transação anterior estará ainda disponível, caso necessite ser visualizada novamente.


## <strong>Características de uma rede Blockchain</strong>
<br/>
#### <strong><strong>Transparência</strong>
<span class="paragraph">Os integrantes da rede têm a garantia de consultar os blocos e verificar a autenticidade das informações. Proporcionando maior transparência, onde não há outros pontos isolados que possam conter quaisquer informações inconsistentes. Toda transação será a mesma entre ambas as partes já que apesar de decentralizado, também é garantida a veracidade entre elas.

#### <strong><strong>Confiabilidade</strong>
<span class="paragraph">Diferentemente de um processo centralizado, onde a informação é gerenciada e aprovada em um único ponto. Com Blockchain temos vários pontos ou peers na rede, fazendo o trabalho de verificar os requisitos para aprovação de uma transação. Para isso usa-se o termo consensus, onde cada peer, deve processar as transações e verificar se atende aos critérios de uma regra pré-estabelecida, para que somente então marque a transação como válida. Mas o diferencial de todo este processo, é a necessidade de 51% dos peers aprovarem a transação, para que esta seja adicionada a um bloco e inserida na rede, ou mais precisamente dentro da ledger.

#### <strong><strong>Imutabilidade</strong>
<span class="paragraph">Toda transação dentro da ledger é imutável, ou seja, não pode ser alterada. Para que quaisquer mudanças ocorram em relação aos dados existentes, é necessário o envio de uma nova transação, para que passe por todo o processo novamente e com sua inclusão na ledger seja considerada a informação mais recente.

#### <strong><strong><strong>Segurança</strong>
<span class="paragraph">Blockchain traz consigo um ganho incrível na segurança das informações utilizadas na rede. Isso se deve em grande parte pela utilização de criptografia assimétrica PKI, onde é obrigatório que os participantes tenham suas chaves públicas e privadas para executar suas operações.
Outro fator importante que garante a segurança é o poder computacional que seria necessário para um possível ataque. Uma vez que, toda ledger é igualmente distribuída entre seus peers, seria necessário que mais de 50% destes tenham sido comprometidos, para que qualquer operação mal-intencionada tenha êxito. Isso se deve ao algoritmo de consensus, onde 51% de aprovação é necessária para qualquer transação na rede, logicamente para um cenário onde o ataque seja simplesmente forçar uma transação indevida.<br/>
<span class="paragraph">Em casos onde, se tente alterar alguma transação já armazenada nos blocos da ledger, seria ainda pior, já que para tal se faz necessário reescrever toda cadeia de blocos existentes. Os blocos são ligados pelo código hash de seus anteriores, mais uma vez se tornando inviável, principalmente se a rede já tiver alguma maturidade devido a quantidade de blocos existentes.

## <strong>Blockchains públicas<strong>
<span class="paragraph">Existem casos em que uma rede Blockchain não necessita de níveis de acesso a diferentes regras, como visualização de transações por exemplo. O usuário apenas pode se conectar à rede, e contribuir ou fazer uso dela para gerar novas transações através de seus serviços. Para tal uma rede Blockchain pública cai como uma luva, o exemplo mais comum disso é Bitcoin. Qualquer pessoa pode virar um nó na rede e começar a minerar, ou criar uma carteira virtual e fazer transferências para outros usuários sem nenhum custo ou critério de elegibilidade adicional.<br/>
Geralmente blockchains publicas trabalham com uma forma de incentivo, para que seus participantes contribuam com seu processamento e crescimento da rede.
 
## <strong>Blockchains privadas<strong>
<span class="paragraph">Todas as empresas possuem informações sensíveis que não podem ser compartilhadas, mas que as vezes fazem sentido serem adicionadas na rede por questões do negócio. Visando este tipo de cenário temos as blockchains privadas ou permissionadas, as quais possibilitam criar acessos para que somente usuários pré-definidos possam utilizar.<br/>
<span class="paragraph">Semelhantes as Blockchains públicas, elas também usam os conceitos de consensus e criptografia PKI, mas agora com mais essa camada de segurança por usuários.

## <strong>Blockchains hibridas<strong>
<span class="paragraph">Existe cenários onde necessita-se de processos que sejam abertos, mas existe também a falta de confiança ao expor outros desnecessários, que não consegue ser suprida por uma blockchain pública. Como visto anteriormente é possível usar uma blockchain privada, para que se disponibilize o acesso por meio de usuários, mas isso não ajuda quando é necessário ter os dois tipos de processos juntos.
Para estes então pode-se usar uma abordagem que usufrui das duas, que é chamada de blockchain hibrida.<br/>
<span class="paragraph">Dentre tantas características deste tipo de blockchain, podemos ressaltar a vantagem de se ter várias entidades ou empresas na mesma rede, compartilhando suas informações para contribuir na gerencia de um processo mais seguro e confiável, sem deixar de lado a transparência das informações que são relevantes a todos seus participantes. Afinal informações sensíveis não devem estar visíveis a todos, e para estes cenários limitar a transparência das informações a quem é pertinente se faz necessário.

## <strong>Smart Contract<strong>
<span class="paragraph">Apesar de ser um conceito antigo, teve sua popularização na primeira plataforma para criação de smart contracts, a Ethereum.
Os smart contracts ou contratos inteligentes são as regras de negócio responsáveis pelas validações da rede Blockchain. Portanto todas as vezes que os peers necessitam validar alguma transação, fazem uso deste smart contract para rodar as regras que lá foram definidas, se certificando de que tudo esteja como esperado.<br/>
<span class="paragraph">Cada framework para criação de redes Blockchain possibilitam sua criação em determinadas linguagens de programação como Java, JavaScript e GoLang por exemplo.

## <strong>Conclusões<strong>
<span class="paragraph">Blockchain é uma tecnologia que tem um grande potencial se utilizado de maneira correta. Assim como pode ajudar a melhorar ou criar novos processos devido a suas características, também pode atrapalhar se entendido como a solução para todos os problemas. O fato é que para usar Blockchain, em qualquer cenário, primeiramente deve-se fazer uma série de questionamentos até chegar à conclusão de que a tecnologia trará os benefícios esperados<br/>
<span class="paragraph">Uma vez que seja a escolha correta, só resta então usufruir de tudo que ela tem a agregar nos lugares a qual é explorada.

<style>
.paragraph {
    margin-left: 50px;
}
</style>
