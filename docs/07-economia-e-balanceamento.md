# Economia e balanceamento

[Índice](README.md) · [Requisitos e backlog →](08-requisitos-e-backlog.md)

> As tabelas são metas e estimativas do GDD, não medições. O material apresenta inconsistências relevantes; veja a [auditoria](11-riscos-decisoes-e-auditoria.md).

## Fórmulas consolidadas

| ID | Fórmula proposta | Uso |
| --- | --- | --- |
| F-01 | `velMax_base × (0,70 + 0,30 × vel/100) × forma` | Movimento |
| F-02 | `erroBase × (1,35 − 0,70 × passe/100) × pressão` | Passe |
| F-03 | `atributo + random(−8,+8)` | Duelos; usar composição específica de cada duelo |
| F-04 | `baseZona + curvaFin + bonusÂngulo − gkReflexo` | Expectativa de finalização |
| F-05 | `estamina_anterior − 8/s em sprint + 4,5/s parado` | Estamina; andando recupera 2/s |
| F-06 | `clamp(0,35 + (atkA − defB)/120, 0,25, 3,2)` | Lambda da simulação |
| F-07 | `100 + 25 × gols + 60 × vitória + 30 × clean_sheet` | XP de partida jogada |
| F-08 | `(soma_atributos/10)^1,8 × 40 × fator_idade` | Valor de mercado; fator de idade não definido |

O GDD propõe constantes `readonly` em `src/shared/balancing.ts`, testes de snapshot e sincronização entre código e documento. Veja tabelas de movimento e ações em [mecânicas](02-mecanicas-de-partida.md).

## Parâmetros globais propostos

| Grupo | Constantes principais |
| --- | --- |
| Partida | duração 180 s; intervalo após 90 s; intervalo 10 s; campo 1600 × 1000; gol 160 × 100; área 300 × 420 |
| Atleta | raio 24; seleção 260; histerese 40; sprint 8/s; recuperação parado 4,5/s, andando 2/s; limiares 25 e 10 |
| Bola | raio 12; arrasto 1,15/s; restituição 0,58; velocidade máxima 1400; posse 24; controle 0,92 |
| Passe | faixas de carga 180/450/900 ms; cone 55°; erros 5/8/12°; velocidades 480/620/780; pressão +0,25/adversário até 1,75 |
| Chute | carga 900 ms; penalidade 0,20 por 100 u além de 620 u |
| Bote | janela 400 ms; raio 32 u; eficácia IA 0,70; falta por ângulo desfavorável 0,60 |
| Goleiro | offset 40; saída 120; reflexo base 55 + 0,35/atributo; fechamento 15° |
| Economia | bilheteria 0,08; prêmio vitória D/C/B/A = 20/40/70/120 CR; manutenção 25 por nível |

## Metas de partidas

| Indicador | Alvo | Faixa aceitável |
| --- | --- | --- |
| Gols totais por partida | 3,2 | 2,4–4,2 |
| Vitória do jogador contra Amador | 60–68% | ≥ 55% |
| Vitória contra Elite | 32–40% | 25–45% |
| Posse do jogador | 50% | 40–60% |
| Finalizações totais | 14–18 | 10–22 |
| Conversão | 18–22% | 14–26% |
| Faltas | 6–9 | 4–12 |
| Gols de bola parada | 25–30% | ≤ 35% |
| Duração real | 4m20s ±20s | ≤ 5 min |
| Tempo até primeiro gol | 55 s | 35–90 s |

Medir por playtest e simulações; o cálculo correto de conversão é gols ÷ chutes. Não tomar simulação abstrata como prova de que a IA visual ou a experiência humana cumprem as metas.

## Progressão do clube

Duas grandezas: CR para salários, mercado, itens e infraestrutura; XP acumulativo para níveis e desbloqueios. Sem moeda premium. Fórmula informada: `xp_necessario(nivel) = 400 × nivel^1,35`, além de F-07. A tabela de XP acumulado original não é consistente com a fórmula sem definição adicional.

| Nível | XP acumulado informado | Desbloqueio |
| --- | ---: | --- |
| 1 | 0 | Início |
| 2 | 400 | Recuperador |
| 3 | 1.020 | Vaga de olheiro |
| 4 | 1.770 | Treino nível 2 |
| 5 | 2.620 | Ampliação do estádio |
| 6 | 3.545 | Patrocínios melhores |
| 7 | 4.540 | Treino nível 3 |
| 8 | 5.595 | Teto de 18 atletas |
| 9 | 6.700 | Escudo dourado |
| 10 | 7.855 | Lenda do clube |

## Receita, despesa e sustentabilidade

- Bilheteria: `capacidade × 0,08 × (0,6 + 0,4 × moral/100)` CR.
- Patrocínio: valor fixo do contrato, por exemplo 120 CR/rodada na Série D.
- Prêmio de vitória: D 20, C 40, B 70, A 120 CR. Vendas: F-08.
- Despesas: soma dos salários mais estádio.nível × 25 CR.
- Prêmios de acesso: D→C 400, C→B 900, B→A 1.800 CR.

| Cenário do GDD | Receita | Despesa | Saldo por rodada |
| --- | ---: | ---: | ---: |
| Série D, inicial | 204 | 345 | −141 CR |
| Série D, segundo ano | 284 | 350 | −66 CR |
| Série C | 460 | 480 | −20 CR |
| Série A | 2.900 | 5.445 | −2.545 CR |

A tensão econômica é intencional, mas a afirmação de que uma venda por temporada resolve o déficit não segue necessariamente desses números. Validar orçamento inicial, folha completa, receitas, política para saldo negativo e 100 saves no TST-010. O prêmio de vitória só entra quando há vitória. Nenhuma taxa de falência ou sustentabilidade foi medida.

## Dificuldade e elenco

Série D: Amador e multiplicador de atributos adversários 0,95; C: Amador+/Profissional− e 1,00; B: Profissional e 1,03; A: Elite e 1,05. Níveis intermediários precisam de parâmetros explícitos. Alvos de vitória: D 62–68%, C 55–60%, B 45–52%, A 35–42%.

Estamina: um descanso recupera +35; recuperador +40; preparador nível 3 tem efeito descrito de +20% em toda recuperação, embora outro trecho especifique +20% por nível. Exemplos residuais são hipóteses, não simulação executada.
