# Diagrama de Caso de Uso (Use Case Diagram)

## O que é

O Diagrama de Caso de Uso é um diagrama UML que representa as **interações entre os usuários do sistema (atores) e as funcionalidades que o sistema oferece (casos de uso)**. Seu objetivo é mostrar *quem* usa o sistema, *o que* pode ser feito e *como* as funcionalidades se relacionam entre si — sem entrar em detalhes de implementação.

É um dos primeiros artefatos criados na análise de um sistema porque comunica o escopo de forma visual e acessível tanto para a equipe técnica quanto para o cliente.

### Como construir um Diagrama de Caso de Uso

**Passo 1 — Identificar os atores**

Atores são entidades externas que interagem com o sistema. Podem ser pessoas (usuários, administradores), outros sistemas ou dispositivos. A pergunta para identificá-los é: *"Quem usa ou é afetado pelo sistema?"*

No diagrama, atores são representados por um boneco palito com o nome abaixo.

```
        O
       /|\      ← ator
       / \
    Funcionário
```

**Passo 2 — Identificar os casos de uso**

Casos de uso são as funcionalidades do sistema do ponto de vista do ator. A pergunta é: *"O que o ator precisa fazer com o sistema?"* ou *"O que o sistema faz para o ator?"*

No diagrama, casos de uso são representados por elipses com o nome dentro, dentro de um retângulo que representa a fronteira do sistema.

```
┌─────────────────────────┐
│       Sistema           │
│   ╔═══════════════╗     │
│   ║ Registrar     ║     │
│   ║ Entrada       ║     │
│   ╚═══════════════╝     │
└─────────────────────────┘
```

**Passo 3 — Conectar atores a casos de uso**

Uma linha sólida entre o ator e o caso de uso indica que aquele ator pode realizar aquela ação.

**Passo 4 — Identificar relacionamentos entre casos de uso**

Dois relacionamentos especiais existem entre casos de uso:

- **`<<include>>`** — o caso de uso base **sempre** executa o caso de uso incluído. É obrigatório. Usado quando uma funcionalidade é parte integrante de outra.
  - Exemplo: "Monitorar Segurança" sempre inclui "Reconhecer Face" — não existe monitoramento sem reconhecimento.

- **`<<extend>>`** — o caso de uso estendido **pode ou não** ser executado, dependendo de uma condição. É opcional.
  - Exemplo: "Monitorar Segurança" pode estender "Notificar Presença não Autorizada" — a notificação só acontece *se* uma pessoa não cadastrada for detectada.

A seta vai sempre do caso de uso dependente em direção ao caso de uso base:
- `<<include>>`: a seta sai do caso base → aponta para o incluído
- `<<extend>>`: a seta sai do caso estendido → aponta para o base

**Passo 5 — Identificar herança entre atores**

Se um ator herda todos os casos de uso de outro, usa-se uma seta de generalização (triângulo vazio). No diagrama, `CEO` herda de `Administrador do Sistema`, pois tem acesso a tudo que o administrador tem, mais funcionalidades exclusivas.

## Como é usado neste projeto

O diagrama do projeto tem 6 atores e 12 casos de uso para o sistema de automação da Bergaworks Money. Cada requisito funcional mapeou para pelo menos um caso de uso:

| Requisito | Caso de Uso |
|-----------|-------------|
| RF01 — Acesso por Voz | Acessar Ambientes Controlados → Processar Comando de Voz |
| RF02 — Automação de Iluminação | Gerenciar Iluminação → Ajustar Automaticamente Dispositivos |
| RF03 — Controle de Ar-Condicionado | Gerenciar Climatização → Ajustar Automaticamente Dispositivos |
| RF04 — Detecção de Presença | Gerenciar Climatização / Iluminação → Detectar Presença no Ambiente |
| RF05 — Reconhecimento Facial | Monitorar Segurança → Reconhecer Face |
| RF06 — Notificação de Acesso | Monitorar Segurança → Notificar Presença não Autorizada |

Os relacionamentos `<<include>>` indicam funcionalidades obrigatórias (Monitorar Segurança *sempre* Reconhece Face). Os `<<extend>>` indicam funcionalidades condicionais (Desligar Dispositivos Quando Vazio só ocorre *se* não houver presença detectada).

## Exemplo do projeto

```
Ator: Funcionárias do RH
  │
  ├──→ Acessar Ambientes Controlados
  │         │
  │         ├── <<include>> ──→ Processar Comando de Voz
  │         └── <<extend>>  ──→ Notificar Presença não Autorizada
  │
  └──→ Gerenciar Iluminação
            │
            └── <<extend>> ──→ Desligar Dispositivos Quando Vazio
```

## Recursos para aprofundamento

- [UML Diagrams — Use Case Diagram](https://www.uml-diagrams.org/use-case-diagrams.html) — referência completa da notação UML
- [Lucidchart — How to Draw a Use Case Diagram](https://www.lucidchart.com/pages/uml-use-case-diagram) — guia prático com exemplos visuais
- [PlantUML — Use Case](https://plantuml.com/use-case-diagram) — ferramenta usada para gerar o diagrama deste projeto
