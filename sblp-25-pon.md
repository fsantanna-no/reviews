# Resumo

O artigo propõe a implementação de um compilador para o Paradigma Orientado
a Notificações (PON).
A implementação em C++ se baseia em namespaces, ao invés de OO.
Essa abordagem mantém uma estrutura de código legível, mas ao mesmo tempo
evita chamadas extras desnecessárias, proporcionando ganhos de desempenho.
Os experimentos mostram um ganho de desempenho para um cenário de rede de
sensores, uma vez que a semântica da linguagem evita testes desnecessários,
além dos ganhos com a técnica de namespaces.

# Pontos fortes

- A percepção e a discussão sobre redundâncias temporais e estruturais.
- A técnica escolhida para o compilador proposto.

# Pontos fracos

- A discussão sobre paradigmas de programação.
- As técnicas e paradigmas escolhidos como base de comparação de desempenho.
- A complexidade dos experimentos e bases de comparação.

# Avaliação

- Sobre o PON

O artigo coloca o PON como um novo paradigma de programação, ao lado do PI e
PD.
Depois, na Seção 3.1 o descreve como declarativo, mas mostra um exemplo
baseado em testes e mudanças de estado típicos do PI.
Toda essa discussão está um pouco confusa no artigo.
O PD é um conceito muito vago, que pode abranger desde SQL até linguagens
funcionais, então não fica muito claro o objetivo dessa discussão.
Além disso, e principalmente, o PON se parece muito com técnicas de
programação orientadas a eventos, padrão observador, programação de streams,
etc.
Diversos termos como lógico-casual, facto-execucional, orientação a regras e
a fatos, etc possuem conceitos análogos nessas outras abordagens.
Na opinião desse revisor, seria mais produtivo uma comparação com essas
técnicas similares.
Em particular, seria interessante destacar qual é o fator mais fundamental que
distingue o PON dessas outras abordagens.

- Sobre as Redundâncias

Essa discussão é interessante, mas utiliza um exemplo um pouco simples e, de
certa forma, ingênuo, pois utiliza a técnica de polling.

Em termos de desempenho, esse não é o "estado da arte", nem mesmo no PI.
O mais comum é utilizar bibliotecas orientadas a eventos para eliminar essas
redundâncias estruturais e temporais.
Do ponto de vista temporal, as callbacks são chamadas somente na ocorrência de
eventos de interesse.
Do ponto de vista estruturas, as callbacks poderiam "unificar" os testes de
interesse para cada tipo de ocorrência.
O artigo menciona que "mesmo técnicas como orientação a eventos não resolvem
a questão, ainda que podendo mitigá-la", mas não apresenta mais explicações.
Na opinião desse revisor, o exemplo escolhido é uma espécie de "espantalho",
e uma comparação com um código orientado a eventos seria mais interessante.

No mundo do PD, existem soluções baseadas em dataflow e streams que também
eliminam tais redundâncias.
Essas alternativas não são discutidas no artigo.

- Sobre o Resumo, Introdução e Conclusão

Essas seções, em particular o Resumo, possuem diversos termos pouco
conhecidos que confundem o que é contribuição do que é trabalho anterior.
Além disso, o uso de voz passiva também dificulta identificar as reais
contribuições do trabalho.
Esse revisor entendeu que a contribuição central é a nova implementação
baseada em namespaces, e que o resto são trabalhos anteriores do mesmo grupo.
Essa diferenciação poderia ficar mais clara no texto.

- Sobre a implementação NPCPP

A contribuição central do artigo é a implementação de um novo compilador.
Em particular, a contribuição é o uso de namespaces para evitar chamadas a
construtores e auto-referências `this` que carregam um certo overhead.

Por outro lado, evitar o uso de objetos torna impossível instanciar entidades
do PON em tempo de execução.
Por exemplo, não seria possível instanciar "modelos" do PON para tratar
transações dinâmicas, tais como conexões de rede dinâmicas em um servidor.
Seria interessante discutir as limitações da abordagem.

A descrição do processo de notificações no final da página 4 não é muito
diferente dos sistemas orientados a eventos.
Novamente, seria interessante comparar com esses sistemas.

- Sobre os Experimentos

O cenário da Rede de Sensores parece extremamente simples para tirar
conclusões sobre desempenho.
O sistema inteiro possui um sensor e um atuador e uma máquina de estados sem
nenhuma complexidade.
Esse revisor não conseguiu acessar o link para o código fonte, então não foi
possível verificar a sua complexidade.
De qualquer forma, seria interessante explicar o Código 2, que parece
relativamente grande para a especificacao da segunda linha da Seção 5.1.
Uma outra questão é a escolha da implementação em C++ OO, que é sabidamente
ineficiente.
Na opinião desse revisor, seria mais interessante comparar com um código
orientado a eventos.
Dado que o programa é relativamente pequeno, uma opção ainda mais
interessante seria criar um progama "ótimo" em C++ manualmente, sem
redundâncias temporais e estruturais.
Esse programa serviria como um benchmark base para comparar as diferentes
abordagens.

Sobre o cenário do Bitonic Sort, esse revisor não entendeu a sua motivação.
Além de ser um cenário desfavorável ao PON em termos de desempenho, qual
seria a motivação em termos semânticos ou de expressividade?

- Avaliação geral

Esse revisor entende que o artigo ainda precisa de melhorias para ser aceito.
Seguem as principais considerações:

- O artigo poderia se focar inteiramente nas contribuições propostas.
  As discussões sobre paradigmas e o PON poderiam ser reduzidas ou eliminadas.
  Dessa forma, o Resumo, Introdução e Seções 2 e 3 poderiam ser mais
  orientadas às contribuições.
- O exemplo que motiva o trabalho poderia ser implementado com técnicas
  existentes mais próximas da proposta, tais como POE. Além disso, as
  discussões e comparações poderiam seguir nesse mesmo caminho. Nessa mesma
  linha, o artigo não possui uma seção de trabalhos relacionados, que poderia
  ser incluída reduzindo as seções sugeridas.
- O experimento é demasiadamente simples, além de se basear em uma comparação
  com uma implementação sabidamente ineficiente. As sugestões de comparação
  com POE ou com um benchmark manual não trariam grandes dificuldades de
  implementação.
