# Direção de arte e áudio

[Índice](README.md) · [Arquitetura →](06-arquitetura.md)

## Arte

Pixel art 2D em visão aérea inclinada, paleta quente e saturada, contorno escuro de 1 px, dois tons de sombreamento. Sprites lógicos de atleta 32 × 32 px, bola 16 × 16 px. Prioridade para silhueta, equipe e número legíveis; grama em faixas de 80 u e linhas de 3 px. Animações planejadas a 12 fps: corrida 6 frames, chute 4 e desarme 4. Indicador âmbar; partículas de 8–16 px. Cores iguais ou confundíveis devem gerar padrão listrado no time B.

| Uso | Cor |
| --- | --- |
| Grama clara / escura | `#3E8E41` / `#34803A` |
| Linhas | `#F2F2E8` |
| Time A / B | `#2E6BE6` / `#E64C2E` |
| Seleção | `#FFC42E` |
| UI base | `#12161F` / `#1C2230` |
| Texto | `#F5F7FA` |

Contraste deve ser medido; valores e afirmações do GDD não substituem verificação WCAG.

## Assets previstos

| ID | Asset | Especificação |
| --- | --- | --- |
| AST-001 | `atlas-players.png` | Atlas 512 × 512 de atletas e animações |
| AST-002 | `atlas-ball.png` | Sprite sheet 64 × 16, quatro quadros |
| AST-003 | `atlas-ui.png` | Atlas 512 × 512, ícones e painéis 9-slice |
| AST-004 | `campo-tileset.png` | Tileset 256 × 256 para campo e marcações |
| AST-005 | `crest-kit.svg` | Escudos paramétricos, oito formas e padrões |
| AST-006 | `font-pixel.png` | Fonte bitmap; fallback de sistema |
| AST-007 | `atlas-fx.png` | Atlas 256 × 256 de efeitos |
| AST-008 | `portraits.png` | Retratos procedurais, pós-MVP |

Pipeline proposto: Aseprite → atlas JSON com hash → `public/assets/` → preload. Orçamento total ≤ 2,5 MB. Assets aqui são especificações, não arquivos já produzidos.

## Áudio previsto

| ID | Evento | Duração |
| --- | --- | ---: |
| SFX-001 | Chute | 0,18 s |
| SFX-002 | Passe | 0,12 s |
| SFX-003 | Gol | 1,40 s |
| SFX-004 | Trave | 0,30 s |
| SFX-005 | Defesa do goleiro | 0,22 s |
| SFX-006 | Apito | 0,60 s |
| SFX-007 | Falta/cartão | 0,45 s |
| SFX-008 | Desarme limpo | 0,20 s |
| SFX-009 | Clique UI | 0,06 s |
| SFX-010 | Confirmação UI | 0,14 s |
| SFX-011 | Erro UI | 0,16 s |
| SFX-012 | Torcida ambiente, loop | 4 s |
| SFX-013 | Ovação | 2,2 s |
| SFX-014 | Arfada de estamina baixa | 0,50 s, repetição a cada 4 s |
| SFX-015 | Bola na rede / arremesso lateral, conforme GDD | 0,15 s |

| ID | Trilha | Uso | Duração |
| --- | --- | --- | --- |
| BGM-01 | Domingo de Jogo | Menu/hub | 1:20, loop |
| BGM-02 | Noventa Minutos | Partida | 2:00, loop e três camadas |
| BGM-03 | Vestiário | Resultado/gestão | 1:10, loop |
| BGM-04 | Acesso | Fim de temporada | 0:40, uma vez |

Mixagem proposta: BGM −14 LUFS, SFX pico −6 dBFS; ducking da BGM de −8 dB no gol. Sliders Master/BGM/SFX e mudo; eventos críticos têm equivalente visual. Fontes de áudio CC0 ou sintetizadas são uma suposição; auditar licenças antes de distribuição. Áudio completo é Should no backlog.
