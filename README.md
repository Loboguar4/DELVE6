# DELVE6

**Um dado. Uma chance. Caminhos infinitos.**

DELVE6 (ou DelveS) é um sistema OSR ultraminimalista construído em torno de uma única premissa: **tudo se resolve com um d6**. Sem tabelas de múltiplos dados, sem fichas complexas — só um dado de seis lados, papel, lápis, e uma masmorra gerada proceduralmente à sua frente.

Este repositório contém o **livro de regras core** (`delve6-book.pdf`) e uma **implementação jogável em navegador** (`index.html`) do primeiro módulo, *The Forgotten Vault*.

---

## Jogar agora

<https://loboguar4.github.io/DELVE6/>

---

## Manifesto

1. Um único dado.
2. Regras mínimas.
3. Geração procedural.
4. Improvisação acima de preparação.
5. Todo módulo pode ser modificado.
6. O mestre é opcional.

> O livro fornece ferramentas, não histórias prontas.

DELVE6 foi desenhado para **campanhas solo**: o mínimo de recurso necessário para jogar é um d6, papel e caneta. Nenhum mestre é obrigatório — a masmorra se gera sozinha, rolagem por rolagem. 

---

## Neste repositório

| Arquivo | O que é |
|---|---|
| [`delve6.txt`](./delve6.txt) | O livro de regras core: manifesto, gerador de masmorra, classes, combate, itens e inimigos. |
| [`delve6-book.pdf`](./delve6-book.pdf) | O livro de regras core em HTML. |
| [`index.html`](./index.html) | Implementação jogável de *The Forgotten Vault* — um crawler de masmorra completo, rodando inteiramente no navegador. |
| `README.md` | Este documento. |
| `LICENSE` | Licença MIT. |

---

## Como jogar (versão digital)

Não há instalação, servidor ou build. Basta abrir `index.html` em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).

1. Escolha uma classe.
2. Distribua os quatro modificadores (FOR, AGL, PRE, DUR) entre os valores **3, 2, 1, 0**, sem repetição.
3. Escolha arma e armadura iniciais (algumas exigem atributos mínimos, ou são exclusivas de uma classe).
4. Desça à masmorra.

A interface é organizada em **janelas independentes** — Ficha, Mapa da Masmorra, Masmorra, Ações e Registro de Dados — que podem ser **arrastadas, redimensionadas, sobrepostas e minimizadas** livremente, como um pequeno desktop. O layout que você montar fica salvo durante toda a sessão do navegador (inclusive entre incursões, até a página ser atualizada).

---

## Recursos implementados na versão digital

- **Geração procedural completa** do algoritmo de masmorra descrito em `delve6.txt` e `delve6-book.pdf`: saguões, corredores, armadilhas, salas escuras, prisões, portas trancadas, bifurcações e o Portão Rúnico.
- **Movimentação restrita a salas adjacentes**, com mapa que só revela o tipo de cada sala depois que ela é visitada.
- **Backtracking com risco**: revisitar uma sala já explorada rola 1d6 — valores baixos trazem de volta um inimigo comum.
- **Tochas com durabilidade** (d6 salas/movimentações), necessárias para lutar sem desvantagem e para coletar itens escondidos no escuro.
- **Joias únicas por cor** (amarela, vermelha, azul) — cada cor só existe uma vez em toda a masmorra, com notificação narrativa ao encontrá-las.
- **Seis classes jogáveis**, cada uma com uma perícia própria (ver tabela abaixo), incluindo recarga por turnos/salas caminhadas onde aplicável.
- **Veneno Raro** (item exclusivo do Ladino): imbui a arma equipada e envenena o alvo quando o dano penetra a armadura — com restrições por tipo de arma.
- **Combate por turnos com iniciativa**, registro de dados detalhado (cada rolagem e modificador explicado), pausas dramáticas e barra de vida em tempo real.
- **Tela de permadeath** ao cair: bloqueia qualquer ação, deixando só "Nova descida" e "Ver histórico" (o registro completo daquela partida).
- **Combate contra o Ciclope** para conquistar o Tesouro e vencer a masmorra.

---

## Regras principais (resumo)

Para as regras completas e o texto original, veja [`delve6.txt`](./d6.txt) ou [`delve6-book.pdf`](./delve6-book.pdf). Resumo de referência rápida:

### Atributos

Distribua **3, 2, 1, 0** entre FOR, AGL, PRE e DUR, sem repetição.

| Atributo | Determina |
|---|---|
| **FOR** | Dano base e testes de força |
| **AGL** | CA (esquiva) e acerto em ataques, além de testes de agilidade |
| **PRE** | Carisma, coragem, inteligência e poder mágico |
| **DUR** | Pontos de vida (`PV = DUR + d6`) |

**Classe de Armadura:** `CA = AGL + d6` (considerando modificadores de armadura sobre a AGL total)

### Classes e perícias

| Classe | Perícia |
|---|---|
| **Bárbaro** | Fúria de Sangue — com PV ≤ metade do máximo, ataques corpo a corpo causam +2 de dano. |
| **Cavaleiro** | Guarda de Aço — rola d6, somando o valor à CA até o próximo turno; se o d6 do próximo ataque inimigo for igual, contra-ataca de graça; se o d6 rolado for 6, também anula um crítico inimigo por completo. |
| **Mago Elemental** | Conjura d6 + PRE de dano ignorando armadura. Recarrega em 3 turnos ou salas caminhadas. Em d6=1 a magia falha e causa 1 de dano ao próprio Mago. |
| **Warlock** | Pacto Sombrio — o próximo ataque ganha vantagem (anula a desvantagem da escuridão) e um crítico inimigo nesse meio-tempo é anulado. Recarrega em 3 turnos ou salas caminhadas. |
| **Ladino** | Golpe Furtivo — o primeiro ataque de cada combate rola com vantagem (2d6, usa o maior). |
| **Caçador** | Mira Certeira — ataques com Arco nunca erram e causam +1 de dano fixo. |

