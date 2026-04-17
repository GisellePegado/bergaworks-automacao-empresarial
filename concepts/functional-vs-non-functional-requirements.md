# Requisitos Funcionais e Não Funcionais (Functional vs Non-Functional Requirements)

## O que é

Todo sistema tem dois tipos de requisitos: os que descrevem **o que ele faz** e os que descrevem **como ele deve ser**. Saber diferenciar os dois é uma das habilidades centrais do analista de sistemas.

### Requisitos Funcionais (RF)

Descrevem as **funções e comportamentos** que o sistema deve executar. São as ações que o sistema realiza em resposta a entradas ou eventos. A pergunta-chave para identificá-los é:

> *"O que o sistema deve fazer?"*

Características dos requisitos funcionais:
- Descrevem funcionalidades concretas e observáveis
- Têm um ator que dispara a ação ou um evento que a aciona
- Podem ser testados diretamente: ou o sistema faz aquilo ou não faz
- Geralmente geram casos de uso no diagrama UML

**Exemplos gerais:** "O sistema deve permitir login com CPF e senha", "O sistema deve enviar e-mail de confirmação após o cadastro".

### Requisitos Não Funcionais (RNF)

Descrevem as **qualidades e restrições** do sistema — as condições sob as quais ele deve operar. A pergunta-chave é:

> *"Como o sistema deve funcionar?"*

Características dos requisitos não funcionais:
- Descrevem propriedades do sistema como um todo, não funções específicas
- Afetam a arquitetura, tecnologia e infraestrutura escolhidas
- São mais difíceis de testar — exigem métricas claras ("em menos de 2 segundos", "disponível 99,9% do tempo")
- Frequentemente são restrições impostas por regulações, hardware ou preferências do cliente

As categorias mais comuns de RNF são: desempenho, segurança, usabilidade, confiabilidade, manutenibilidade e compatibilidade.

**Exemplos gerais:** "O sistema deve responder em menos de 2 segundos", "Os dados devem ser armazenados em servidor local".

### Como diferenciar na prática

Uma técnica simples: tente completar a frase com o requisito em questão.

- *"O sistema deve **[verbo de ação]**..."* → provavelmente funcional
- *"O sistema deve **[ser/ter/funcionar]**..."* → provavelmente não funcional

Outra forma: pergunte se o requisito descreve uma **funcionalidade** (algo que o sistema faz) ou uma **qualidade** (como o sistema se comporta). Se for qualidade, é não funcional.

## Como é usado neste projeto

O projeto coletou 6 requisitos funcionais e 6 não funcionais a partir da entrevista com a Bergaworks Money. A distinção ficou clara na prática:

| Tipo | Exemplo do projeto | Justificativa |
|------|-------------------|---------------|
| RF | RF01 — Controle de Acesso por Voz | Descreve uma ação concreta: o sistema *permite* acesso via voz |
| RF | RF04 — Detecção de Presença | Descreve uma função: o sistema *identifica* presença por câmeras |
| RNF | RNF01 — Acessibilidade | Descreve uma qualidade: o sistema deve *ser* acessível |
| RNF | RNF03 — Conectividade Limitada | Descreve uma restrição: o sistema deve *funcionar* com internet limitada |

Note que RF01 e RNF01 estão relacionados ao mesmo tema (acesso por voz), mas descrevem dimensões diferentes: o RF diz *o que* o sistema faz, o RNF diz *como* ele deve fazer para ser acessível.

## Exemplo do projeto

```
Situação identificada na entrevista:
  "Uma funcionária do RH tem deficiência visual e precisa usar o sistema."

Requisito Funcional gerado (o que o sistema faz):
  RF01 — O sistema deve permitir acesso a ambientes controlados
         através de comandos de voz.

Requisito Não Funcional gerado (como o sistema deve ser):
  RNF01 — O sistema deve ser acessível para pessoas com deficiência
           visual, priorizando a interface por comando de voz.
```

## Recursos para aprofundamento

- [IREB — Glossary of Requirements Engineering](https://www.ireb.org/en/cpre/cpre-glossary/) — definições formais usadas na certificação internacional de analistas
- [W3Schools — Software Requirements](https://www.w3schools.com/soft/) — introdução prática a requisitos de software
