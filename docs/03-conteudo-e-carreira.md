# Conteúdo e carreira

[Índice](README.md) · [Interface e acessibilidade →](04-interface-e-acessibilidade.md)

## Princípio de conteúdo

Clubes, atletas e calendários devem ser gerados proceduralmente com seed determinística e dados compartilhados. Clubes, atletas e escudos são fictícios; usar composição silábica pt-BR, sobrenomes comuns e filtro de conteúdo ofensivo. Nenhuma licença real é pressuposta.

## Entidades

### ENT-001 · Clube

ID (`slug + seed`), nome de 3–24 caracteres, sigla editável de 3 caracteres, escudo paramétrico com forma, duas cores e padrão; divisão 1–4, reputação 0–100, orçamento em CR, estádio, tática e elenco de 11–18 atletas. Estádio planejado de 1.000 a 30.000 lugares, nível 1–5. Tática: formação e cinco instruções.

### ENT-002/003 · Atleta e atributos

ID, nome, idade de 16–38, papel (GOL, ZG, LAT, VOL, MEI ou ATA), seis atributos de 1–100, potencial oculto, forma 0,85–1,10, estamina e moral 0–100, contrato com salário e rodadas restantes, valor de mercado e lesão opcional de 0–4 rodadas.

| Atributo | Efeito declarado |
| --- | --- |
| Velocidade | Velocidade máxima e aceleração |
| Passe | Erro angular do passe |
| Finalização | Expectativa de conversão |
| Drible | Retenção e duelo de desarme |
| Defesa | Desarme e interceptação |
| Físico | Duelo aéreo e resistência à estamina |

Potencial limita evolução; olheiros o revelam parcialmente. Forma e estamina afetam o desempenho; moral baixa aumenta erro de decisão.

### ENT-004 · Comissão técnica

Preparador físico: recuperação +20%/nível; olheiro: revela potencial de 1–3 alvos/rodada; auxiliar técnico: reduz erro de decisão da IA aliada em 8%/nível. Três níveis, adquiridos em CR. Apesar da apresentação como conteúdo, a comissão é Could no requisito e Should no backlog; conferir [prioridades](11-riscos-decisoes-e-auditoria.md).

### ENT-005/006 · Competições e calendário

| Divisão | Clubes | Rodadas | Promoção | Rebaixamento |
| --- | ---: | ---: | --- | --- |
| Série D (LVL-04) | 8 | 14 | 2 primeiros à C | — |
| Série C (LVL-03) | 8 | 14 | 2 primeiros à B | 2 últimos à D |
| Série B (LVL-02) | 8 | 14 | 2 primeiros à A | 2 últimos à C |
| Série A (LVL-01) | 8 | 14 | Campeão conclui carreira vitoriosa | 2 últimos à B |

Turno e returno invertido; cada clube joga uma vez por rodada. Pontos: 3/1/0. Desempate: saldo, gols pró, confronto direto, sorteio por seed. Entre rodadas, uma ação de treino; janela de transferências nas rodadas 3–5 e 12–13. No fim da temporada, renovar carreira mantendo elenco, envelhecendo atletas um ano e gerando calendário, ou iniciar nova carreira. Base inicial proposta: três elencos-modelo e 25 atletas livres; outros clubes gerados proceduralmente.

| Divisão | Média de atributos pretendida | Potencial típico | Valor de elenco informado |
| --- | --- | --- | --- |
| D | 38–52 | 55–72 | 80–260 CR |
| C | 52–63 | 65–80 | 260–700 CR |
| B | 63–74 | 75–88 | 700–1.800 CR |
| A | 74–88 | 85–99 | 1.800–5.000 CR |

A tabela de valores e exemplos do GDD conflita com outros dados; veja [economia](07-economia-e-balanceamento.md) e [auditoria](11-riscos-decisoes-e-auditoria.md).

## Itens — ITM-001–008

| ID | Item | Efeito | Preço / duração |
| --- | --- | --- | --- |
| 001 | Recuperador muscular | +40 de estamina a um atleta | 25 CR / imediato |
| 002 | Chuteira leve | +4 velocidade | 40 CR / 1 partida |
| 003 | Luva de treino | +6 defesa do goleiro | 55 CR / 2 partidas |
| 004 | Vídeo de análise | Erro de decisão da equipe −5% | 35 CR / próxima partida |
| 005 | Centro de treinamento | Aumenta nível do treino | 300–1.200 CR / permanente |
| 006 | Ampliação de estádio | +5.000 lugares | 800–2.400 CR / permanente |
| 007 | Olheiro regional | Revela informação oculta dos alvos | 500 CR / 3 rodadas |
| 008 | Contrato de patrocínio | +120 CR por rodada | gratuito, 1 de 3 ofertas / 7 rodadas |

Consumíveis devem resolver emergências, com limite de três em estoque. Níveis e efeitos de algumas estruturas entram em conflito entre seções originais.

## Evolução e moral — MEC-021/023

Treino semanal: foco Ataque, Defesa ou Físico; +1 ponto distribuído entre dois atributos, com chance de +2 em nível alto, sem exceder potencial. Evolução por temporada: 16–21 anos +3 a +6 em dois atributos ligados ao papel; 22–27 +1 a +3 em um; 28–31 de 0 a −2; 32–38 −3 a −6, com aposentadoria aos 38. Moral: vitória +6, gol do atleta +4, titularidade +1, derrota −6, banco −2, lesão −10. Abaixo de 40 pode aumentar erro pessoal em até 15%. Mais detalhes de economia em [balanceamento](07-economia-e-balanceamento.md).