### Armas

| Arma | Dano | Requisito |
|---|---|---|
| Desarmado | FOR | — |
| Cajado | d6 + 0 (+2 PRE) | Somente Mago Elemental |
| Adaga | d6 + 1 | — |
| Espada Curta | d6 + 2 | — |
| Espada Longa | d6 + 3 | FOR ≥ 2 |
| Martelo de Guerra | d6 + 4 | FOR ≥ 3 |
| Arco | d6 + 1 | AGL ≥ 2 · em crítico, rola dano duas vezes e usa o maior |

Adaga e Arco compartilham essa regra de crítico (duas rolagens de dano, usa a maior).

### Armaduras

| Armadura | Redução de dano | Modificador de AGL | Requisito |
|---|---|---|---|
| Capuz | -0 | +2 AGL | — |
| Armadura de Couro | -1 | +1 AGL | — |
| Armadura Bárbara | -2 | — | — |
| Armadura de Placas | -3 | -1 AGL | FOR ≥ 2 |

### Consumíveis

| Item | Efeito |
|---|---|
| Coquetel Verde | Cura 1 + d6 de PV |
| Lockpick | Testa AGL para destrancar portas sem arrombar (gasta 1 por uso) |
| Tocha | Remove a desvantagem da escuridão e revela itens ocultos; dura d6 salas/movimentações |
| Veneno Raro *(exclusivo do Ladino)* | Imbui a arma equipada; envenena o alvo (1 PV/turno) quando o dano penetra a armadura. Não funciona em Cajado ou Martelo; com Arco, o efeito se perde em caso de erro. Guarda Esqueleto é imune. |

Usar qualquer consumível durante o combate gasta o turno.

### Combate

- **Acerto:** `AGL + d6 vs CA` — um d6 natural = 6 é um acerto automático que também ignora a armadura do alvo ao aplicar dano.
- **Dano:** `FOR + d6 + n(arma) - armadura do alvo`
- **Iniciativa:** role d6 — acima de 3, o jogador age primeiro; 3 ou menos, o inimigo age primeiro.
- **Lutar no escuro** aplica desvantagem (rola dois d6, usa o menor) em rolagens de ataque.
- **Fugir** testa AGL vs a CA do inimigo.

### Inimigos 

| Inimigo | FOR | AGL | PRE | DUR | Traço |
|---|---|---|---|---|---|
| Guarda Esqueleto | 1 | 2 | 0 | 3 | Imune a veneno; ao cair, reergue-se com metade do PV (+1 se ímpar) |
| Kobold | 2 | 3 | 0 | 1 | 1 em 6 de aparar um ataque, anulando o dano e contra-atacando |
| Ciclope (chefe) | 3 | 3 | 3 | 6 | 1 em 6 de rugido que cancela o turno do jogador (teste de PRE resiste) |

---

## The Forgotten Vault

O módulo introdutório de DELVE6: uma masmorra esquecida, uma fortuna perdida, uma única saída. O gerador de masmorra segue este algoritmo:

1. **Entrada fixa.**
2. Role d6 para o tipo da primeira área (saguão, corredor, hub, escadaria, poço, elevador).
3. Role d6 para o que existe ao fundo dela: passagem aberta, porta destrancada, porta trancada, portão rúnico, ou uma bifurcação.
4. Role d6 para a nova área alcançada (corredor circular, beco sem saída, escada espiral, armadilha, sala escura, prisão).
5. Role d6 para um evento nessa sala (combate, nada, ouro, consumível ou joia).
6. Repita os passos 3–5 para cada exploração às cegas, até reunir as três joias e abrir o Portão Rúnico. Voltar a salas já exploradas é permitido, mas revisitá-las rola risco de reencontro.
7. Enfrente o Ciclope para alcançar o Tesouro e sair da masmorra.

Este módulo **não inclui** sistema de retorno à superfície, loja ou acampamento — esses elementos ficam livres para expansões.

---

## Crie o seu Delve

> Você pode criar módulos, cenários, monstros, classes, campanhas e adaptações para DELVE6 CORE livremente e gratuitamente. Créditos são apreciados, mas não obrigatórios. Faça algo interessante.

O sistema é livre para modificação, expansão e reinterpretação — mas a premissa original é usar **apenas um d6**. Expandir o sistema de forma desordenada pode exigir mais dados; se isso acontecer, considere se ainda é um "Delve" ou já é outra coisa (o que também é válido!).

Na versão em HTML, classes, armas, armaduras e inimigos vivem em objetos JavaScript simples e comentados (`CLASSES`, `WEAPONS`, `ARMORS`, `ENEMIES`) perto do topo do arquivo — um bom ponto de partida para hackear sem precisar entender o resto do código.

**Hack it. Expand it. Publish it.**

---

## Licença

Este projeto interativo em HTML é distribuído sob a **Licença MIT** — veja [`LICENSE`](./LICENSE) para o texto completo.

O livro é licenciado sob Creative Commons Attribution 4.0 International (CC BY 4.0).

© 2026 Ashen Desk. DELVE6™ and its logo are trademarks of Ashen Desk

## Créditos

Criado por **Bandeirinha**.
