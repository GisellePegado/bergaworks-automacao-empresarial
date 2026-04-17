# Conversão de Requisitos em Classes (Requirements to Classes)

## O que é

Converter requisitos em classes é o processo que transforma as necessidades descritas em linguagem natural — os requisitos funcionais — em estruturas orientadas a objetos que o sistema vai implementar. É a ponte entre a análise (o quê o sistema faz) e o design (como o sistema é estruturado internamente).

O processo parte de uma premissa da orientação a objetos: o mundo real é composto por **objetos** que têm características (atributos) e comportamentos (métodos). O papel do analista é identificar quais objetos do domínio do problema precisam existir no sistema.

### O processo passo a passo

**Passo 1 — Extrair substantivos dos requisitos**

Leia cada requisito funcional e sublinhe todos os substantivos. Cada substantivo é um candidato a classe. Não filtre ainda — anote todos.

```
RF01: "O sistema deve permitir que funcionários acessem ambientes
       controlados através de comandos de voz."

Substantivos encontrados:
  sistema, funcionário, ambiente, comando, voz
```

**Passo 2 — Filtrar os candidatos**

Nem todo substantivo vira classe. Aplique os filtros:

| Situação | Decisão |
|----------|---------|
| Representa uma entidade com dados e comportamentos próprios | ✅ Virar classe |
| É apenas um atributo de outra classe | ❌ Virar atributo |
| É redundante ou sinônimo de outro | ❌ Eliminar |
| É um conceito muito vago ou genérico | ❌ Eliminar ou refinar |

No exemplo acima:
- `sistema` → ✅ classe `SistemaAutomacao`
- `funcionário` → ✅ classe `Usuario`
- `ambiente` → ✅ classe `Ambiente`
- `comando de voz` → ❌ atributo ou parâmetro de método (não tem vida própria)

**Passo 3 — Definir atributos de cada classe**

Para cada classe, volte aos requisitos e pergunte: *"Que dados precisamos guardar sobre este objeto?"*

Os atributos vêm dos detalhes dos requisitos e das regras de negócio:

```
RF01 menciona que apenas 4 pessoas específicas podem usar voz.
→ Usuario precisa de: tipo (CEO, Diretor, Funcionário RH, Funcionário Comum)
→ Usuario precisa de: whatsAppNumero (para receber notificações — RF06)
```

**Passo 4 — Definir métodos de cada classe**

Métodos vêm dos **verbos** dos requisitos — as ações que o sistema executa:

```
RF01: "permitir que funcionários acessem ambientes"
→ Usuario.acessarAmbiente(ambiente: Ambiente): Boolean

RF06: "enviar mensagens via WhatsApp"
→ Usuario.receberNotificacao(mensagem: String, imagem: Imagem): void
```

**Passo 5 — Identificar os relacionamentos**

Com as classes definidas, identifique como elas interagem. Os relacionamentos emergem dos requisitos que envolvem mais de uma entidade:

```
RF04: "câmeras identificam presença nos ambientes"
→ CameraReconhecimento vigia Ambiente (associação)
→ Ambiente monitora SensorPresenca (composição — sensor pertence ao ambiente)
```

## Como é usado neste projeto

A pergunta da atividade foi exatamente esta: *"Como fazemos para converter um requisito ou grupo de requisitos em uma classe?"*

A resposta aplicada no projeto seguiu o processo acima. Exemplo completo com RF05 e RF06:

```
RF05: "O sistema deve identificar através de câmeras se as pessoas
       presentes estão cadastradas no banco de dados."

RF06: "O sistema deve enviar mensagens via WhatsApp para a CEO
       quando identificar pessoas não cadastradas."

Substantivos: câmera, pessoa, banco de dados, mensagem, imagem
Classes geradas: CameraReconhecimento, Usuario, Imagem

Atributos de CameraReconhecimento (extraídos do comportamento descrito):
  -id: Integer
  -status: Boolean

Métodos de CameraReconhecimento (extraídos dos verbos dos requisitos):
  +capturarImagem(): Imagem          ← RF05: câmera captura
  +reconhecerUsuario(): Usuario      ← RF05: identifica se está cadastrado
  +detectarAcessoNaoAutorizado(): Boolean  ← RF05: verifica cadastro
  +notificarAcessoNaoAutorizado(imagem: Imagem): void  ← RF06: envia notificação

Relacionamento identificado:
  CameraReconhecimento ──captura──→ Imagem  (associação 1:*)
  CameraReconhecimento ──notifica──→ Usuario (associação 0:*)
```

## Exemplo do projeto

```
Requisito → Substantivos → Classe → Atributos + Métodos

RF03: "O sistema deve gerenciar o funcionamento dos aparelhos
       de ar-condicionado (ligar/desligar e ajustar temperatura)
       de forma automática."

Substantivos: sistema, aparelho de ar-condicionado, temperatura
Classe: DispositivoArCondicionado

Atributos:
  -id: Integer
  -status: Boolean
  -temperatura: Double

Métodos (dos verbos ligar, desligar, ajustar):
  +ligar(): void
  +desligar(): void
  +ajustarTemperatura(valor: Double): void
  +verificarStatus(): Boolean
  +calcularConsumo(): Double
```

## Recursos para aprofundamento

- [Martin Fowler — Analysis Patterns](https://martinfowler.com/books/ap.html) — padrões de extração de classes do domínio do problema
- [UML Diagrams — Class Diagram](https://www.uml-diagrams.org/class-diagrams-overview.html) — referência completa da notação UML para classes
