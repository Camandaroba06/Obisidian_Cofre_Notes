---
sticker: emoji//1f470
---


Nesse capítulo iniciaremos com uma breve introdução feita pelo livro do kleinberg.

## O problema

Para introduzir a questão, vamos pensar informalmente sobre algum tipo de informação que pode ser levantada como um grupo de amigos, todos de nível Júnior na faculdade de CC, aplicando para empresas para entrevistas de verão. O ponto crucial desse processo de aplicação é a relação entre dois tipos de grupos diferentes:
- Empresas
- Estudantes
Cada estudante (ou aplicador) tem suas **preferências** de empresas ordenadamente e cada empresa (após terem recebido todos os currículos) tem suas **preferências** de estudantes ordenadamente. Baseando-se nessas preferencias, companias ofertam para algum dos estudantes, estudantes escolhem qual dessas ofertas aceitar, e pessoas vão saindo da maratona de entrevistas de verão (por terem sido contratadas?).

Gale e Shapley acreditam que a ordenação desses pares de empregados e empresas pode acabar acontecendo de um jeito errado caso não tenha nada para reforçar isso.

Imagine um exemplo, seu amigo Raj acabou de ser aceito para a maior empresa de telecomunicações CluNet. Alguns dias depois, a pequena startup WebExodus, que vinha arrastando algumas decisões finais, chama Raj para ser empregado deles. Agora, Raj acaba preferindo WebExodus ao invés de CluNet (talvez por questões pessoais) e essa nova oferta leva ele a rejeitar seu emprego da CluNet para ir a WebExodus. Com a perda de um funcionário, CluNet oferta um emprego para um dos seus candidatos em lista de espera, que prontamente rejeitam ofertas de outras empresas como a Babelsoft, e a situação começa a virar uma bola de neve fora de controle.


As coisas parecem tão ruins, ou até piores, do outro lado da moeda. Suponha que a amiga de Raj, Chelsea, que iria para a Babelsoft, mas acabou de ouvir a história de Raj, ligue para o pessoal da WebExodus e diga: "Sabe, eu preferiria muito mais passar o verão com vocês do que na Babelsoft." Eles acham isso muito fácil de acreditar; e, além disso, ao analisarem a candidatura de Chelsea, percebem que prefeririam tê-la contratado em vez de algum outro estudante que realmente está programado para passar o verão na WebExodus. Nesse caso, se a WebExodus fosse uma empresa um pouco menos escrupulosa, poderia muito bem encontrar alguma maneira de retirar a oferta feita a esse outro estudante e contratar Chelsea em vez disso.

É bem possível que prefiramos a seguinte situação, mais estável, na qual o próprio interesse impede que as ofertas sejam retiradas e redirecionadas. Considere outro aluno que combinou de passar o verão na CluNet, mas liga para a WebExodus e revela que também preferiria trabalhar para eles. Mas, nesse caso, com base nas ofertas já aceitas, eles podem responder: “Não, acontece que preferimos todos os alunos que aceitamos a você, então receamos que não há nada que possamos fazer”. Ou considere um empregador que, empenhado em entrar em contato com seus melhores candidatos que foram para outros lugares, ouve de cada um deles: “Não, estou feliz onde estou”. Nesse caso, todos os resultados **são estáveis** ​​— não há mais acordos externos que possam ser feitos.

Então, esta é a pergunta que Gale e Shapley fizeram: Dado um conjunto de preferências entre empregadores e candidatos, podemos atribuir candidatos a empregadores de forma que para cada empregador E e cada candidato A que não esteja escalado para trabalhar para E, pelo menos uma das duas situações a seguir seja verdadeira?
- E prefere o que foi aceito do que A; ou
- A prefere sua empresa atual que E.

Se isso for cumprido, o interesse individual irá impedir qualquer empregador/aplicador de realizar ofertas por debaixo dos panos.


### Formulando o Problema

Para pegar a essência desse conceito, e ajudar a tornar o problema o mais claro possível. As Empresas e Aplicadores apresentam algumas assimetrias que podem gerar confusão. Cada aplicante costuma olhar para uma vaga e cada empresa olha para vários aplicantes.

