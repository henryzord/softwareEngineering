# Test-Driven Development

O desenvolvimento orientado a testes (TDD, Test-Driven Development) foi inicialmente proposto por Kent Beck como parte
integrante da metodologia Extreme Programming (XP)[^1]. A ideia é que o desenvolvedor escreva os testes _antes_ de 
começar a desenvolver a nova funcionalidade. É considerada uma técnica de design de software, e não de testes. 

Segundo Prikladinicki[^1], o Desenvolvimento orientado a testes deve seguir os seguintes passos:

1. Escreva um teste automatizado, antes de escrever qualquer código de produção.
2. Execute o teste. Ele **deve** falhar! Isso prova que a funcionalidade ainda não foi implementada.
3. Como o **teste** funciona mas o código-fonte que deveria satisfazer o teste ainda não, isso quer
   dizer que temos conhecimento de uma nova funcionalidade que deve ser implementada, e **como** ela
   deve ser implementada.
4. Implemente o código-fonte que satisfaz as condições do teste.

O primeiro passo consiste em escrever um teste automatizado para uma funcionalidade que ainda não foi implementada. 
Apesar de parecer estranho, é bem fácil de fazer, já que se escreve o que se espera da funcionalidade antes de 
implementá-la, evitando vícios de implementação. A segunda consiste em aplicar [refatoração](REFATORACAO.md), uma 
técnica que visa mudar a implementação interna do código-fonte sem contudo mudar seu comportamento externo.

Os testes também podem ser utilizados como documentação do software, dado que descrevem no decorrer do tempo as 
funcionalidades implementadas (por um software de controle de versão, como o git).

Segundo Sommerville[^2], um diagrama de fluxo do Desenvolvimento Dirigido a Testes seria o seguinte:

```mermaid
flowchart LR
    A("Identificar nova funcionalidade")
    B("Escrever teste")
    C("Executar o teste")
    D("Implementar<br>funcionalidade<br>e refatorar")
    if{"Falhou?"}

    A --> B
    B --> C
    C --> if
    if -- "sim" --> D
    if -- "não" --> A
    D --> C
```

>[!WARNING]
> Atenção! Testes unitários não são testes automatizados!
> 
> Com frequência, testes unitários são implementados de maneira automatizada. Porém, isto não é uma obrigatoriedade!
> Na verdade, outros tipos de teste podem ser também automatizados, como testes de integração (através de um framework
> como por exemplo [selenium](https://www.selenium.dev/)).


## Tipos de teste de software

### Unitários

Os testes unitários verificam pequenas funcionalidades de um componente. Por exemplo, se tivermos uma classe 
`Calculadora`, podem-se escrever tantos testes unitários quanto forem os métodos da calculadora (e.g. `testaSoma`, 
`testaMultiplicacao`, etc).

### De Componentes

Um teste de componente assume um componente completo (e.g. `Calculadora`) de forma isolada, testando sua lógica interna
e sua interação com interfaces externas. Outros componentes **não são** testados em conjunto quando testa-se um 
componente em específico; são usadas entradas simuladas (mock ups), com um retorno esperado. Por exemplo, para testar
o método `soma` da classe `Calculadora`, simula-se a digitação de dois números, com o resultado esperado já conhecido.

### Integração

Os testes de integração verificam a interface entre componentes e como eles se comunicam. Por exemplo, pode-se testar 
como um componente `Teclado` coleta as informações digitadas pelo usuário e as repassa para o componente `Calculadora`.

### Funcionais/Aceitação

São testes que avaliam o sistema do ponto de vista da interface externa (por exemplo, a interface Web de um site), 
levando em consideração a perspectiva do usuário final que fará uso do software. Testes funcionais garantem que o 
sistema realiza as funções esperadas, enquanto testes de aceitação validam que o sistema atende aos requisitos acordados 
com o cliente ou usuário final.

## Escrevendo testes unitários

O repositório [CTISM-Prof-Henry/softwareTesting](https://github.com/CTISM-Prof-Henry/softwareTesting) traz exemplos de como
escrever testes unitários automatizados nas linguagens Java, Python e Javascript.

## Cobertura

A cobertura de um conjunto de testes automatizados e unitários de software consiste em calcular quantos % do código está
coberto (executado) pelos testes. Apesar de não ser uma relação 1:1 para a qualidade do software (por exemplo, um 
software pode estar totalmente coberto por testes unitários automatizados e ainda assim não fazer o que o cliente 
espera), é desejável que pelo menos a maioria do código-fonte seja testado antes de ser colocado em produção.

O repositório [CTISM-Prof-Henry/softwareTesting](https://github.com/CTISM-Prof-Henry/softwareTesting) traz exemplos de como
calcular a cobertura de testes nas linguagens Java, Python e Javascript.

## Bibliografia

[^1]: Prikladinicki, R., de Almeida, E. S., & de Souza, J. T. (2014). Métodos ágeis para desenvolvimento de software. 
Disponível [neste link](https://integrada.minhabiblioteca.com.br/reader/books/9788582602089). Acesso em 30/07/2025.
[^2]: Sommervile, I. Engenharia de Software. 9ª Edição. (2011).
