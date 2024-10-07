# AWS Step Functions

## Visão Geral

**AWS Step Functions** é um serviço da Amazon Web Services (AWS) que facilita a orquestração de microserviços e outras funções distribuídas. Ele permite a criação de fluxos de trabalho complexos e automatiza processos usando uma abordagem visual e declarativa. É ideal para aplicações que envolvem múltiplas etapas que precisam ser coordenadas de maneira sequencial ou paralela.

### Principais Conceitos

- **State Machine (Máquina de Estados)**: Representa o diagrama de estados que define o fluxo de trabalho. Cada **estado** pode ser uma tarefa simples ou uma operação mais complexa.
  
- **Tasks (Tarefas)**: Estados que executam operações específicas, como invocar uma função Lambda ou interagir com serviços da AWS.

- **Tipos Especiais de Estados**: 
  - **Pass**: Passa os dados de um estado para o próximo.
  - **Wait**: Pausa a execução por um período específico.
  - **Fail** e **Succeed**: Indicadores de finalização com falha ou sucesso, respectivamente.

- **ASL (Amazon States Language)**: Linguagem JSON usada para definir o fluxo de estados e transições.

## Documentação Oficial

A documentação oficial da AWS Step Functions está disponível aqui. Ela inclui guias, exemplos de uso, e a referência completa da linguagem **Amazon States Language (ASL)**.

## Workflow Studio & ASL (Amazon States Language)

### Workflow Studio

O **Workflow Studio** é uma interface visual que permite criar fluxos de trabalho de maneira gráfica. Ele oferece a capacidade de:

- Arrastar e soltar componentes para construir fluxos de trabalho.
- Visualizar as transições entre estados.
- Integrar serviços AWS sem a necessidade de código manual.

### Amazon States Language (ASL)

O **Amazon States Language** é uma linguagem baseada em JSON usada para definir fluxos de trabalho no Step Functions. Ele permite especificar como os estados transitam entre si e incorporar lógica de controle, como loops e condicionais.

Exemplo básico de ASL (json):
```json

{
  "Comment": "Exemplo de uma Máquina de Estados",
  "StartAt": "HelloWorld",
  "States": {
    "HelloWorld": {
      "Type": "Pass",
      "Result": "Olá, Mundo!",
      "End": true
    }
  }
} 

```

## Precificação e Custos

A precificação do AWS Step Functions é baseada em duas métricas principais:

- **Número de Transições**: Cada vez que um estado transita para outro, é contabilizada uma transição.
- **Duração da Execução**: No caso do **Express Workflows**, há cobrança adicional pela duração da execução do fluxo de trabalho.

### Modelos de Preços

- **Standard Workflows**: Ideal para fluxos de trabalho de longa duração com poucas execuções. Exemplo de custo: $0.025 por 1.000 transições.
- **Express Workflows**: Adequado para execuções rápidas e em alto volume. Exemplo de custo: $1.00 por 1 milhão de invocações e $0.00000417 por GB-segundo de execução.

Para detalhes específicos de preços, consulte a [página de precificação da AWS](https://aws.amazon.com/step-functions/pricing/).

## Permissões

As permissões para usar o AWS Step Functions são gerenciadas através do **AWS Identity and Access Management (IAM)**. As políticas de permissões controlam:

- Quem pode criar, modificar ou deletar máquinas de estado.
- Quem pode iniciar ou parar execuções.
- O acesso a outros serviços AWS integrados.

### Exemplo de política de IAM:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "states:StartExecution",
        "states:StopExecution",
        "states:DescribeExecution",
        "states:ListExecutions"
      ],
      "Resource": "arn:aws:states:us-east-1:123456789012:stateMachine:MyStateMachine"
    }
  ]
}
```

## Conclusão

O AWS Step Functions oferece uma maneira simples e poderosa de orquestrar workflows e microserviços. Com o **Workflow Studio**, fica fácil criar fluxos de trabalho visuais, enquanto o **ASL** oferece flexibilidade para lógicas mais complexas. A precificação é baseada no número de transições e na duração de execução, e as permissões são configuradas usando políticas IAM, garantindo controle e segurança.

## Links Úteis

- [Documentação Oficial](https://docs.aws.amazon.com/step-functions/)
- [Precificação](https://aws.amazon.com/step-functions/pricing/)

