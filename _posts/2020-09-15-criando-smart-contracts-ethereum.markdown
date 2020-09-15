---
layout: page
title:  "Criando Smart Contracts para Ethereum"
date:   2020-09-15 11:30:00 -0300
categories: blockchain ethereum
---
<br>
<div class="row">
    <div class="col-sm-12" style="text-align:center">
        <img src="https://siasky.net/_A0bnl5t4UW8A47XXhHlF_f6IERxcEIjRdEGm4dRUQY3Lg">
    </div>
</div>
<br>
<br>

Como abordado no último post seguimos com essa série sobre a Ethereum, e hoje começamos a entrar em uma parte mais técnica, mas não se preocupe, mesmo que você não seja desenvolvedor creio que muito conteúdo aqui continua sendo proveitoso. Só lembrando que se você ainda não leu o último post seu conhecimento aqui fica limitado, isso não é uma crítica sobre suas capacidades, mas apenas porque o raciocínio vai se complementando conforme os posts vão sendo lidos, se for o caso clique <a href="{{ site.baseurl }}{% link _posts/2020-08-04-conhecendo-o-ethereum.markdown %}">aqui</a>, caso contrário vamos em frente que garanto que você vai gostar.
Ethereum talvez seja um dos protocolos mais rock star do momento, também pudera, o Ether é uma das criptomoeda mais rentáveis do mercado, pelo menos até o momento em que este post é produzido. E se você como eu gosta de descobrir como as coisas são feitas e as vezes até criar novas engrenagens, então precisamos falar um pouco sobre alguns tópicos que garantem o funcionamento de um smart contract na Ethereum, para então começar a desenvolver nosso próprio.
<br>
<br>


## <strong>Ethereum Virtual Machine(EVM) uma breve introdução
EVM é a parte do Ethereum que cuida do deploy e execução dos smart contracts. Podemos pensar na EVM como uma quase-turing complete machine, isso porque sistemas que sejam turing complete possuem programas que sejam escritos de maneira a encontrar alguma resposta, no entanto não há garantias do tempo ou memória gastos em sua execução. A EVM é, portanto, quase-turing complete, pelo fato do processamento que é gasto em sua execução ser determinado pela quantidade de <strong>gas</strong>.<br>
Podemos dividir esse conceito entre <strong>gas</strong> e <strong>gas price</strong>, onde gas é a medida utilizada para mensurar a computação que será executada, entenda o gas também como dinheiro a ser gasto para isso. Já o gas price é a quantidade de Ether equivalente para cada unidade de gas, onde o valor é medido por <strong>Gwei</strong> que seria apenas uma quantidade menor de Ether.
O problema todo ou na verdade solução, se da pelo fato de que a execução das transactions tem um custo pequeno se comparado ao valor do Ether, então é necessario medidas menores para fazer os calculos do custo computacional, para entender melhor 10 Gwei equivalem a 0.00000001 ETH por exemplo.
Não se preocupe vamos falar mais sobre o que é gas em instantes, por enquanto entenda como se fosse um combustível que será usado para processar um smart contract.<br>
Para que uma transação seja executada deve conter as informações sobre o gas a ser consumido, e claro, isso é relativo ao esforço que será gasto no processamento, portanto existe uma equivalência entre poder de computação e quantidade mínima de gás exigido, caso contrário, a transação não será executada e vai devolver a seguinte mensagem <strong>“run out of gas”</strong>.<br>
Apesar do termo “Virtula Machine” se referir normalmente a virtualização de uma máquina real com processador e memória, como VirtualBox por exemplo.<br>
A EVM limita-se apenas a prover uma abstração de armazenamento e computação de bytecodes, semelhante a JVM – Java Virtual Machine. O que possibilita smart contracts serem escritos em diferentes linguagens como Solidity e Vyper, uma vez que as instruções devem gerar bytecodes a serem executados posteriormente. Adentrar-se mais nesses conceitos da EVM pode ser um pouco maçante, portanto deixemos mais sobre esse conteúdo para um futuro post, o que você precisava entender até o momento já é suficiente para acompanhar.
<br>
<br>

