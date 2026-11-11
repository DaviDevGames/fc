# Riscos, decisões e auditoria

[Índice](README.md) · [Glossário e rastreabilidade →](12-glossario-e-rastreabilidade.md)

## Premissas a validar

| ID | Hipótese | Validação / prazo sugerido |
| --- | --- | --- |
| SUP-01 | 7v7 e 2 × 90 s são divertidos e legíveis em 5 polegadas | Cinco pessoas, M3 |
| SUP-02 | Câmera portrait e minimapa são jogáveis | Três aparelhos reais, M3 |
| SUP-03 | Quatro formações geram variedade suficiente | Playtest M6 |
| SUP-04 | Seis atributos diferenciam atletas | TST-007, M6 |
| SUP-05 | Economia apertada gera tensão sem frustração | TST-010 e playtest, M7 |
| SUP-06 | Áudio CC0/sintetizado serve à identidade | Protótipo sonoro M5 |
| SUP-07 | Simulação Poisson parece justa em relação a jogar | TST-021 e feedback, M7 |
| SUP-08 | Pixel art 32 × 32 é suficiente | Revisão visual M2 |
| SUP-09 | Um dev entrega todo Must em oito semanas a 12 h/semana | Refutada pelo próprio GDD; revisar também soma do backlog |
| SUP-10 | Dicas contextuais dispensam tutorial separado | Playtest M5 sem instrução prévia |

## Riscos

| ID | Risco | Mitigação ou plano B |
| --- | --- | --- |
| RSK-01 | Escopo não cabe no prazo original | Decidir A/B/C, reestimar; A recomendado |
| RSK-02 | IA não é crível ou justa | Simular e testar; ajustar erro e reação |
| RSK-03 | Série A injusta | Medir vitórias; reduzir multiplicador se necessário |
| RSK-04 | Similaridade com propriedade real | Nomes/escudos fictícios e revisão jurídica |
| RSK-05 | Áudio inadequado ou licença ambígua | Auditar licenças; sintetizar ou desabilitar áudio |
| RSK-06 | Câmera retrato confusa | Playtest, minimapa e indicador; eventual landscape |
| RSK-07 | Ausência de spin reduz variedade | Testar; curva simplificada pós-corte se necessário |
| RSK-08 | FPS insuficiente em Android | Medição em hardware; modo low e menos efeitos |
| RSK-09 | Corrupção ou quota causam perda | Backup, validação, tratamento de falhas e exportação |
| RSK-10 | Vazamento de listeners | Limpeza de cena e TST-023 |
| RSK-11 | Economia trava a carreira | TST-010; recalibrar receitas e custos |
| RSK-12 | Feature creep | Congelar recorte e manter lista de exclusões |

## Decisões pendentes

| ID | Questão | Dono | Gatilho |
| --- | --- | --- | --- |
| TBD-01 | Portrait funcional ou landscape obrigatório? | Usuário | Antes de M5 |
| TBD-02 | Escudo apenas forma/cor ou editor? | Usuário | Antes de M6 |
| TBD-03 | Assistir simulação automática na partida rápida? | Usuário | Antes de M6 |
| TBD-04 | Nomes das dificuldades e divisões? | Usuário | Antes de M6 |
| TBD-05 | Gamepad no MVP? | Usuário | Antes de M7 |
| TBD-06 | Confirmar pt-BR apenas na v1.0 | Usuário | Antes de M7 |
| TBD-07 | Hospedagem: itch.io, GitHub Pages, Vercel ou outra? | Usuário | Antes de M8 |
| TBD-08 | Quantidade e fase de playtests externos? | Usuário + dev | S4 e S7 |
| **TBD-09** | **A Vertical Slice, B MVP enxuto ou C MVP completo?** | **Usuário** | **Antes de M1; bloqueante** |

Recomendações do GDD, não decisões adicionais: A; landscape-first com portrait funcional; escudo simples; Série A–D.

## Conflitos que exigem resolução

Estas observações foram identificadas na organização do material e **não alteram o escopo aprovado**:

