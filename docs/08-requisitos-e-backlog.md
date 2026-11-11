# Requisitos e backlog

[Índice](README.md) · [Roadmap e produção →](09-roadmap-e-producao.md)

As prioridades são as declaradas no GDD, incluindo divergências entre tabelas. O escopo de produção continua condicionado à escolha de TBD-09.

## Requisitos funcionais

| ID | Requisito | Prioridade |
| --- | --- | --- |
| REQ-F-001 | Partida 7v7, 180 s, campo 2D | Must |
| REQ-F-002 | Movimento com aceleração e sprint | Must |
| REQ-F-003 | Troca automática/manual com histerese | Must |
| REQ-F-004 | Passe curto/médio/longo e cone de mira | Must |
| REQ-F-005 | Chute carregado e física da bola | Must |
| REQ-F-006 | Desarme e faltas por contato | Must |
| REQ-F-007 | Goleiro posiciona, defende e repõe | Must |
| REQ-F-008 | IA por papel e quatro dificuldades | Must |
| REQ-F-009 | Quatro formações e cinco instruções com efeito | Must |
| REQ-F-010 | Lateral, escanteio, tiro de meta, falta e pênalti | Must |
| REQ-F-011 | HUD de placar, tempo, estamina e instruções | Must |
| REQ-F-012 | Joystick e quatro botões touch ≥ 48 px | Must |
| REQ-F-013 | Partida rápida configurável | Must |
| REQ-F-014 | Criação de clube e escudo | Must |
| REQ-F-015 | Mundo procedural de 4 × 8 clubes | Must |
| REQ-F-016 | 14 rodadas, turno/returno, classificação | Must |
| REQ-F-017 | Acesso, rebaixamento e renovação de carreira | Must |
| REQ-F-018 | Mercado com filtros, compra, venda e negociação | Must |
| REQ-F-019 | Treino semanal limitado pelo potencial | Must |
| REQ-F-020 | Estamina e moral persistentes | Must |
| REQ-F-021 | Simulação Poisson e resultado auditável | Must |
| REQ-F-022 | Autosave após partida e gestão | Must |
| REQ-F-023 | Exportação/importação JSON com checksum e migração | Must |
| REQ-F-024 | Loja com oito itens e melhorias | Should |
| REQ-F-025 | Atributos impactam desempenho em campo | Must |
| REQ-F-026 | Cinco dicas contextuais | Should |
| REQ-F-027 | Comissão técnica, três cargos e níveis | Could |
| REQ-F-028 | Histórico de carreira, títulos e recordes | Could |
| REQ-F-029 | Interface de pênalti com mira e força | Should |
| REQ-F-030 | Pausa com instruções táticas | Must |

## Requisitos não funcionais

| ID | Meta |
| --- | --- |
| REQ-NF-001 | 60 fps desktop mid-range; ≥ 45 fps Android mid-range |
| REQ-NF-002 | Shell ≤ 350 KB gzip; chunk lazy do jogo ≤ 900 KB |
| REQ-NF-003 | Input → frame ≤ 50 ms p95 |
| REQ-NF-004 | Integridade de progresso; crash test em 20 pontos |
| REQ-NF-005 | Privacidade, zero telemetria e offline após primeiro carregamento |
| REQ-NF-006 | Chrome, Edge, Firefox, Safari recentes; iOS 15+, Android 9+ |
| REQ-NF-007 | Ação crítica a ≤ 1 toque da tela principal; profundidade ≤ 3 níveis |
| REQ-NF-008 | Acessibilidade: alvo 48 px, contraste, remap, daltonismo, redução de movimento |
| REQ-NF-009 | Completável em Amador + assistência Total |
| REQ-NF-010 | TS strict, `noUncheckedIndexedAccess`, sem `any`, cobertura ≥ 60% nas áreas definidas |
| REQ-NF-011 | Client-side; degradação graciosa em `file://` sem service worker |
| REQ-NF-012 | Todas as strings via `pt-BR.ts` com lint |
| REQ-NF-013 | Sem crash em 1.000 partidas simuladas fuzz |
| REQ-NF-014 | Mesma seed e mesmos inputs → mesmo resultado |
| REQ-NF-015 | Assets ≤ 2,5 MB; save típico ≤ 1 MB |

## Backlog Must

| ID | Entrega | Estimativa do GDD |
| --- | --- | ---: |
| BKL-001 | Setup Vite, React, TS strict, Tailwind, Vitest, PWA | 0,5 d |
| BKL-002 | EventBus tipado e domínio | 0,5 d |
| BKL-003 | Instância Phaser, cenas iniciais e escala | 1 d |
| BKL-004 | Balanceamento e snapshots | 0,5 d |
| BKL-005 | Entidades, movimento e sprint | 2 d |
| BKL-006 | Posse, drible e troca | 1,5 d |
| BKL-007 | Passe e cabeceio | 2 d |
| BKL-008 | Chute e física | 1,5 d |
| BKL-009 | Desarme, faltas e cartões | 1,5 d |
| BKL-010 | Goleiro | 2 d |
| BKL-011 | Utility AI, papéis, dificuldades | 3 d |
| BKL-012 | Formações e instruções | 1,5 d |
| BKL-013 | Reinícios e pênalti | 2 d |
| BKL-014 | Árbitro e estados | 1,5 d |
| BKL-015 | HUD, touch e joystick | 2 d |
| BKL-016 | Câmera portrait e minimapa | 1 d |
| BKL-017 | Hub responsivo | 1,5 d |
| BKL-018 | Gerador de mundo | 2 d |
| BKL-019 | Elenco, tática e escalação | 2 d |
| BKL-020 | Mercado e negociação | 2 d |
| BKL-021 | Resultado e aplicação no store | 1 d |
| BKL-022 | Classificação, calendário e simular | 1,5 d |
| BKL-023 | Treino e potencial | 1 d |
| BKL-024 | Temporada e acesso/rebaixamento | 1,5 d |
| BKL-025 | Save, fallback, migração e autosave | 1,5 d |
| BKL-026 | Exportação/importação e checksum | 0,5 d |
| BKL-027 | Menu, novo jogo, configurações | 1,5 d |
| BKL-028 | Simulador e consistência | 1 d |
| BKL-029 | PWA e offline | 1 d |
| BKL-030 | Acessibilidade avançada | 1,5 d |

A soma dos valores das linhas é **43,5 dias**, não 47,5 dias conforme o total textual do GDD. Ambas excluem trabalho adicional não estimado; reconciliar antes de comprometer prazo.

## Demais prioridades

- **Should:** BKL-031 loja e upgrades; 032 comissão; 033 dicas; 034 pausa tática; 035 créditos; 036 áudio; 037 arte final.
- **Could:** BKL-038 desafios; 039 copa nacional; 040 editor de escudo avançado; 041 histórico e recordes; 042 inglês; 043 retratos.
- **Won't v1.0:** multiplayer, 11v11, 3D/física realista, licenças reais, contas/nuvem, anúncios e microtransações.

Observe que REQ-F-030 é Must enquanto BKL-034 é Should; REQ-F-027 é Could enquanto BKL-032 é Should. Resolver explicitamente. Matriz de rastreabilidade: [glossário e rastreabilidade](12-glossario-e-rastreabilidade.md).
