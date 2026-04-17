# Diagrama de Classes (Class Diagram)

## O que é

O Diagrama de Classes é um diagrama UML que representa a **estrutura estática do sistema** — as classes que o compõem, seus atributos, métodos e os relacionamentos entre elas. É o principal artefato da modelagem orientada a objetos e serve como base para a implementação do código.

Enquanto o Diagrama de Caso de Uso mostra *o que* o sistema faz do ponto de vista do usuário, o Diagrama de Classes mostra *como* o sistema é estruturado internamente.

### Como construir um Diagrama de Classes

**Passo 1 — Identificar as classes**

Classes são as "coisas" do domínio que o sistema precisa representar e manipular. Para encontrá-las, analise os requisitos buscando por **substantivos** — nomes de entidades, objetos ou conceitos relevantes.

Uma classe é representada por um retângulo dividido em três compartimentos:

```
┌─────────────────────┐
│      NomeClasse     │  ← nome da classe
├─────────────────────┤
│ -atributo: Tipo     │  ← atributos (dados)
│ -outro: Tipo        │
├─────────────────────┤
│ +metodo(): Retorno  │  ← métodos (comportamentos)
│ +outro(): void      │
└─────────────────────┘
```

**Passo 2 — Definir atributos e métodos**

Atributos são as **características** da classe — os dados que ela armazena. Métodos são os **comportamentos** — as ações que ela pode executar.

A visibilidade é indicada por um símbolo antes do nome:
- `+` público — acessível por qualquer classe
- `-` privado — acessível apenas pela própria classe
- `#` protegido — acessível pela classe e suas subclasses

**Passo 3 — Definir os relacionamentos**

| Relacionamento | Símbolo | Significado |
|----------------|---------|-------------|
| Associação | linha sólida | Uma classe "conhece" outra |
| Composição | losango preenchido | Uma classe "é parte" de outra; não existe sem ela |
| Agregação | losango vazio | Uma classe "tem" outra; pode existir independentemente |
| Herança | triângulo vazio | Uma classe "é um tipo de" outra (generalização) |
| Dependência | seta tracejada | Uma classe "usa" outra temporariamente |
| Realização | seta tracejada com triângulo | Uma classe implementa uma interface |

**Passo 4 — Definir multiplicidades**

A multiplicidade indica quantas instâncias de uma classe se relacionam com quantas de outra, semelhante à cardinalidade do MER:

```
1      → exatamente um
0..*   → zero ou muitos
1..*   → um ou muitos
0..1   → zero ou um (opcional)
```

### Como extrair classes dos requisitos

O processo parte dos requisitos funcionais e dos casos de uso já identificados:

1. **Liste todos os substantivos** relevantes nos requisitos — cada um é um candidato a classe
2. **Elimine os redundantes** — sinônimos, atributos disfarçados de entidade
3. **Valide com o domínio** — a classe precisa ter dados (atributos) e comportamentos (métodos) próprios para justificar sua existência
4. **Identifique os relacionamentos** — como as classes interagem entre si para realizar os casos de uso

## Como é usado neste projeto

A extração de classes partiu dos requisitos e do diagrama de caso de uso. Os substantivos relevantes identificados foram: sistema, usuário, ambiente, dispositivo de iluminação, ar-condicionado, sensor, câmera, imagem.

Cada um virou uma classe com atributos extraídos dos requisitos:

| Classe | Origem no requisito |
|--------|-------------------|
| `SistemaAutomacao` | RF03 — sistema gerencia funcionamento dos dispositivos |
| `Usuario` | RF01 — sistema permite que pessoas específicas acessem |
| `Ambiente` | RF02/RF03 — sistema controla iluminação e climatização *dos ambientes* |
| `DispositivoIluminacao` | RF02 — sistema controla a *iluminação* |
| `DispositivoArCondicionado` | RF03 — sistema gerencia *ar-condicionado* |
| `SensorPresenca` | RF04 — sistema *identifica presença* |
| `CameraReconhecimento` | RF05 — sistema *identifica* pessoas por câmeras |
| `Imagem` | RF05/RF06 — câmera captura *imagem* para reconhecimento e notificação |

## Exemplo do projeto

```
RF05: "O sistema deve identificar através de câmeras se as pessoas
       presentes estão cadastradas no banco de dados."

Substantivos encontrados: câmera, pessoa, banco de dados
Classes geradas:
  - CameraReconhecimento (a câmera que faz o reconhecimento)
  - Usuario (a pessoa que pode ou não estar cadastrada)

Método extraído do comportamento descrito:
  CameraReconhecimento
    +reconhecerUsuario(): Usuario
    +detectarAcessoNaoAutorizado(): Boolean
    +notificarAcessoNaoAutorizado(imagem: Imagem): void
```

## Recursos para aprofundamento

- [UML Diagrams — Class Diagram](https://www.uml-diagrams.org/class-diagrams-overview.html) — referência completa com todos os tipos de relacionamento
- [Lucidchart — Class Diagram Tutorial](https://www.lucidchart.com/pages/uml-class-diagram) — guia visual passo a passo
- [PlantUML — Class Diagram](https://plantuml.com/class-diagram) — ferramenta usada para gerar o diagrama deste projeto