## <strong>Gas, Fee & Gas Price
Imagine a seguinte situação, você tem 400 quilômetros de distância para percorrer com seu carro, e você sabe que ele tem um consumo médio de 10 quilômetros o litro do combustível.<br>
Presume-se, portanto, que seu gasto para chegar ao destino seja de 40 litros, para facilitar vamos ignorar qualquer tipo de variância e nos ater somente aos números inteiros. Caso você abasteça o carro com 30 litros ao invés de 40, inevitavelmente será impossível andar mais do que 300 quilômetros, como resultado em algum momento acenderá o alerta no painel do carro avisando que acabou o combustível.
Agora vamos calcular o gasto para esse percurso todo, se o preço do combustível está 3 reais o litro, o valor final ficaria em 40(litros) x 3(reais) = 120 reais. Parabéns você acabou de entender como funciona o conceito de gas e gas price na Ethereum, calma deixe-me explicar melhor.<br>
Todo smart contract possui uma quantidade de processamento especifica para sua execução na Ethereum (distância), e para que este seja computado pela EVM, é necessário uma certa quantidade de gas(combustível) correspondente para que consiga chegar ao final com o resultado do processamento. O gas price(preco do combustivel) pode ser calculado no site <a href="https://ethgasstation.info/">ETH Gas STATION</a> por exemplo.
Toda vez que a EVM vai executar alguma transação é alocado um gas supply equivalente ao valor do gas limit especificado. Caso o gas supply não for suficiente para pagar pelo valor da execução o processo é encerrado e a transação revertida. Veja então que o gas limit deve ser enviado junto da transaction para que a EVM possa fazer esse cálculo, e garantir a execução das instruções, já que para tal é necessário verificar se existe gas suficiente para isso. Dessa maneira problemas como ataque DDOS e falhas nos smart contracts, sejam propositais ou não, se limitam a quantidade de gas fornecido para execução, inviabilizando ataques e garantindo a segurança da rede.<br>
Quando a execução chega ao fim sem nenhum problema o valor gasto ou <strong>gas fee</strong>, é repassado para os <strong>miners</strong> e o restante já que não atingiu o gas limit, é devolvido para quem enviou a transaction. Caso contrário se a quantidade de gas for insuficiente para sua execução, será inevitável um <strong>“run out of gas”</strong>, o processo então será encerrado e a transação e o estado todo revertido, mas o valor gasto para execução até o momento é repassado para os miners já que houve o esforço gasto no processamento.
<br>
<br>

## <strong>Smart Contracts e Solidity
Muito bem, agora chegou a hora de colocar a mão na massa. Para criarmos um smart contract vamos usar o <a href="http://remix.ethereum.org/">Remix</a>, uma ferramenta open source para escrever os smart contracts usando a linguagem Solidity.<br>
Provavelmente essa será a interface com que irá se deparar:<br>
<img src="https://siasky.net/ZADHwkUNs2ETFrhIRU-uN0uqPKRmMSryVJEM3MRbUHpxtg" />


Antes de começar a codificar é necessário preparar nosso ambiente pois alguns plug-ins ficam inativos inicialmente na ferramenta. Para isso no painel esquerdo clique no ícone que se parece com uma tomada que o <strong>“PLUGIN MANAGER”</strong> vai abrir em seguida. Procure por <strong>“SOLIDITY COMPILER”</strong> nos plugins disponíveis, ou digite <strong>“compiler”</strong> na busca para encontrar o plugin que desejamos. Agora só clicar em <strong>“activate”</strong> e pronto, já podemos começar a programar. Esse plugin que acabamos de adicionar nada mais é do que o compilador necessário para gerar a versão do nosso contrato para deploy posteriormente<br>
<img src="https://siasky.net/IAB-ru3FbN-O823GrDaJoA7xm6Bxebbh_wZwL5QlApQdZw" />


Clique no ícone <strong>“+”</strong> para criar um novo arquivo com o nome de <strong>SimpleStorage.sol</strong>, este será nosso smart contract.<br>
<img src="https://siasky.net/EAAYSBTysAW-HQqHCC9RlSBb1pKju6Jye9SjM0DFZhbA9w" />
<br>
<br>
<img src="https://siasky.net/dABmw89USfP_pDvx1CGCUr2bfm31b295cf85I6O_INTegQ" />


Agora crie o smart contract com a codificação a seguir e vamos discutir um pouco sobre ele.<br>
<img src="https://siasky.net/MACYARwfxOxQJDPnGuXIsunFD77gtUYmil_V7uUklyB9Sg" />


