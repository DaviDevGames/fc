# Glossário e rastreabilidade

[Índice](README.md) · [README principal](../README.md)

## Glossário

| Termo | Significado |
| --- | --- |
| 7v7 | Sete atletas por equipe, incluindo goleiro |
| ADR | Registro de decisão arquitetural, contexto e consequências |
| Assistência | Ajuste de mira antes do disparo, sem alterar física posterior |
| Autosave | Gravação automática após mudança de estado |
| `balancing.ts` | Local proposto para constantes de balanceamento |
| CR | Créditos de gestão do clube |
| Deadzone | Área em que a câmera ou joystick não reage ao movimento |
| Duelo | Comparação de atributos com variação aleatória limitada |
| Headless | Execução sem renderização |
| Histerese | Margem para evitar alternância instável |
| Hub | Tela central da carreira |
| MoSCoW | Must, Should, Could, Won't: classes de prioridade |
| MVP | Produto mínimo viável no recorte escolhido |
| PWA | Aplicação web instalável, com possibilidade de uso offline |
| Poisson | Distribuição usada no modelo abstrato de gols simulados |
| Potencial | Teto oculto de evolução do atleta |
| Seed | Semente do gerador pseudoaleatório para reprodutibilidade |
| Steering | Movimento contínuo orientado a comportamentos |
| Utility AI | Escolha de ação por pontuação de utilidade contextual |
| XP | Experiência acumulada do clube |

## Prefixos

`MEC` mecânica · `ENT` entidade · `LVL` divisão/estágio · `ITM` item · `UI` tela/componente · `AST` asset · `SFX` efeito sonoro · `BGM` trilha · `EVT` evento · `REQ-F` requisito funcional · `REQ-NF` requisito não funcional · `BKL` backlog · `RSK` risco · `ADR` decisão arquitetural · `TST` teste · `SUP` suposição · `TBD` decisão pendente · `AUD` achado de auditoria.

## Requisito funcional → teste → backlog

| Requisito | Teste | Backlog |
| --- | --- | --- |
| REQ-F-001 | TST-001 | BKL-014 |
| REQ-F-002 | TST-003 | BKL-005 |
| REQ-F-003 | TST-004 | BKL-006 |
| REQ-F-004 | TST-005 | BKL-007 |
| REQ-F-005 | TST-006 | BKL-008 |
| REQ-F-006 | TST-006 | BKL-009 |
| REQ-F-007 | TST-008 | BKL-010 |
| REQ-F-008 | TST-009 | BKL-011 |
| REQ-F-009 | TST-011 | BKL-012 |
| REQ-F-010 | TST-012 | BKL-013 |
| REQ-F-011 | TST-013 | BKL-015 |
| REQ-F-012 | TST-013 | BKL-015 |
| REQ-F-013 | TST-015 | BKL-027 |
| REQ-F-014 | TST-015 | BKL-027 |
| REQ-F-015 | TST-017 | BKL-018 |
| REQ-F-016 | TST-017 | BKL-022 |
| REQ-F-017 | TST-017 | BKL-024 |
| REQ-F-018 | TST-010 | BKL-020 |
| REQ-F-019 | TST-019 | BKL-023 |
| REQ-F-020 | TST-019 | BKL-019 |
| REQ-F-021 | TST-021 | BKL-028 |
| REQ-F-022 | TST-018 | BKL-025 |
| REQ-F-023 | TST-018 | BKL-026 |
| REQ-F-024 | TST-010 | BKL-031 |
| REQ-F-025 | TST-007 | BKL-005–010 |
| REQ-F-026 | TST-015 | BKL-033 |
| REQ-F-027 | TST-019 | BKL-032 |
| REQ-F-028 | TST-017 | BKL-041 |
| REQ-F-029 | TST-012 | BKL-013 |
| REQ-F-030 | TST-013 | BKL-034 |

Este é o mapeamento declarado no GDD; um vínculo não garante que o teste cubra todo o requisito.

## Requisito não funcional → evidência prevista

| Requisito | Teste | Evidência pretendida |
| --- | --- | --- |
| REQ-NF-001 | TST-024 | FPS em Android real e profiling |
| REQ-NF-002 | TST-024 | Relatório de bundle e gzip |
| REQ-NF-003 | TST-024 | Trace de 100 inputs e p95 |
| REQ-NF-004 | TST-018 | Crash test em 20 pontos |
| REQ-NF-005 | TST-025 | Inspeção de rede/cache e offline |
| REQ-NF-006 | TST-025 | Matriz de browsers preenchida |
| REQ-NF-007 | TST-013 | Auditoria de fluxo |
| REQ-NF-008 | TST-016 | Relatório axe e checklist WCAG |
| REQ-NF-009 | TST-016 | Playtest assistido |
| REQ-NF-010 | TST-002 | Typecheck e cobertura |
| REQ-NF-011 | TST-025 | Teste de build em arquivo local |
| REQ-NF-012 | TST-002 | Lint de strings |
| REQ-NF-013 | TST-022 | 1.000 partidas de fuzz |
| REQ-NF-014 | TST-022 | Teste de propriedade seed + inputs |
| REQ-NF-015 | TST-024 | Inventário e tamanho de assets e save |
