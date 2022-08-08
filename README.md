# Resumo livro domain drive design
- Dominio
  - representação de um contexto do negócio, como por exemplo: alocação de produtos no estoque 
  - aonde encontra-se o problema
- subdominio
  - quando o dominio e complexo, nos os dividimos 
- Modelo
  - o conhecimento do domínio, ou seja, as regras de negócio. 
  - solução para o problema
- contexto delimitado
  - relação entre o modelo com o do dominio 

## Tipos de subdominios - pertence a parte do problema
- coredomain (exemplo empresa de vendas)
  - atividade do dominio, que diferencia o negócio
- subdomínios de suporte
  - da suporte ao domain (operação principal, ex: logística, fiscal, que fornecem dados ou atividades ao core domain)
- subdominios genericos
  - nao tem relação direta com o coredomain (financeiro, rh, contabilidade, muitas vezes atendidos por softwares de prateleira)

## Linguagem onipresente
- time técnico falar a mesma lingua do negócio
- se ater a complexidade do negócio

## Entidade
- Possui um identidade, onde representa que aquele instancia é unica
- Pode possuir atribudos que são "objetos de valor"
- não pode ser anêmico, ou seja, a falta de informações do dominio

## Objetos de valor
- Não possui uma identidade unica
- Podem ser compartilhados entre as entidades
- Ideal que sejam imutáveis

## Serviços
- Serviço da aplicação lida com as entradas e respostas da mesma
- Serviço de infra estrutura cuida de comunicações externas ou tratativas de baixo nível
- Serviço de dominio lidam com regras de negócio:
  -  que não fazem sentido ficar na entidade
  -  orquestram chamadas de regras na entidade

## Granularidade
- Classes de domínio muito pequenas, tendem que suas regras vazam para o serviço ou pior, a camada da aplicação
- Classes de dominio coesas e com a granularidade certa, deixam para os serviços apenas orquestrarem as chamadas.

## Módulo
- Os módulos devem ser coesos, assim minimiza o acoplamento com outros módulos
- o módulo deve contar uma história, ou seja, objetos (classes) que pertencem ao mesmo contexto de negócio.

## Agregador
- Conjunto de objetos, que se relacionam e pertencem ao mesmo contexto.
- A comunicação com esse conjunto é realizado via entidade raiz, ou seja, o objeto mestre.
- obs: essa entidade deve ter um identificador unico.
- os objetos de valores também podem ter identificadores unicos, mas valem apenas dentro do agregador.


### Fabrica do agregador
- Quando a criação do modelo é complexo, faz a necessidade de uma fabrica
- ela faz parte do dominio mas não do modelo, ou seja, a função é apenas criar o agregador
- pode-se criar parte do agregador e este ser populado no decorrer do seu ciclo de vida
- o cliente não pode criar a entidade, caso esta seja complexa, nesse caso chamar a fabrica