<strong>Na linha 1</strong> a instrução que a colocarmos no nosso contrato é a versão em que será compilado <strong>^0.6.0</strong>, isso informa que o código foi construído para funcionar nas versões de compiladores <strong>até 0.7.0, mas não incluindo esta última em si</strong>.<br>
<img src="https://siasky.net/AACYIN8x0Q9ZeaezI2NpbF4wkm1_HibNHA34rW78c_joVg" />


<strong>Na linha 3</strong> definimos o nome do nosso contrato SimpleStorage usando a keyword contract, vale ressaltar que o nome do contrato não necessariamente precisa ter o mesmo nome do arquivo que criamos, poderia por exemplo ter nomeado como simplesmente storage.sol que não haveria impacto algum, mas por questões de boas práticas devemos sempre ter o nome do arquivo como nome do contrato e também fazer uso de CamelCase, para mais informações sobre boas práticas em solidity de uma olhada em sua <a href="https://solidity.readthedocs.io/en/v0.6.12/style-guide.html">documentação completa</a>.<br>
<img src="https://siasky.net/AABrnW4yuYW_INuK1k42F6PfXEtZqv1oD94lZKuHWHI8kw" />


<strong>Linha 5</strong> Definimos uma variável do tipo integer, mas antes de seguirmos adiante, dê uma olhada nos tipos de dados que são aceitos pelo solidity.<br>
<img src="https://siasky.net/AACgB7ao1Mmjoya7WZWpvZafqaGricrbYVSdKeKIDsEjdA" />


Lembrando que não vamos escovar os bits de cada tipo de dados aqui, caso queira entender mais a fundo você pode acessar a documentação completa nesse <a href="https://solidity.readthedocs.io/en/v0.6.12/types.html">link</a>.<br>
<strong>Tipos de dados no Solidity</strong>
<ul>
    <li>
        <strong>bool:</strong> true e false
    </li>
    <li>
        <strong>int & uint:</strong> int(signed) e uint(unsigned), são disponíveis com intervalos de int8 – int256 e uint8 – uint256, incrementados em passos de 8. Se faz necessário um certo cuidado com os cálculos, uma vez que por exemplo uint32 é o mesmo que 2**32-1, caso uma operação entre dois números nesse tipo de dado ultrapassar o limite será feito um truncate e vai causar perca de precisão. Se não tratado corretamente, isso pode causar sérios efeitos colaterais ao funcionamento de seu smart contract.
    </li>
	<li>
        <strong>string:</strong> O tipo string não tem muito segredo, aceita caracteres da tabela ASCII e pode ser escrito usando aspas simples <strong>‘solidityStr’</strong> ou duplas <strong>“solidityStr”</strong>, o diferencial é que pode ser quebrado em múltiplas partes por exemplo: <strong>“solidity”</strong>  <strong>“Str”</strong> é o mesmo que <strong>“solidityStr”</strong>, além disso são implicitamente convertidos em bytes <strong>(byte1 – byte32)</strong>, o que possibilita por exemplo fazer atribuições como <strong>byte32 strAsByte = “solidityStr”</strong>.
    </li>

</ul>
Voltando agora para a <strong>linha 5</strong>, com nossa variável <strong>data</strong> do tipo <strong>uint256</strong> podemos armazenar números inteiros sem sinal, de maneira que possibilite criar alguma lógica posterior no smart contract
<br>
<br>

Na <strong>Linha 7</strong> declaramos uma <strong>function</strong> que recebe um parâmetro do tipo <strong>uint256</strong> e o atribui para nossa <strong>state variable</strong> chamada <strong>data</strong>

<img src="https://siasky.net/CAACpDPLMe2qhLvX3WPFq6EQVVfGAkDokXPx-6UHDno3cQ" />


