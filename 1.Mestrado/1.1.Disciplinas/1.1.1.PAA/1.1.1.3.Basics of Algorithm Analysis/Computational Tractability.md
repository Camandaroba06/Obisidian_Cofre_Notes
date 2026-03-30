Tratabilidade Computacional

Um dos principais focos deste livro é encontrar algoritmos eficientes para problemas computacionais. Nesse nível de generalidade, nosso tema parece abranger toda a ciência da computação; então, o que há de específico em nossa abordagem aqui?

Primeiramente, tentaremos identificar temas amplos e princípios de design no desenvolvimento de algoritmos. Buscaremos problemas e abordagens paradigmáticas que ilustrem, com o mínimo de detalhes irrelevantes, as abordagens básicas para projetar algoritmos eficientes. Ao mesmo tempo, seria inútil buscar esses princípios de design isoladamente, portanto, os problemas e as abordagens que consideramos são extraídas de questões fundamentais que surgem em toda a ciência da computação, e um estudo geral de algoritmos acaba servindo como um bom panorama de ideias computacionais que surgem em muitas áreas.

Outra propriedade compartilhada por muitos dos problemas que estudamos é sua natureza fundamentalmente discreta. Ou seja, como o Problema do Emparelhamento Estável, eles envolverão uma busca implícita sobre um grande conjunto de possibilidades combinatórias;
e o objetivo será encontrar eficientemente uma solução que satisfaça certas condições claramente definidas.

Ao buscarmos compreender a noção geral de eficiência computacional, focaremos principalmente na eficiência em tempo de execução: queremos algoritmos que sejam executados rapidamente. Mas é importante que os algoritmos também sejam eficientes no uso de outros recursos. Em particular, a quantidade de espaço (ou memória) usada por um algoritmo é uma questão que também surgirá em vários pontos do livro, e veremos técnicas para reduzir a quantidade de espaço necessária para realizar um cálculo.

---
### Algumas tentativas iniciais de definir eficiência.

A primeira grande questão que precisamos responder é a seguinte: Como devemos
transformar a noção vaga de um algoritmo “eficiente” em algo mais concreto?

Uma primeira tentativa de uma definição funcional de eficiência é a seguinte.

==Definição Proposta de Eficiência (1): Um algoritmo é eficiente se, quando implementado, ele for executado rapidamente em instâncias de entrada reais.==


Vamos dedicar um tempo para considerar esta definição. Em certo nível, é difícil discordar: um dos objetivos fundamentais do nosso estudo de algoritmos é resolver problemas reais rapidamente. E, de fato, existe uma área significativa de pesquisa dedicada à implementação cuidadosa e à análise de desempenho de diferentes algoritmos para problemas computacionais discretos.

Mas há alguns pontos cruciais ausentes nesta definição, mesmo que nosso objetivo principal seja resolver instâncias de problemas reais rapidamente em computadores reais. O primeiro
ponto é a omissão de onde e quão bem implementamos um algoritmo. Mesmo algoritmos ruins podem ser executados rapidamente quando aplicados a pequenos casos de teste em processadores extremamente rápidos; mesmo bons algoritmos podem ser executados lentamente quando codificados de forma descuidada. Além disso, o que é uma instância de entrada “real”? Não conhecemos toda a gama de instâncias de entrada que serão encontradas na prática, e algumas instâncias de entrada podem ser muito mais difíceis do que outras. Finalmente, esta definição proposta acima não considera o quão bem, ou mal, um algoritmo pode escalar à medida que os tamanhos dos problemas crescem para níveis inesperados. Uma situação comum é que dois algoritmos muito diferentes terão desempenho comparável em entradas de tamanho 100; multiplique o tamanho da entrada por dez, e um ainda será executado rapidamente enquanto o outro consumirá uma enorme quantidade de tempo.


O que poderíamos pedir é uma definição concreta de eficiência que seja independente de plataforma, independente de instância e com valor preditivo em relação ao aumento do tamanho das entradas. Antes de nos concentrarmos em quaisquer consequências específicas dessa afirmação, podemos pelo menos explorar sua sugestão implícita e de alto nível: que precisamos adotar uma visão mais matemática da situação.

Podemos usar o Problema do Emparelhamento Estável como um exemplo para nos guiar. A entrada tem um parâmetro de “tamanho” natural N; poderíamos considerá-lo como o tamanho total da representação de todas as listas de preferências, já que é isso que qualquer algoritmo para o problema receberá como entrada. N está intimamente relacionado ao outro parâmetro natural neste problema: n, o número de homens e o número de mulheres. Como existem 2n listas de preferências, cada uma de comprimento n, podemos considerar N = 2n², suprimindo detalhes mais refinados de como os dados são representados. Ao considerar o problema, procuraremos descrever um algoritmo em alto nível e, em seguida, analisar seu tempo de execução matematicamente como uma função do tamanho da entrada N.