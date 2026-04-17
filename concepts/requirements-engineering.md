# Engenharia de Requisitos (Requirements Engineering)

## O que é

Engenharia de Requisitos é o processo de descobrir, documentar e validar o que um sistema precisa fazer — antes de qualquer linha de código ser escrita. É a ponte entre o problema do cliente e a solução técnica da equipe de desenvolvimento.

O processo começa com uma pergunta simples: **o que o sistema precisa fazer?** Mas responder essa pergunta bem é difícil. Clientes raramente sabem exatamente o que querem, expressam necessidades de forma vaga ou contraditória, e frequentemente descobrem novos requisitos durante a conversa. O papel do analista é conduzir esse processo de forma estruturada.

As técnicas mais comuns de coleta são:

| Técnica | Quando usar |
|---------|-------------|
| Entrevista | Quando há um ou poucos stakeholders com conhecimento profundo |
| Questionário | Quando há muitos usuários e pouco tempo disponível |
| Observação | Quando o processo já existe e o sistema vai digitalizá-lo |
| Workshop | Quando vários stakeholders precisam alinhar visões diferentes |
| Análise de documentos | Quando há manuais, formulários ou sistemas legados como referência |

Após a coleta, os requisitos são organizados, classificados (funcionais ou não funcionais), priorizados e documentados de forma que possam ser validados com o cliente e usados como base para o desenvolvimento.

## Como é usado neste projeto

O projeto simulou uma entrevista real com a responsável pela Bergaworks Money — Marianne Bergami — conduzida pelo professor durante a aula. A Giselle assistiu à entrevista, tomou notas e extraiu os requisitos a partir do que foi dito.

O processo seguiu as etapas clássicas da engenharia de requisitos:

```
Entrevista com a cliente (perguntas abertas → mapeamento de problemas)
        ↓
Identificação de urgências, causas e possíveis soluções
        ↓
Perguntas fechadas para confirmar regras de negócio específicas
        ↓
Resumo do projeto e validação com a cliente
        ↓
Documentação dos requisitos funcionais e não funcionais
        ↓
Criação dos diagramas de caso de uso e classes
```

## Exemplo do projeto

Um trecho da entrevista revelou que a empresa tinha uma funcionária com deficiência visual. Esse detalhe, capturado durante a conversa, gerou dois requisitos diretamente:

- **RF01** — Controle de Acesso por Voz (a interface precisa ser acessível por voz)
- **RNF01** — Acessibilidade (o sistema deve priorizar interface por comando de voz)

Sem uma entrevista bem conduzida, essa necessidade poderia nunca ter sido capturada.

## Recursos para aprofundamento

- [SWEBOK — Requirements Engineering](https://www.computer.org/education/bodies-of-knowledge/software-engineering) — guia oficial da IEEE sobre engenharia de software
- [Ian Sommerville — Software Engineering](https://www.pearson.com/en-us/subject-catalog/p/software-engineering/P200000003268) — referência clássica com capítulo dedicado a requisitos
