# 🏟️ FC

> Três minutos de futebol no navegador — e uma temporada para construir o seu clube.

**FC** é a especificação de um jogo de futebol 2D 7v7 que combina controle direto em partidas curtas com gestão de clube, elenco e carreira. A proposta é funcionar no navegador, sem backend, contas ou microtransações, com suporte offline após o primeiro acesso.

> **Estado do repositório:** documentação de planejamento. O GDD de referência está aprovado como especificação, mas a escolha de escopo e prazo está pendente e é bloqueante antes do marco M1. Este repositório não afirma conter jogo, código, build ou testes implementados.

## O jogo em resumo

- **Partida:** 7 contra 7, dois tempos de 90 segundos de jogo, visão aérea inclinada e controles arcade.
- **Carreira:** quatro divisões de oito clubes, 14 rodadas por temporada, acesso, rebaixamento, treino e mercado.
- **Acesso:** navegador desktop e mobile, com PWA e save local exportável planejados.
- **Identidade:** clubes, atletas e escudos fictícios; pixel art legível e interface em português do Brasil.
- **Modelo:** gratuito, sem backend, telemetria, login, anúncios ou moeda premium.

## Documentação

| Documento | Conteúdo |
| --- | --- |
| [Índice](docs/README.md) | Mapa da documentação e ordem de leitura |
| [Visão e escopo](docs/01-visao-e-escopo.md) | Pitch, pilares, modos, loops e limites do produto |
| [Mecânicas de partida](docs/02-mecanicas-de-partida.md) | Controles, bola, passe, chute, defesa, goleiro, IA e regras |
| [Conteúdo e carreira](docs/03-conteudo-e-carreira.md) | Entidades, divisões, calendário, itens e progressão |
| [Interface e acessibilidade](docs/04-interface-e-acessibilidade.md) | Telas, navegação, HUD, controles e experiência responsiva |
| [Direção de arte e áudio](docs/05-arte-e-audio.md) | Estilo, paleta, catálogo de assets e áudio |
| [Arquitetura](docs/06-arquitetura.md) | Stack, fronteiras, EventBus, cenas, persistência e ADRs |
| [Economia e balanceamento](docs/07-economia-e-balanceamento.md) | Fórmulas, parâmetros, metas e riscos de calibração |
| [Requisitos e backlog](docs/08-requisitos-e-backlog.md) | Requisitos funcionais e não funcionais, prioridades e entregas |
| [Roadmap e produção](docs/09-roadmap-e-producao.md) | Caminhos de escopo, marcos, estimativas e definição de pronto |
| [Testes e aceite](docs/10-testes-e-aceite.md) | Estratégia TST-001–025 e cenários críticos |
| [Riscos, decisões e auditoria](docs/11-riscos-decisoes-e-auditoria.md) | Premissas, riscos, decisões pendentes e inconsistências |
| [Glossário e rastreabilidade](docs/12-glossario-e-rastreabilidade.md) | Termos, prefixos e mapa requisito → teste → backlog |

## Stack-alvo

React 18.3+ · Phaser 3.80+ · TypeScript strict · Vite 5 · Zustand 4.5+ · Tailwind CSS 3.4+ · Vitest 2 · IndexedDB · PWA. Consulte [Arquitetura](docs/06-arquitetura.md) para detalhes e dependências propostas.

## Próxima decisão

Antes de iniciar a implementação, escolher **TBD-09**:

| Caminho | Entrega | Prazo estimado no GDD |
| --- | --- | --- |
| A · Vertical Slice | Partida completa e hub mínimo, sem carreira/temporada | 6–8 semanas |
| B · MVP enxuto | Partida e carreira linear, com cortes de gestão e acessibilidade avançada | 14–16 semanas |
| C · MVP completo | Todos os 30 itens Must planejados | ~23–38 semanas |

O GDD recomenda **A**, mas a escolha pertence ao usuário. As projeções requerem revisão conforme a capacidade real e as inconsistências apontadas em [produção](docs/09-roadmap-e-producao.md).

## Sobre esta documentação

Documentos organizados e adaptados a partir do **GDD-FC.md v1.0.0**, de 04/11/2026. Os arquivos são uma organização temática do conteúdo fornecido, não uma reprodução literal integral. Números são metas e hipóteses de design, não resultados comprovados. Conflitos do documento original estão registrados em [riscos e auditoria](docs/11-riscos-decisoes-e-auditoria.md) e não foram resolvidos unilateralmente.