Pode ser útil, ao menos no começo, eliminar essas complicações e chegar a algo mais "básico": cada um dos *n* aplicantes aplica para cada uma das *n* empresas, e cada empresa quer aceitar **APENAS UM** aplicante.

Seguindo Gale e Shapley, nós observamos que esse caso especial pode ser visto como o problema de conceber um sistema que cada um dos *n* homens e *n* mulheres pode acabar casando: Nosso problema naturalmente é análogo a dois "gêneros" (aplicantes e empresas) e no caso, nós estamos considerando que cada um está olhando para um casamento monogâmico e de sexo oposto.

Então, considere um conjunto *M* = $\{m_1,m_2,...,m_n\}$ de $n$ homens, e um conjunto *W* = $\{w_1,w_2,...,w_n\}$ de $n$ mulheres. Seja *M x W* denotado como o conjunto de todas as possibilidade de pares ordenados na forma $(m,w)$, em que $m \in M$ e $w \in W$. Um matching *S* é um conjunto de pares ordenados em que cada valor de *M x W*, com a propriedade de que cada membro de *M* e cada membro de *W* aparece em no máximo um par ordenado de *S*. Um **Matching Perfeito** *S'* é um matching com a propriedade de que cada membro de *M* e cada membro de *W* aparece em EXATAMENTE um par de *S'*.

Cada homem $m \in M$ rankeia todas as mulheres; Aqui diremos que cada $m$ prefere $w$ do que $w'$ se $m$ rankear $w$ mais alto do que $w'$. O nome que daremos a esse ranking será **Lista de Preferências**. Não ha empate no ranking. Cada mulher, analogamente, rankeia os homi tbm.

