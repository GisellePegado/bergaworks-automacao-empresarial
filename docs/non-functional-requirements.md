# Requisitos Não Funcionais

> Levantados a partir de entrevista com a responsável pela Bergaworks Money.  
> Os requisitos não funcionais descrevem **como o sistema deve se comportar**.

---

| ID | Categoria | Descrição |
|----|-----------|-----------|
| RNF01 | Acessibilidade | O sistema deve ser acessível para pessoas com deficiência visual, priorizando a interface por comando de voz. |
| RNF02 | Segurança de Dados | O sistema deve manter os dados de reconhecimento facial e controle de acesso em um servidor local, garantindo a privacidade e segurança das informações. |
| RNF03 | Conectividade Limitada | O sistema deve funcionar com acesso limitado à internet, utilizando conexão apenas para o serviço de WhatsApp para envio de notificações. |
| RNF04 | Eficiência Energética | O sistema deve ser capaz de reduzir o consumo de energia desligando luzes e equipamentos quando não houver pessoas nos ambientes. |
| RNF05 | Disponibilidade | O sistema deve operar continuamente no horário de funcionamento da empresa, garantindo que os recursos estejam disponíveis durante todo o expediente. |
| RNF06 | Manutenibilidade | O sistema deve ser desenvolvido considerando a necessidade de manutenção periódica, facilitando intervenções técnicas sem comprometer o funcionamento geral. |

---

## Como foi identificado cada requisito

Os requisitos não funcionais descrevem **características de qualidade** do sistema — não o que ele faz, mas como ele deve fazer. Emergem de restrições técnicas, culturais ou operacionais identificadas durante a entrevista.

> Exemplo: A informação de que o sistema ficaria em servidor interno, sem conexão ampla com a internet, originou o RNF03 — Conectividade Limitada.

> Exemplo: A presença de uma funcionária com deficiência visual na equipe que usaria o sistema tornou a acessibilidade um requisito não funcional prioritário — RNF01.