1. **Estimativa:** soma dos 30 itens Must é 43,5 dias, não 47,5 informados. O calendário de oito semanas também inclui carreira completa, embora o texto diga que isso não cabe no prazo.
2. **Bônus angular do chute:** `clamp(0,20 − 0,0006 × distância, 0, 0)` é sempre zero. Além disso, o limiar de chute “inevitável” não é definido, e a proteção não deve se tornar sorteio oculto que contradiga o gol físico.
3. **Atributos ausentes:** força, altura e reflexos aparecem nas fórmulas, mas os atletas têm somente seis atributos. Não há mapeamento explícito para físico/defesa nem escala definida para o reflexo do goleiro.
4. **Economia e Poisson:** com forças de ataque e defesa iguais, a fórmula dá λ=0,35 por time, ou 0,70 gol esperado no total, abaixo da meta 2,4–4,2. A fórmula F-08 depende de fator de idade ausente e pode divergir das faixas de preços. O déficit de 141 CR × 14 rodadas é 1.974 CR, não necessariamente coberto por uma venda de 80–260 CR; validar pressupostos e orçamento inicial.
5. **Passe e física:** com arrasto exponencial 1,15/s, velocidade inicial de 480/620/780 u/s tem distância assintótica aproximada de 417/539/678 u, abaixo de parte dos alcances indicados. Definir impulso, atrito ou alcance efetivo.
6. **Defesa:** o fluxograma indica bote no vazio se bola estiver a mais de 32 u; o cenário de falta usa bola a 50 u e contato com atacante a 30 u. Definir ordem de colisões e geometria.
7. **Classificação versus moeda:** em um trecho empate concede “1 CR”, mas tabela de liga diz 1 ponto. Tratar pontos e créditos como conceitos distintos; confirmar recompensa financeira.
8. **XP e elenco:** fórmula e tabela de XP acumulado não coincidem de forma óbvia; elenco pode ter até 18 atletas desde ENT-001, mas esse teto aparece desbloqueado no nível 8.
9. **Prioridades:** pênalti figura em reinícios Must, mas interface MEC-024/REQ-F-029 é Should. Pausa tática é Must no requisito, Should no backlog; comissão é Could no requisito e Should no backlog; loja aparece como MVP em uma tabela e Should em outra.
10. **Save:** debounce de 2 s não garante zero perda ao fechar imediatamente; definir commit durável, falhas e recuperação antes de prometer. Fechamento antes de um commit pode impedir qualquer garantia sem estratégia adicional.
11. **Eventos:** EVT-020 tem dois significados no texto; tabela e interface EventMap não contêm os mesmos eventos ou payloads, inclusive pausa. Criar contrato único.
12. **Duração e UX:** “3 min + 30 s de telas”, intervalo de 10 s e meta de duração real de 4m20s são números distintos; definir se interrupções param relógio e o que entra na medição.
13. **Estádio e comissão:** estádio tem 1–5 níveis em ENT-001, mas upgrade de 3 níveis em §9. Preparador físico é +20% por nível em ENT-004 e +20% total no nível 3 em §10.6.
14. **Requisitos e auditoria:** checklist afirma 29 ✅/2 ⚠️/1 ❌, mas os ícones das 32 linhas parecem somar 30 ✅/1 ⚠️/1 ❌; tabela B.4 lista REQ-F-028 como órfão apesar do vínculo BKL-041. A cobertura de MEC é descrita ora como 24, ora 25.
15. **Rede/offline:** um service worker pode satisfazer requisições do próprio navegador a partir do cache sem acessar a rede; esclarecer se “zero requisição” significa zero tráfego externo. Atualização automática e banner de atualização precisam ser compatibilizados.
16. **Regras de disciplina:** amarelo aos dois acúmulos, amarelo por probabilidade e limite mínimo de seis atletas necessitam uma regra única e definição para nova expulsão. Alguns cenários Gherkin afirmam resultado garantido apesar de sorteios por duelo.

## Auditoria original e status

O GDD registra AUD-01 a AUD-07: vínculo de histórico, parâmetros menores de UI, monitoramento da economia e câmera, escopo como bloqueante, detalhamento de mecânicas e ADR-08 pendente. Sua assinatura considera fases 0–7 concluídas como **documentação**, com fase 8 aguardando o usuário. A aprovação do GDD não comprova entrega nem validação do software.
