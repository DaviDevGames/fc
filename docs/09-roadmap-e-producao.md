# Roadmap e produção

[Índice](README.md) · [Testes e aceite →](10-testes-e-aceite.md)

## Decisão bloqueante — TBD-09

| Caminho | Corte proposto | Prazo informado |
| --- | --- | --- |
| A · Vertical Slice | M1–M5: partida completa e hub mínimo; sem carreira/temporada | 6–8 semanas |
| B · MVP enxuto | Partida e carreira linear de uma temporada; cortar mercado, treino, câmera mobile avançada e acessibilidade avançada | 14–16 semanas, segundo GDD |
| C · MVP completo | Os 30 itens Must do backlog | ~23–38 semanas, segundo GDD |

**Recomendação do GDD:** A. **Decisor:** usuário. Nenhum caminho foi escolhido no conteúdo recebido.

## Estimativa e ressalvas

O texto original declara 47,5 dias × 8 h = 380 h; com 20% de overhead, 456 h, ou 38 semanas a 12 h/semana e ~23 semanas a 20 h/semana. **A soma das 30 linhas do backlog é, porém, 43,5 dias**, equivalendo a 348 h e 417,6 h com o mesmo overhead: ~34,8 semanas a 12 h/semana ou ~20,9 a 20 h/semana. Esses cálculos não tornam a estimativa confiável: arte, áudio, QA, integração e contingências devem ser explicitamente revisados. O prazo do caminho A também requer estimativa própria por item e capacidade.

## Marcos propostos

| Marco | Foco | Entregável-alvo |
| --- | --- | --- |
| M1 | Fundação | Campo vazio e um atleta controlável |
| M2 | Campo | Dois atletas, bola, passe e chute |
| M3 | Defesa | 7v7, gol, goleiro e faltas |
| M4 | IA | Quatro dificuldades e partidas competitivas |
| M5 | Interface | HUD, touch e hub navegável |
| M6 | Gestão | Mercado, treino e tabela de carreira |
| M7 | Entrega | Save, exportação, PWA e acessibilidade |
| M8 | Polimento | Balanceamento, correções e release candidate |

O GDD associa M1–M8 a semanas S1–S8, mas reconhece que o MVP completo não cabe nesse calendário na disponibilidade proposta; tratar a sequência como ordem ilustrativa, não compromisso de prazo.

**Gate por marco:** build em mobile real, zero bugs P0 e um playtest externo de 15 min.

## Definition of Done

1. TS strict e `tsc --noEmit` limpos, sem `any` implícito.
2. Testes associados escritos e passando em CI local.
3. Fronteiras de import verificadas.
4. Testado em desktop e dispositivo móvel real.
5. Funciona offline após o primeiro carregamento.
6. Strings no catálogo `pt-BR.ts`.
7. Alvos ≥ 48 px, contraste AA e escala 150% verificados.
8. GDD atualizado quando parâmetros mudarem.
9. Zero bugs P0/P1 do item.
10. Playtest rápido de cinco minutos sem bloqueio.

Esses critérios são requisitos pretendidos, não uma alegação de que já foram cumpridos.