Dado um casamento perfeito S' (o livro volta a chamar de S por algum motivo, ent vo usar S), o que pode dar de errado ? Seguindo a motivação inicial em termos de empregados e aplicantes, nós deveríamos nos preocupar com a seguinte situação: Há dois pares $(m,w)$ e $(m',w')$ em S (Figura 1.1) com a propriedade de que $m$ prefere $w'$ do que seu atual parceiro $w$; e $w'$ prefere $m$ do que seu atual parceiro $m'$. Nesse caso, não há nada que impeça $m$ e $w'$ de abandonarem seus parceiros atuais e casarem juntos, ai entra aquela ideia lá do começo de esse trem não ser "self-enforcing". Nós vamos dizer que esse par $(m,w')$ é uma **INSTABILIDADE** com respeito a S: $(m,w')$ não estão presentes em S, massss cada um deles $m$ e $w'$ prefere um ao outro do que seus atuais parceiros em S, oq ameaça a integralidade de S como estrutura de casamento perfeito.
<center><p align="left"><center></center></p></center>
![[Pasted image 20260328161048.png]]

Com tudo isso que foi dito aqui, o objetivo principal é gerar um conjunto de casamentos SEM INSTABILIDADES. Nós vamos dizer que S é **estável** se (i) é perfeito, e (ii) não há instabilidades com respeito a S.

Duas questões podem ser imediatamente levantadas:
- Há algum casamento estável para todo conjunto de listas de preferências?
- Dados um conjunto de listas de preferências, podemos eficientemente construir um casamento estável se houver algum ?

---

### Alguns Exemplos

Para ilustrar essas definições, considere as seguintes 2 instâncias de Stable Matching Problem.

Primeiro, suponha que você tenha 2 elementos homem $\{m,m'\}$, e 2 elementos mulher $\{w,w'\}$. As listas de preferências são:

$m$ prefere $w$ do que $w'$
$m'$ prefere $w$ do que $w'$


$w$ prefere $m$ do que $m'$
$w'$ prefere $m$ do que $m'$

Se nós pensarmos sobre esse conjunto de listas de preferências intuitivamente, isso representa um acordo completo: Os homens preferem a mesma sequência de mulheres, e as mulheres preferem a mesma sequência de homens. Com isso, há apenas um caso de Casamento Estável que é o caso em que S for formado por $(m,w) e (m',w')$, uma vez que m prefere w e w prefere m esse casamento seria formado e não ameaçado pelos demais, levando a m' e w' se casarem pela lista de preferências. O outro Casamento Perfeito (mas não estável) seria o caso de S ser formado por $(m',w) e (m,w')$, que não seria estável, uma vez que há um par ordenado que não está presente em S que ameaça sua existência, que é o par $(m,w)$, uma vez que m prefere w ao invés do seu parceiro atual w' e w prefere m ao invés de seu parceiro atual m'. Dessa forma, m e w terminariam os casamentos com m' e w' para casarem entre si formando $(m,w)$.

A seguir, um exemplo onde as coisas são um pouco mais complicadas. Suponha a preferência

$m$ prefere $w$ do que $w'$
$m'$ prefere $w'$ do que $w$
$w$ prefere $m'$ do que $m$
$w'$ prefere $m$ do que $m'$

O que acontece agora ? Os 2 homens tem preferências que combinam perfeitamente com cada um (as mulheres estão rakeadas de maneira oposta), e as duas mulheres tem as preferências acontecendo tbm rankeadas de maneira oposta. A preferência dos homens entra em conflito com a preferência das mulheres.

Neste segundo exemplo, há duas Stable Matchings. Uma delas consite em S ser composta pelos pares $(m,w)$ e $(m',w')$, que é estável devido ao fato de eu não conseguir formar um par ordenado que não está presente em S de tal modo que ameace sua existência, devido a esse conflito de interesses entre homens e mulheres. O outro casamento estável seria S composto por $(m,w')$ e $(m',w)$ que devido aos interesses conflitantes entre homens e mulheres não formariam uma instabilidade. Nesse caso, pelo que entendi do assunto, o conjunto S formado seria dependente sentido do proponente.

**Com isso, nota-se que é possível para uma mesma instância haver mais de uma Stable Matching**

---

### Design do Algoritmo


Nós vamos mostras agora que existe um Stable Matching para todo conjunto de listas de preferências entre homens e mulheres. Além disso, nós mostrarmos isso ira responder também uma outra pergunta feita lá em cima: É possível fazer isso com algum algoritmo de maneira eficiente para construir essas Stable Matching ?

Algumas ideias basicas que motivaram o algoritmo:
- Inicialmente, todos estão **Não Casados**. Suponhamos que um homem não casado $m$ escolha a mulher $w$ que é o ranking mais alto de usa lista de preferências e **propõe** para ela. Podemos declaram imediatamente que $(m,w)$ serão nossos pares no Stable Matching final ? Não necessariamente: Em algum momento futuro algum outro homem $m'$ pode **propor** para $w$ por preferir ela. Por outro lado, pode ser perigoso para $w$ rejeitar $m$ agora mesmo; Ela pode nunca mais receber a proposta de alguém que ela rankeia como mais alto que $m$. Então uma ideia natural seria ter o par $(m,w)$ entrar em um estado intermediario - **Noivado**.
- Suponha agora que o estaco com que alguns homens e mulheres são **Solteiros** (não noivados) e alguns são noivados. O próximo passo seria olhar para isso. Um homem solteiro qualquer $m$ escolhe a maior rankeada mulher $w$ para quem ele ainda não propôs, e ele propõe para ela. Se $w$ também for solteira, então $m$ e $w$ se tornam noivos. Por outro lado, $w$ já for noiva de outro homem $w'$, nesse caso, ela escolhe com qual homem ela vai noivar com base no ranking de machos entre $m$ ou $m'$, aquele que for maior em sua lista de preferências; Esse homem se torna noivo de $w$ e o outro se torna ou se mantém (depende doq ele era antes) solteiro.
- Finalmente, o algoritmo ira terminar quando **NINGUÉM mais estiver solteiro**, neste momento, todos os noivos são declarados no final, e o resultado é um casamento perfeito.

Aqui o código completin:


```python
Initially all m ∈ M and w ∈ W are free
While there is a man m who is free and hasn’t proposed to every woman
	Choose such a man m
	Let w be the highest-ranked woman in m’s preference list to whom m has not yet proposed
	If w is free then
		(m, w) become engaged
	Else w is currently engaged to m
		If w prefers m to m then
			m remains free
		Else w prefers m to m
			(m, w) become engaged
			m becomes free
		Endif
	Endif
Endwhile
Return the set S of engaged pairs
```

Embora o G-S algorithm seja fácil de afirmar/entender, ele não é obvio de visualizar que devolve um Stable Matching, ou um **Stable Matching perfeito**. Nós seguiremos a provar isso agora, através de uma sequência de fatos intermediários. 

---


### Analisando o Algoritmo

Primeiro considere a perspectiva da mulher $w$ durante a execução do algoritmo. Para um $while$, ninguém propôs para ela ainda, e ela está solteira. Então, um homem $m$ talvez proponha para ela, e ela torne-se noiva. Com o passar do tempo, ela deve receber propostas adicionais, aceitando aquelas que subirem no ranking de seus parceiros. Então, descobrimos:

==1.1) $w$ continua noiva do momento em que recebe a sua primeira proposta, e a sequência de parceiros os quais ela está noiva torna-se melhor e melhor. (subindo na lista de preferências).==

