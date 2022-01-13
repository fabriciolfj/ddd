# Resumo livro domain drive design
- Dominio
  - representação de um contexto do negócio, como por exemplo: alocação de produtos no estoque 
- Modelo
  - o conhecimento do domínio, ou seja, as regras de negócio. 

## Entidade
- Possui um identidade, onde representa que aquele instancia é unica
- Pode possuir atribudos que são "objetos de valor"

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
