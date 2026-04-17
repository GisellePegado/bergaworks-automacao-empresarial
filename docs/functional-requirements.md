# Requisitos Funcionais

> Levantados a partir de entrevista com a responsável pela Bergaworks Money.  
> Os requisitos funcionais descrevem **o que o sistema deve fazer**.

---

| ID | Nome | Descrição |
|----|------|-----------|
| RF01 | Controle de Acesso por Voz | O sistema deve permitir que 4 pessoas específicas (1 diretor e 3 funcionárias do RH) acessem ambientes controlados através de comandos de voz, com foco na acessibilidade para a funcionária com deficiência visual. |
| RF02 | Automação de Iluminação | O sistema deve controlar a iluminação dos ambientes através de comandos de voz, permitindo ligar e desligar luzes sem restrição de usuários. |
| RF03 | Controle Automatizado de Ar-Condicionado | O sistema deve gerenciar o funcionamento dos aparelhos de ar-condicionado (ligar/desligar e ajustar temperatura) de forma automática, sem necessidade de intervenção dos funcionários. |
| RF04 | Detecção de Presença | O sistema deve identificar a presença de pessoas nos ambientes através de câmeras para automatizar o funcionamento de luzes e equipamentos. |
| RF05 | Reconhecimento Facial para Acesso | O sistema deve identificar através de câmeras se as pessoas presentes estão cadastradas no banco de dados. |
| RF06 | Notificação de Acesso não Autorizado | O sistema deve enviar mensagens via WhatsApp para a CEO quando identificar pessoas não cadastradas no banco de dados. |

---

## Rastreabilidade: RF × Casos de Uso

| Requisito | Caso de Uso relacionado |
|-----------|------------------------|
| RF01 | Acessar Ambientes Controlados → Processar Comando de Voz |
| RF02 | Gerenciar Iluminação → Ajustar Automaticamente Dispositivos |
| RF03 | Gerenciar Climatização → Ajustar Automaticamente Dispositivos |
| RF04 | Gerenciar Climatização / Gerenciar Iluminação → Detectar Presença no Ambiente |
| RF05 | Monitorar Segurança → Reconhecer Face |
| RF06 | Monitorar Segurança → Notificar Presença não Autorizada |

---

## Como foi identificado cada requisito

Os requisitos funcionais emergem das **funções que o sistema deve executar** — ou seja, o que ele faz. Durante a entrevista, foram mapeados os problemas e as necessidades da empresa, transformando cada necessidade concreta em um requisito com ID, nome e descrição objetiva.

> Exemplo: A necessidade de "ligar e desligar luzes sem precisar tocar em interruptores" originou o RF02 — Automação de Iluminação.
