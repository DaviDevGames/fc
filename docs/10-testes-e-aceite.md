# Testes e critérios de aceite

[Índice](README.md) · [Riscos e decisões →](11-riscos-decisoes-e-auditoria.md)

## Estratégia planejada

Vitest para lógica pura e propriedade; Playwright para fluxos e UI; axe-core e verificação manual para acessibilidade; `fake-indexeddb` para persistência; simulação em lote para balanceamento; Lighthouse, traces e aparelhos reais para desempenho. Alvo de cobertura ≥ 60% em `shared/` e `game/systems/`. Nada abaixo constitui evidência de testes executados.

| ID | Verificação | Critério proposto |
| --- | --- | --- |
| TST-001 | Partida e placar | 180 s de jogo, placar válido, `match:end` uma vez |
| TST-002 | Estático e constantes | Snapshots, lint de strings, `tsc --noEmit` |
| TST-003 | Movimento | Aceleração, velocidade máxima e sprint |
| TST-004 | Troca | Seleção, histerese e ausência de flicker |
| TST-005 | Passe | Cone, distribuição de erro e clamp anti-saída |
| TST-006 | Chute e desarme | Carga, trajetória, colisões, contato e faltas |
| TST-007 | Atributos | +20 finalização muda conversão em ≥ 5%; esclarecer pontos percentuais ou relativo |
| TST-008 | Goleiro | Resposta proporcional e chute inevitável entra |
| TST-009 | Balanceamento | 1.000 partidas por dificuldade; faixas de gols e vitórias |
| TST-010 | Economia | 100 saves sem falência incapacitante antes da rodada 10 |
| TST-011 | Táticas | Formações e instruções mudam comportamento mensuravelmente |
| TST-012 | Reinícios | Todos resolvem e retornam a Play |
| TST-013 | HUD | Tempo/placar corretos, alvos e fluxo touch |
| TST-014 | Assistência | Não altera a física após o disparo |
| TST-015 | Onboarding | Menu à primeira partida com poucos cliques e dicas não bloqueantes |
| TST-016 | Acessibilidade | Contraste, foco, remapeamento, distinção de equipes e playtest assistido |
| TST-017 | Mundo | 4 × 8 clubes, calendário válido, acesso e rebaixamento |
| TST-018 | Save | Autosave, 20 pontos de crash, migração, corrupção e importação |
| TST-019 | Gestão | Treino, potencial, estamina e moral persistentes |
| TST-020 | Fronteiras | Sem imports app ↔ game; jogo sem storage |
| TST-021 | Simulação | Médias da simulação e cena convergem em ±10% |
| TST-022 | Determinismo/fuzz | Mesma seed e mesmos inputs; 1.000 partidas sem crash |
| TST-023 | Ciclo de vida | Zero listeners vazados após shutdown |
| TST-024 | Performance | FPS, latência, bundle e tamanho de assets medidos |
| TST-025 | Offline/compatibilidade | Primeiro cache, reload offline, browsers e `file://` |

## Cenários críticos em Gherkin

```gherkin
# language: pt
Funcionalidade: Partida e relógio
  Cenário: Partida termina normalmente
    Dado que uma partida foi iniciada
    Quando 180 segundos de jogo ativo forem consumidos
    Então o placar deve conter dois inteiros não negativos
    E o evento de fim de partida deve ser emitido exatamente uma vez

  Cenário: Gol reinicia com o time que sofreu
    Dado um placar de 0 a 0 aos 45 segundos
    Quando a bola cruza totalmente a linha do gol do time B
    Então o placar deve ser 1 a 0
    E a bola deve voltar ao centro para a equipe B
```

```gherkin
# language: pt
Funcionalidade: Controles
  Cenário: Sprint bloqueado com estamina crítica
    Dado um atleta com estamina 9
    Quando o jogador aciona sprint
    Então o sprint não deve ser ativado
    E deve haver feedback perceptível

  Esquema do cenário: Carga de passe
    Quando o jogador segura o passe por <carga> milissegundos
    Então o passe deve ser <tipo> a <velocidade> unidades por segundo
    Exemplos:
      | carga | tipo  | velocidade |
      | 100   | curto | 480        |
      | 300   | médio | 620        |
      | 700   | longo | 780        |

  Cenário: Chute satura e viaja fisicamente
    Quando o jogador carrega o chute por 1200 milissegundos
    Então a força deve saturar em 100
    E a bola deve viajar com velocidade de até 1400 unidades por segundo
    E o gol deve depender da trajetória e das colisões
```

```gherkin
# language: pt
Funcionalidade: Carreira e integridade
  Cenário: Potencial limita treino
    Dado um atleta com potencial 65 e finalização 65
    Quando o foco de ataque é aplicado por 5 semanas
    Então finalização deve permanecer 65

  Cenário: Importação inválida preserva o save
    Dado um save válido em andamento
    Quando um JSON com checksum inválido é importado
    Então a importação deve falhar com mensagem clara
    E o save existente deve permanecer inalterado

  Cenário: Persistência antes do resultado
    Dado que a partida terminou
    Quando a tela de resultado é exibida
    Então a aplicação do resultado deve ter sido persistida com sucesso
    E a rodada não deve ser aplicada duas vezes
```

```gherkin
# language: pt
Funcionalidade: Acessibilidade
  Cenário: Controles touch
    Dado o HUD em viewport de 360 por 640 pixels
    Então cada botão de ação deve ter pelo menos 48 por 48 pixels
    E os botões devem estar separados por pelo menos 8 pixels

  Cenário: Remapeamento
    Dado que o jogador troca a tecla de chute de K para X
    Quando recarrega e inicia uma partida
    Então X deve chutar e K não deve mais chutar
```

Os cenários são uma seleção adaptada, não uma reprodução integral dos exemplos do GDD. Resolver primeiro as contradições de TST-006, persistência e goleiro descritas na [auditoria](11-riscos-decisoes-e-auditoria.md).
