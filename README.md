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

Exemplo básico de ASL:
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
