# Visão geral e escopo

[Índice](README.md) · [Mecânicas →](02-mecanicas-de-partida.md)

## Pitch

**FC** combina partidas de futebol 2D com controle direto e gestão de clube. Em campo o jogador conduz, passa, chuta e desarma; fora dele escala, treina e negocia para subir da quarta divisão até o título. A fantasia central é: **“Eu sou o cara que resolve dentro e fora de campo.”**

Referências de design: Sensible Soccer e Kick Off para controle arcade; Brasfoot e Elifoot para gestão acessível; Football Manager para consequência das decisões; Pocket League Story para progressão charmosa; Rocket League para leitura espacial. Não se pretende reproduzir suas licenças nem sua complexidade.

## Pilares

| Pilar | Objetivo e métrica | Antiobjetivo |
| --- | --- | --- |
| Controle tátil | Input → ação visual ≤ 50 ms p95; passes não intencionais ≤ 8% em playtest | Física imprevisível que pune o controle |
| Densidade | Jogar → primeiro toque em ≤ 4 cliques / 8 s; sessões curtas | Menus excessivos e transições longas |
| Consequência | Diferença ≥ 15% em gols entre extremos de elenco na mesma divisão; duas consequências reconhecidas em playtest | Gestão cosmética |
| Acessibilidade técnica | FCP ≤ 1,5 s em 4G; shell ≤ 350 KB gzip; offline após primeiro acesso | Servidor, conta ou download superior a 5 MB |

Em conflitos, controle vence realismo; densidade vence profundidade no primeiro corte; performance vence gráficos; polimento vence volume de conteúdo.

## Escopo declarado

**Dentro do MVP-alvo:** partida rápida contra IA; carreira renovável com 4 divisões × 8 clubes; 7v7, 2 × 90 s e regras simplificadas; mercado, base e treino; persistência local, exportação/importação JSON e PWA offline; remapeamento, escala, paleta acessível e redução de movimento.

**Fora da v1.0:** multiplayer e ranking global; backend, conta, nuvem e cross-save; 11v11, 3D e física realista; licenças reais; editor tático avançado individual; futebol feminino, seleções e copas continentais; localização além de pt-BR.

## Loops

- **Sessão:** abrir → hub → jogar ou gerir → partida → resultado e recompensa → gestão → sair ou repetir. Alvo: 4–8 min; resultado é ponto natural de saída com save concluído.
- **Partida:** observar → ler espaço → escolher condução, passe, chute ou desarme → executar → resolver → receber feedback → repetir. Ciclo estimado: 1,5–4 s; pressão forçada se não houver decisão relevante por mais de 6 s.
- **Carreira:** disputar rodada → receber CR/XP/reputação → treinar e recuperar → negociar ou promover base → ajustar tática → nova rodada. Após 14 rodadas: acesso, permanência ou rebaixamento, contratos e novo calendário.

Uma temporada é estimada em cerca de 63 min, e a subida D→A em cerca de 4,2 h; estimativas exigem playtest.

## Primeiros 10 minutos pretendidos

| Tempo | Experiência |
| --- | --- |
| 0:00–0:25 | Abrir e criar identidade do clube |
| 0:25–1:10 | Dicas não bloqueantes de movimento, passe e chute em partida real |
| 1:10–4:00 | Primeira partida em Amador |
| 4:00–5:30 | Resultado, recompensa e sugestão de treino |
| 5:30–8:00 | Treino ou contratação guiada |
| 8:00–10:00 | Início da carreira na Série D |

O roteiro é intenção de design; a relação entre partida rápida, recompensa e criação de carreira precisa ser esclarecida na implementação.