Pela perspectiva do homem $m$ durante a execução do algoritmo é diferente. Ele é solteiro até que ele proponha para a de maior ranking na lista; Neste momento ele pode ou não se tornar noivo. Com o passar do tempo, ele talvez alterne entre solteiro e noivo; de qualquer forma a seguinte propriedade acontece:

==1.2) A sequência de mulheres que $m$ propõe vai se tornando pior e pior (descendo na lista de preferências).==

Agora, mostraremos que o algoritmo termina, e fornece um número de iterações limitadas necessária para terminar.

==1.3) O G-S algorithm termina depois de no máximo $n^2$ iterações do $While$ loop.==

Proof.

Uma estratégia útil para limitação-superior do tempo de execução de um algoritmo como nós estamos tentando fazer aqui, é encontrar uma medida de **Medida de Progresso**. Nomeadamente, nós vemos algum caminho preciso de dizer que aquele passo tomado pelo algoritmo leva ele mais próximo da terminação.

Nesse caso do presente algoritmo, cada interação consiste em algum homem propondo (apenas uma vez) para uma mulher que ele nunca propôs antes. Então, se supormos *P(t)* denotado pelo conjunto de pares $(m,w)$ como o $m$ propôs para $w$ no fim da iteração t, nós vemos que para todo t, o tamanho de *P(t+1)* é estritamente maior que o tamanho de *P(t)*. mas há apenas $n^2$ possíveis pares de homens como mulheres ao todo, então o valor de *P(.)* pode crescer até no máximo $n^2$ vezes ao longo do algoritmo. Isso permite que hajam apenas no máximo $n²$ iterações.

Dois pontos valem a pena serem notados sobre esse fato anterior e a proof. Primeiro, haverão algumas execuções do algoritmo (com certas listas de preferências) que podem envolver algum número próximo de $n^2$ iterações, então essa análise não está tão longe da melhor possível. Segundo, existem alguns quantificadores que podem não funcionar tão bem para **Medida de Progresso** para o algoritmo, uma vez que eles podem não necessariamente crescer a cada iteração. Por exemplo, o número de indivíduos solteiros pode permanecer constante (pode surgir um novo noivado com a desfeita de um ja existente, com isso temos o número de solteiros mantido constante, por isso não é um bom quantificador/quantitativo) de uma iteração para outra, assim como o número de pares noivos (mesma ideia, um novo par de noivos pode surgir com a desfeita de outro par, logo o número de pares noivos permanece constante). Dessa forma, esses quantitativos podem não servir para serem usando diretamente para fornecer um limie superior de máximo de iterações possíveis, no mesmo estilo do parágrafo anterior.