Gostaria de discutir alguns conceitos antes de prosseguirmos. Existem 3 locais para se armazenar os dados na EVM <strong>storage, memory e stack</strong>, esse último é utilizado para manter apenas pequenas variáveis locais e apesar de livre para uso pode lidar apenas com informações de tamanho pequeno.<br>
No caso do <strong>storage</strong> é o local onde todas as <strong>state variables</strong> como a nossa <strong>“data”</strong> são armazenados. E por último, mas não menos importante <strong>memory</strong> é usado para manter informações temporárias, portanto considere que para esse tipo entre uma chamada e outra da function os valores não serão mantidos. Acho que ficou claro que quando estamos falando de <strong>storage</strong> é um local onde mantemos informações importantes, que podem ser acessadas sempre que necessário dentro do nosso smart contract.
Ainda na linha 7 nossa function <strong>“setData”</strong> possui visibilidade pública, e o que determina isso é a keyword <strong>public</strong>. Uma função pode ser declarada como <strong>external, public, internal ou private</strong>. Deixar nossa function como public implica em permitir sua visualização tanto dentro como fora do smart contract.
Os outros tipos de visibilidade podem ser vistos nesse link da <a href="https://solidity.readthedocs.io/en/v0.6.12/contracts.html#visibility-and-getters">documentação</a>, mas em outros posts também vamos fazer uso deles e será explicado em mais detalhes. Por fim na <strong>linha 11</strong> apenas atribuímos o valor que é passado por parâmetro para nossa variável <strong>data</strong> (Lembre-se isso vai para dentro do storage).
A única diferença da function <strong>getData</strong> para <strong>setData</strong> é que getData não recebe parâmetro algum e retorna o valor da variável <strong>data</strong> que foi mantido no storage.<br>
<img src="https://siasky.net/CADzERCVSf6wuZAJdEUPuZMMSNO8GR4lUAFF4z3w8mhuWA" />

Mas podemos observar que além de <strong>public</strong> tem mais 2 novos keywords na declaração, <strong>view</strong> e <strong>returns(uint256)</strong>. Functions que são declaradas como <strong>view</strong> simplesmente não alteram o estado, ou no caso não modificam o storage. Já que estamos somente retornando o valor da variável podemos marcar como view, algo interessante é que view functions quando chamadas diretamente não geram custo nenhum em termos de gas.<br>
Em solidity quando queremos retornar algo de alguma function é necessário especificar essa informação, por isso então que colocamos o <strong>returns(uint256)</strong> em sua declaração, isso informa que retornaremos esse tipo dado.

Para testar nosso contrato precisamos fazer deploy dele, mas não se preocupe a conta e a network são apenas para testes. Então volte para barra lateral da esquerda e você vai ver um ícone em formato do Ethereum como na imagem. Clique nele e um painel de deploy será aberto <strong>“DEPLOY & RUN TRANSACTIONS”</strong>.<br>
<img src="https://siasky.net/BACQqaiPMD1tJvYHSHykSsa4koPPMS7nFEvq9xv3Om_bGg" />

Não é necessário modificar nada, apenas garanta que o <strong>ENVIROMENT</strong> esteja como <strong>Javascript VM</strong> e o CONTRACT <strong>SimpleStorage</strong> esteja selecionado, feito isso só clicar em <strong>Deploy</strong> que a mágica vai acontecer.<br>
Podemos observar que na última linha do painel foi criado um dropdown list para o contrato que foi feito deploy, basta expandi-lo que já podemos começar a testar.<br>
Coloque qualquer número no input e clique no botão <strong>setData</strong>.<br>
<img src="https://siasky.net/IABELkfzI9YUJWNZKUyq-YqAiSkqghYR7P8wj2PeYUCZHw" />

É Possivel observar a validação de uma trasaction na parte dos logs, e se clicarmos em <strong>getData</strong> o número adicionado deve retornar na response.<br>
<img src="https://siasky.net/IABQSYBXWcehy3kFBNgLJzROdd0KqV0QApijVB_HftNlpQ">

Parabéns você acabou de criar, fazer deploy e testar seu primeiro smart contract, tente modificar o código e adicionar outras variáveis de storage, crie uma lógica diferente e exercite esse conhecimento, garanto que não será difícil e vai te tornar mais familiarizado com a linguagem. Para o próximo post vamos entrar em tópicos um pouco mais avançados, além de mostrar como fazer cobertura de testes para garantir a qualidade do nosso contrato, por hora paramos por aqui.

Qualquer duvida entre em contato por <a href="/contact/">aqui</a> ou pelo <a href="https://www.linkedin.com/in/erion-ricardo-barasuol-82722a30/">linkedin</a>, obrigado pela sua atenção, um abraço e até a próxima.


<style>
.paragraph {
    margin-left: 50px;
}
</style>