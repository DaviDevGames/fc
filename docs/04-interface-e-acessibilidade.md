# Interface e acessibilidade

[Índice](README.md) · [Arte e áudio →](05-arte-e-audio.md)

## Diretrizes

Uma decisão por tela; até cinco ações primárias no hub. Mobile-first na leitura e desktop-first na densidade. Alvos de toque ≥ 48 × 48 px com espaço ≥ 8 px; texto ≥ 14 px no mobile e ≥ 16 px no desktop. Estados usam ícone, texto e cor; ações críticas ficam na zona de alcance dos polegares.

## Telas

| ID | Tela / função |
| --- | --- |
| UI-01 | Splash e boot |
| UI-02 / 02b | Menu principal e configuração da partida rápida |
| UI-03 | Criação do clube, escudo e cores |
| UI-04 | Hub: próximo jogo, orçamento, moral, estamina e treino |
| UI-05 | Calendário, rodada e simulação |
| UI-06 | Elenco |
| UI-07 | Mercado e transferências |
| UI-08 | Tática e escalação |
| UI-09 | HUD da partida |
| UI-10 | Pausa e instruções |
| UI-11 | Resultado, estatísticas, recompensas e próxima rodada |
| UI-12 | Classificação |
| UI-13 | Configurações e acessibilidade |
| UI-14 | Saves e exportação/importação |
| UI-15 | Fim de temporada, acesso e renovação |
| UI-16 | Loja e melhorias |
| UI-17 | Dicas contextuais |
| UI-18 | Créditos e licenças |

Fluxo: menu → novo jogo → hub → calendário/elenco/mercado/tática/loja; calendário → jogar ou simular → resultado → hub ou próxima rodada. Partida rápida sai do menu por configuração. Fim de temporada leva à renovação.

## Layout e campo

- Desktop ≥ 900 px: sidebar 240 px, conteúdo e painel lateral 320 px.
- Paisagem compacta 600–899 px: topbar 56 px, conteúdo integral.
- Retrato: topbar 56 px, navegação inferior 64 px e conteúdo com rolagem.
- Canvas em paisagem: proporção 16:10 centralizada com Scale.FIT.
- Retrato: campo não rotaciona; câmera segue bola com zoom 1,35 e deadzone 220 × 160 u; minimapa 160 × 100 px. É uma suposição sujeita a playtest e decisão TBD-01.

## HUD

Placar com siglas, gols e cronômetro no topo; barra de estamina sob atleta selecionado; ações passe, chute com carga, bote e sprint no canto inferior direito; joystick no canto inferior esquerdo com zona de 120 px e deadzone de 18%; botão de tática, pausa, avisos e minimapa em retrato. React desenha o HUD textual; Phaser desenha o campo e entidades.

Resultado mostra placar, autores e minuto dos gols, posse, finalizações, desarmes, CR, XP, moral e estamina. A tela só deve aparecer após persistência do resultado. Ações: próxima rodada, classificação e hub.

## Acessibilidade

| Recurso | Alvo |
| --- | --- |
| Remapeamento | Total, persistente; duas opções de binding por ação segundo o GDD |
| Escala de interface | 100%, 115%, 130%, 150% sem quebra |
| Daltonismo | Paleta alternativa e padrão visual para distinguir equipes |
| Movimento reduzido | Desligar shake, partículas e flashes |
| Feedback visual | Gol, falta e apito representados por ícone e texto |
| Contraste | WCAG AA: 4,5:1 para texto e 3:1 para componentes |
| Teclado | Foco visível, ordem lógica, Esc fecha modal |
| Assistência | Amador + assistência Total deve permitir completar o jogo |

## Dicas não bloqueantes — UI-17

Uma por vez, dispensáveis: mover 200 u (WASD/joystick), completar um passe (J), chutar (K), acertar um desarme (L) e trocar de atleta (Tab). Botão **Pular dicas** sempre visível. Nenhuma dica pausa a partida. A especificação marca onboarding como Should apesar de outros trechos apresentá-lo como MVP.
