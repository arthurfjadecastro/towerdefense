# GDD · Tower Defense Tactics · v0.9

Nov 19, 2026 · @John

Versão compilada em 19/11/2026 a partir da v0.8, do GDD v0.6 (incluindo a seção 17, que não tinha entrado na v0.7), do compilado de 18/11, das decisões de 19/11, das avaliações v0.6 e v0.7 e da pesquisa de fórmulas. Esta é a **fonte única da verdade** do jogo: tudo sobre o jogo é tratado na conversa padrão do projeto, e decisões novas entram aqui. Onde a v0.9 muda a v0.8, isso está indicado com "(muda a v0.8)"; o que é novo, com "(novo na v0.9)". Itens marcados como **Pendente** ainda não foram decididos.

## 1. Visão do jogo

Jogo mobile vertical de tower defense tático com tema mitológico. O castelo é o centro do jogo: o jogador monta tropas, evolui o castelo por três eras, constrói torres e usa um herói e um deus para barrar ondas de inimigos que avançam por rotas até o castelo.

Pilares de design:

- Estratégia e tática: o jogador precisa pensar, e cada decisão em um lado (tropa, torre, castelo) prejudica outro.
- Clareza: o jogador sempre vê o que vem pela frente (próxima onda, tipos de inimigo, alcance) antes de decidir.
- Progressão que ajuda, mas não decide: a tática vence a partida; melhorias permanentes são um plus.
- Identidade visual: o castelo evolui e muda de aparência conforme a era e o deus escolhido.

Diferencial em relação ao Kingdom Rush: lá a torre de quartel repõe unidades sozinha; aqui o jogador produz tropas no castelo por ação própria, sem reposição automática.

Narrativa de base: o jogador é como um nômade que se estabeleceu em uma região e constrói sua base. Na última era, já domina o local e a cultura. Existe uma história por trás da campanha e um ponto de partida no mapa (Pendente).

Referências (novo na v0.9): Age of Mythology (tema mitológico, deuses e unidades míticas), Kingdom Rush (clareza de rotas e torres, chamada antecipada de ondas) e árvores de evolução no estilo Path of Exile (ramificações das tropas). A ideia é combinar elementos de arquiteturas diferentes para um jogo único num mercado saturado.

Visão de longo prazo (novo na v0.9): o que está definido é a estrutura core. Acessórios serão acoplados depois, como coleções, outros recursos além de Ouro e Comida e chance de drops de itens raros durante a partida. Eles são importantes para a continuidade e para o jogador voltar.

## 2. Escopo do MVP

O MVP existe para testar o núcleo: movimentação, disposição do mapa, disposição das torres, funcionamento do castelo e criação de tropas. O balanceamento fino fica para a segunda versão.

Regra de escopo: nada novo avança até o MVP estar bom. Se algo novo entrar no MVP, é com critérios de validação próprios, nunca como exceção.

### 2.1 MVP em três partes

O MVP é dividido em três partes, cada uma com métricas e meta numérica própria (metas Pendentes):

1. Combate, economia e torre.
2. Eras e evoluções.
3. Herói e Favor Divino.

**Critério de sucesso do MVP** (novo na v0.9): movimentação, bloqueio, ataques e antecipação de ondas funcionando. Se funcionar, o jogo avança. As metas numéricas de cada parte continuam Pendentes.

### 2.2 O que entra no MVP

- Uma fase jogável de cerca de 15 minutos e 10 ondas, com **3 rotas** e ondas progressivas. As ondas não usam necessariamente as três rotas ao mesmo tempo (muda a v0.6, que deixava 1 a 3 em aberto).
- Castelo com três eras (nomes provisórios), evolução paga com Ouro.
- Três linhas de tropa: infantaria, cavalaria e arqueiros, com tropas fixas (sem ramificações).
- Montagem de tropas de 2 a 10 unidades, com controle coletivo por toque, e o botão **repetir última tropa**.
- **Presets de tropa por faixa de recurso** (pouco, médio e muito recurso), com envio direto para a bandeira (novo na v0.9, seção 5.1).
- Um herói base, com status superiores aos das tropas, movimento livre e respawn de 120 segundos. **Sem nenhuma habilidade, nem ativa nem passiva** (muda a v0.8, que só tirava as ativas). A progressão com habilidades fica para depois do MVP.
- Uma torre simples de arqueiro, em pontos fixos do mapa, com 2 flechas por disparo.
- Um deus, Thanatos, sem Poder Divino. Primeira vantagem: retorno de 25% da Comida das unidades mortas.
- Até três tipos de inimigo, espelhando infantaria, arqueiro e cavalaria. No MVP, todos são comuns e tiram 1 vida do castelo.
- Economia com Comida, Ouro e Favor Divino: renda por tempo pequena e ajustável, ganho por abate e retorno por unidade morta.
- Sinalizador de onda, antecipação de onda com bônus, pausa de menu e pausa tática.
- Tutorial em 4 dicas contextuais (seção 13).
- Cálculo de estrelas pela saúde do castelo.

### 2.3 O que fica fora do MVP

- Tipos de dano (perfurante, magia) e regra de vantagem entre tropas.
- Ramificações de evolução final.
- Habilidades do herói (ativas e passivas), múltiplos heróis, múltiplos deuses e Poder Divino.
- Segundo deus e Unidade Mitológica.
- Composições de tropa pré-definidas montadas fora da partida (distintas dos presets por faixa de recurso, seção 5.1).
- Torres de gelo, veneno, magia, catapulta e óleo quente.
- Chefes que destroem ou desabilitam torres.
- Mapa de campanha completo, fases secundárias, biblioteca de inimigos, loja, diamantes e monetização.
- XP do herói e gasto de estrelas.
- Arquitetura online (vem depois do MVP, mas antes de qualquer recurso de compra).
- Som e música (novo na v0.9).

### 2.4 Pendências que bloqueiam o MVP

1. **Fórmula de dano e escala de status.** Decisão pendente; ver recomendação da pesquisa em 11.4 (muda a v0.8: a pesquisa já foi feita).
2. **Tabela de status e custos** de cada tropa, do herói, da torre e dos três inimigos.
3. **Tabela de economia:** recurso inicial, renda por tempo, valor por abate, custo de cada evolução, bônus de antecipação.
4. **Lista de ondas da fase de teste:** quantidade e tipo de inimigos por onda e por rota.
5. **Regras de mapa:** tamanho dos raios, posição dos pontos de torre, comprimento das rotas.
6. **Custo e alcance da torre.**
7. **Tempo de espera entre ondas**, deduzido do tempo médio de combate por onda.
8. **Favor Divino:** valor inicial, renda e custo do ressurgimento do herói.
9. **Interface mínima:** painel do castelo, carrossel de cartas, HUD, sinalizador, menus de pausa, tela de preparação da fase e tela de constelações (muda a v0.8).
10. **Bandeira de ponto de encontro:** posição inicial e área de toque (o envio foi decidido em 19/11, seção 5.1).

Saíram desta lista na v0.9, por já estarem decididos: dano ao castelo (20 vidas, comum tira 1; seção 2.5), número de ondas (10 no MVP, 10 a 15 no jogo; seção 2.5) e condição de vitória (seção 3).

### 2.5 Decisões de 17/11 revisadas em 19/11

Estas decisões apareciam na avaliação da v0.6 como tomadas em 17/11 e foram revisadas com o John em 19/11. Só a fórmula de dano **continua pendente**; o resto está confirmado.

| Tema | Decisão | Status |
| --- | --- | --- |
| Fórmula de dano | Sugestão: dano = A × 100 / (100 + D) | Pendente. Pesquisa feita; ver recomendação em 11.4 (muda a v0.8) |
| Vida do castelo | 20 vidas. Inimigo comum tira 1, forte tira 2, chefe tira de 3 a 5 | Confirmado em 19/11 |
| Número de ondas | De 10 a 15 por fase, conforme a dificuldade. A fase de teste do MVP tem 10 | Confirmado em 19/11 |
| Duração da fase | Cerca de 15 minutos; fases com mais ondas podem ser mais longas, sem encurtar a espera | Confirmado em 19/11 |
| Motor | Godot | Confirmado em 19/11 |
| Plataformas | Celular e tablet. Só Android no início (iOS depois) | Confirmado em 19/11 |
| Conexão | Online obrigatório | Confirmado em 19/11 |

### 2.6 Produção e plataforma

Novo na v0.9.

- **Ritmo:** sem prazo fixo, com prioridade para a qualidade.
- **Equipe:** John e um colega (Arthur), usando IA e o Claude Code.
- **Arte:** já existem algumas artes; o estilo gráfico final não está fechado.
- **Testadores:** John, o colega e poucas pessoas próximas. Testadora prevista: a esposa do John (seção 15).
- **Plataforma:** celular e tablet; só Android no começo.
- **Online obrigatório**, para evitar versões desatualizadas. Se a conexão cair, o jogo pausa e oferece continuar.

## 3. Estrutura de uma partida

1. O jogador escolhe a fase no mapa externo e, na tela de preparação, o deus, o herói e o preset de estrelas (seção 3.4).
2. A fase começa com castelo simples e frágil, recursos mínimos e portão voltado para a zona de combate.
3. A primeira onda não tem contagem de tempo: o jogador inicia pelo sinalizador. As seguintes iniciam sozinhas após um tempo de espera.
4. Antes de cada onda, um sinalizador na base da rota mostra o ponto de início e o caminho.
5. O jogador monta tropas, constrói torres, movimenta tropas e herói e evolui o castelo.
6. A fase termina com vitória ou derrota (seção 3.5). A saúde do castelo ao final define as estrelas.

### 3.1 Sinalizador e antecipação de onda

Igual ao Kingdom Rush, para evitar cliques: **um toque** no sinalizador mostra o que vem na onda (quantidade e tipos); **dois toques rápidos** antecipam a onda, e o bônus proporcional ao tempo adiantado cai na hora. O jogador só vê a próxima onda.

Risco: adiantar uma onda com inimigos ainda vivos soma as duas. O bônus precisa compensar sem virar obrigação.

### 3.2 Pausa

- **Pausa de menu:** um menu cobre o mapa e o jogador não pode dar comandos.
- **Pausa tática** (muda a v0.6): congela o jogo com o mapa visível. O jogador pode olhar e selecionar, mas não dar ordens. Se isso virar problema no teste, pode voltar a bloquear a tela.

### 3.3 Aceleração

Opção de conforto de até 2x, que acelera tudo, inclusive a contagem da próxima onda. Nunca é requisito para estrelas.

### 3.4 Tela de preparação da fase

Decidido em 19/11 (muda a v0.6, em que deus e herói eram escolhidos na área externa, no topo do mapa do mundo). Motivo: evitar que o jogador esqueça de trocar o deus para a fase.

- Ao selecionar a fase, o jogador vê as informações dela (características e, provavelmente, os monstros), com alguns elementos ocultos por interrogações.
- Fluxo: deus, herói e Iniciar jogo. Poucos toques para quem aceita os padrões (muda a v0.8, que falava em três toques).
- Carrosséis para deus e para herói, com referência na seleção de heróis do Dota.
- O jogador define com um toque o deus padrão e o herói padrão. A tela abre com o padrão; sem padrão definido, abre com a última escolha.
- Em outra área da tela, ele escolhe o preset de estrelas para aquela combinação de deus e herói (novo na v0.9), com a mesma regra: padrão ou último usado.
- Ideia registrada: presets de combinação deus e herói (por exemplo, Zeus e Hércules).

### 3.5 Fim de fase e dano ao castelo

Novo na v0.9.

- **Derrota:** com zero vidas, a fase acaba na hora. Sair no meio da fase também conta como derrota (recompensa da derrota na seção 14).
- **Vitória:** quando morre o último inimigo da última onda.
- **Feedback de dano:** o inimigo que chega ao castelo tira vidas e some. As vidas aparecem como corações, e o castelo se deteriora visualmente (por exemplo, pegando fogo).

## 4. Economia

| Recurso | Fonte | Uso |
| --- | --- | --- |
| Comida | Renda por tempo, abates e retorno por unidade morta | Aquisição de tropas |
| Ouro | Renda por tempo e abates | Evolução do castelo, torres e suas evoluções, evolução de tropas |
| Favor Divino | Renda por tempo e abates, mínimo inicial | Ressurgimento do herói e Poder Divino |

- **Renda por tempo no MVP** (muda a decisão de 17/11, que tirava a renda por segundo): pequena e ajustável, a mesma prevista para o jogo completo, para a falta de recurso não contaminar o teste de movimentação e jogabilidade. A renda começa quando o jogador chama a primeira onda (decidido em 23/11). Perder recurso por estratégia errada continua sendo decisão do jogador.
- Todos os inimigos concedem recursos proporcionalmente à dificuldade, e o ganho cresce conforme a onda.
- **Retorno por unidade morta** (muda a v0.6, em que tropa morta não gerava recurso): todos os deuses devolvem 15% do valor da unidade morta, em Comida. Thanatos devolve 25%. O custo das tropas é igual para todos os deuses; só o percentual muda. O retorno é por unidade, proporcional: cai a cada unidade que morre, não só quando a tropa inteira morre.
- Existe um saldo inicial mínimo para a compra e a defesa iniciais.
- O jogo deve ser balanceado para o jogador não chegar à última onda com muito recurso sobrando. Muito recurso não garante vitória.
- Hades não tem mais o retorno de 20%: fica sem definição, como os demais deuses (decidido em 19/11).
- **Troca de Ouro por Comida** (novo na v0.9, do compilado de 18/11): fora do MVP. Só entra se o teste mostrar jogadores travados com Ouro parado.

### 4.1 Valores iniciais (decididos em 20/11/2026)

| Item | Custo |
| --- | --- |
| Arqueiro (por unidade) | 50 de Comida |
| Infantaria (por unidade) | 70 de Comida |
| Cavalaria (por unidade) | 110 de Comida (era 90; mudou em 23/11) |
| Construir torre | 300 de Ouro |
| Evoluir o castelo para a 2ª era | 500 de Ouro |
| Evoluir o castelo para a 3ª era (final) | 800 de Ouro |
| Saldo inicial da partida | 1.000 de Ouro e 1.000 de Comida |

O custo da tropa é a soma das unidades. Ainda pendentes: renda por tempo, valor por abate, custo das evoluções de tropa e de torre, Favor Divino inicial e custo do ressurgimento do herói, bônus de antecipação.

**Abate e ondas (23/11/2026, valores iniciais para a planilha):**

- Inimigo fraco dá de 15 a 20 de Comida e de 8 a 10 de Ouro. O Ouro é baixo de propósito, para ficar disputado entre torre, era e evolução, mas suficiente para as evoluções.
- Ondas 1 e 2 são de farm, só com inimigos fracos: poucos, mas suficientes para o jogador juntar recursos. Da onda 3 em diante, mistura fracos e fortes.
- Proposta de orçamento por onda, a validar: fraco vale 1 ponto e forte vale 3; a onda n vale 10 + 3 × (n − 1) pontos (onda 1 = 10 fracos; onda 10 = 37 pontos, cerca de 16 fracos e 7 fortes). No MVP, "forte" é o tipo comum mais resistente.
- Valor do abate do inimigo forte: pendente.

## 5. Tropas

Unidade é o combatente individual. Tropa é o agrupamento selecionado e comandado pelo jogador.

- Três linhas: infantaria (hoplitas), cavalaria e arqueiros, todas disponíveis desde o início.
- Cada tropa tem de 2 a 10 unidades. A compra é instantânea: a tropa fica disponível no castelo e depende do deslocamento até o local de uso.
- Grupos maiores custam mais. A economia limitada faz o jogador escolher entre tropa grande, tropa simples e guardar recurso.
- Tropa mista é permitida.

### 5.1 Montagem e compra

- O jogador seleciona unidades nas cartas e monta a tropa. Durante a montagem o saldo não muda: a tela mostra o custo acumulado da tropa por recurso, e o valor só é abatido ao confirmar.
- Uma carta fica vermelha quando o saldo não cobre o custo já acumulado mais o custo dela.
- Com recurso para uma só unidade, ela desce para o deck da tropa e as demais cartas ficam vermelhas. O botão de confirmar só habilita com duas unidades (máximo dez).
- **Repetir última tropa:** entra no MVP.
- **Confirmar e enviar** (decidido em 19/11): ao confirmar, a tropa sai do castelo. Sem destino definido, ela para no centro, no portão (muda a v0.8, que dizia só "no portão"). Ao selecionar o castelo, o jogador pode definir uma bandeira de ponto de encontro, também chamada de estandarte (novo na v0.9), como no Age of Mythology; ela fica visível no mapa e tudo que for produzido vai para lá. Bandeira esquecida numa rota calma é erro de estratégia do jogador, sem aviso automático.
- **Bandeira única (19/11):** há uma só bandeira de ponto de encontro, não uma por rota.
- **Presets de tropa por faixa de recurso** (entra no MVP; muda a v0.8, que deixava em discussão): o jogador salva composições para pouco, médio e muito recurso. Na partida, castelo, preset e confirmar: se houver recurso, a tropa é produzida e vai direto para a bandeira. Objetivo: reduzir os toques de reposição sob pressão (problema E1 da avaliação v0.7).
- Depois do MVP: composições pré-definidas (por exemplo, 4 arqueiros, 5 infantarias e 1 cavalaria), montadas pelo jogador fora da partida e usadas dentro dela, sem tirar a escolha livre.

### 5.2 Comando e formação

- Tocar na tropa e depois no mapa mostra o caminho que ela vai seguir e a move. Tocar na tropa e em **abrir** leva ao detalhamento da postura e da formação.
- **Controle coletivo** (novo na v0.9): não há movimento individual enquanto a tropa tiver duas ou mais unidades.
- Tropa sem destino válido sai pelo portão e fica parada ali.
- Formação padrão: falange (bloco quadrado, fácil de tocar), na ordem cavalaria, infantaria e arqueiros. O jogador pode trocar para bloco, fila ou coluna.
- Movimento da tropa mista: a tropa sai em bloco, a cavalaria vai à frente puxando a direção e o resto segue no rastro, formando uma seta que se estica. Com a tropa selecionada, a seta e o raio ficam visíveis.
- As tropas andam em blocos, com espaço visível entre as unidades e sem sobreposição. Uma unidade passa pela outra sem empurrão.

### 5.3 Papéis

| Linha | Papel | Característica |
| --- | --- | --- |
| Infantaria | Linha de frente | Razoavelmente barata, bloqueia o avanço e tanka. Vira unidade decisiva com evoluções. |
| Cavalaria | Reação rápida | Mais cara, mais HP, um pouco mais de status e maior velocidade. Entra em combate assim que avista o inimigo, sem esperar o resto, e aguenta até a tropa chegar. O jogador pode adiantá-la ou recuá-la. |
| Arqueiros | Dano à distância | Baratos e frágeis, ficam atrás. Atacam sem depender da infantaria e têm boa área de ataque. |

A regra de vantagem entre tropas e os tipos de dano ficam para depois do MVP. No MVP, a viabilidade de uma unidade é comparada pelos status (HP, ataque e defesa).

### 5.4 Capacidade de bloqueio

O inimigo excedente segue a rota. Versão simples:

| Unidade | Bloqueia | Evolução |
| --- | --- | --- |
| Infantaria | 1 | Passa a 2 só na última evolução (campeã) |
| Cavalaria | 1 | Passa a 2 só na última evolução (mudou em 23/11); a intermediária (pesada) ganha só status. No futuro, pode chegar a 3 |
| Arqueiros | 0 (só bloqueia se for alcançado) | — |
| Herói | 2 | 3 como possível evolução do herói ou item que o jogador adquire |

Arqueiro do jogador (novo na v0.9): só bloqueia se um inimigo o alcançar. Nesse caso, mantém o mesmo ataque e intervalo, sem penalidade; a penalidade é morrer rápido.

Proposta em discussão: o reagrupamento (várias unidades no mesmo alvo) vale só para as tropas do jogador; para os inimigos vale a capacidade de bloqueio.

### 5.5 Evolução de tropas

- Cada linha tem três etapas, por exemplo infantaria leve, pesada e campeã. Cada era libera uma evolução, comprada separadamente com Ouro.
- A evolução vale para todas as unidades da linha, as que já existem e as futuras.
- Depois de evoluir uma linha, só se compra a versão nova, pelo mesmo preço. Unidade que morre não gera perda extra (novo na v0.9).
- Quem chega à última era sem ter evoluído pode comprar as três evoluções de uma vez (novo na v0.9).
- Um toque na evolução mostra um card com ganhos de status (ataque, defesa, vida), mudança visual e custo antes de comprar. Evoluções bloqueadas aparecem esmaecidas, com a exigência de era. O mesmo card vale para as torres (seção 9).
- Depois do MVP: ramificação final com duas opções, cada uma com card e uma vantagem específica (característica, não habilidade ativa). Exemplos, nada fechado: mais dano, regeneração de vida, custo de aquisição menor. A escolha é definitiva. A ramificação final também vale para as torres, só depois do MVP (seção 9).

## 6. Herói

Unidade única, escolhida fora da partida em um carrossel. Heróis bloqueados aparecem esmaecidos.

- **MVP:** o herói não tem nenhuma habilidade, nem ativa nem passiva (muda a v0.8, que só tirava as ativas). Habilidades e a progressão com habilidades ficam para depois do MVP.
- Status superiores aos das tropas. Não é imortal.
- **Movimento livre** (muda a v0.6): circula entre os raios e em todas as rotas, pode ficar em qualquer lugar, inclusive na ponta da rota, e luta fora dos raios.
- Bloqueia os 2 primeiros inimigos que encontrar, sem distinguir tipo. Bloquear 3 fica como possível evolução do herói ou item que o jogador adquire (novo na v0.9). O balanceamento usa a quantidade de inimigos e o equilíbrio entre o dano dele e a defesa inimiga: ele segura parte do problema sem resolver tudo sozinho.
- Respawn: ao morrer, cooldown de 120 segundos. Depois disso o jogador paga Favor Divino para ele voltar, sempre no portão. O Favor Divino inicial é menor que o custo, para o jogador não matar o herói de propósito.
- No início da partida, herói e torre fazem o farm inicial de recurso.
- Diferencial: habilidades ativas com cooldown, usadas pelo jogador (fora do MVP). Exemplo: Heitor, príncipe de Troia, com o brado da vitória, que dá bônus de ataque e defesa às tropas próximas.
- Depois do MVP: começa com uma habilidade própria. Ao subir de nível libera outras: no máximo duas ou três ativas, as demais passivas.
- Progressão: até 10 níveis, por XP ganho nas partidas em que participou, com barra própria fora da partida. O XP depende da dificuldade da fase (por exemplo, um herói do zero sobe dois níveis numa fase difícil e um numa fácil). Herói novo começa do zero e pode ser levado a uma fase difícil.
- Grind mínimo aceito: repetir fases para ganhar XP é opção do jogador, controlada para não tirar o encanto.
- Heróis desbloqueáveis são diferentes, não melhores.

## 7. Deuses

- O jogador escolhe um deus antes da fase. O deus dá vantagens em uma camada diferente da do herói: economia, custo e bônus de linhas de tropa.
- O jogo começa com deuses menores (Thanatos, Hipnos, Eros e Perséfone). Os grandes (Hades, Zeus, Poseidon) são desbloqueados ou comprados e ainda não têm definição. Deuses são diferentes, não melhores.
- Deuses ajudam em certas fases (por exemplo, inimigos mágicos pedem um deus de escudo mágico; inimigos de fogo, um deus com proteção contra incêndio). É vantagem estratégica, não obrigatória: outros deuses também vencem.
- Cada deus muda a aparência do castelo (bandeiras, elementos visuais e uma estátua).
- Cada deus terá vantagens, um Poder Divino e, na última era, uma Unidade Mitológica, que se move como o herói e usa poderes próprios sem comando do jogador.
- Ideia em maturação: segundo deus na última era. Risco: só ajudaria quem já está ganhando.
- **MVP:** Thanatos, sem Poder Divino, com retorno de 25% por unidade morta como primeira vantagem.

## 8. Castelo e eras

- O castelo é o centro funcional: monta tropas, evolui e define o raio de atuação das tropas.
- Três eras, com nomes provisórios. A v0.5 usava Pioneiros, Fundação e Domínio (Pendente).
- **Tempo de evolução: cerca de 5 segundos** (muda a v0.6, que previa cerca de 30). O importante é o jogador ver o castelo sendo construído e crescendo. Durante a evolução o castelo funciona normalmente.
- Cada era aumenta o raio, deixa o castelo maior, libera pontos de torre, evoluções de torre e de tropa. A compra não tem efeito imediato na batalha (decidido em 23/11). As tropas mantêm seus status.
- Sem teto de unidades por era: o limite é o recurso.
- **Era como resgate:** quem sente as tropas morrendo e tem recurso guardado pode evoluir de era para liberar evoluções e melhorar em campo. É escolha de quem economizou, não ajuda automática a quem está atrás. Quem está perdendo provavelmente seguiu o caminho errado.
- A evolução de era usa Ouro. XP como requisito fica para depois.
- Evoluções do castelo também mostram card com ganhos, mudança visual e custo antes da compra.
- **Dano ao castelo** (novo na v0.9): o inimigo que chega tira vidas e some. As vidas aparecem como corações e o castelo se deteriora visualmente (por exemplo, pegando fogo). Com zero vidas a fase acaba na hora; a vitória vem quando morre o último inimigo da última onda (seção 3.5).

## 9. Torres

- Construídas só em pontos específicos ao longo das rotas, cerca de 3 a 4 por fase. Alguns pontos têm raio que cobre duas rotas.
- Pode-se construir torre em ponto de rota ainda não liberada, como risco de decisão (novo na v0.9).
- Custam Ouro, mais que uma tropa. O Ouro é disputado entre torres, evolução do castelo e evolução de tropas.
- **Território (confirmado em 19/11):** o raio de ataque da torre também é a área onde o jogador pode alocar tropas. Dentro dele a tropa se move livremente (borda superior, inferior etc., conforme a estratégia). Atacada, ela pode sair para contra-atacar, até cerca de metade do alcance do inimigo além da zona (seção 11.3; muda a v0.8, que aqui dizia "meio raio").
- **Torre x arqueiros:** a torre não exige recompra constante e tem velocidade de ataque maior.
- Dispara várias flechas em sequência, multiplicando o dano. **A torre do MVP começa com 2 flechas por disparo**, o que permite estratégia de início de jogo e finaliza inimigos quando o jogador usa só o herói no começo.
- Trava no primeiro inimigo que entra no raio até ele morrer ou sair do raio; nesse caso, passa ao inimigo mais próximo dentro do raio. Com inimigos de rotas diferentes, ataca sempre o primeiro no raio, o que cria o dilema de qual rota defender.
- Inimigos básicos não destroem torres. Só inimigos específicos, como um chefe, poderão destruí-las ou desabilitá-las por um tempo.
- Evoluções ligadas às eras: a primeira é simples (mais raio e +2 de ataque) e não exige era nova; a segunda exige a próxima era. O "+2 de ataque" será revisto junto com a escala de status (seção 11.4).
- Evoluções de torre também mostram card com ganhos, mudança visual e custo antes da compra (novo na v0.9). A ramificação final em duas opções também vale para torres, mas só depois do MVP.
- Futuro: torres de gelo, veneno, magia, catapulta e óleo quente.
- Pendente: dano, alcance e custo da torre do MVP.

## 10. Mapa e rotas

- **MVP com 3 rotas.** As ondas podem chegar por rotas diferentes em momentos diferentes.
- O raio do castelo recebe várias entradas de rota. As tropas ficam dentro do raio, no limite de cada rota, e não agrupadas no castelo.
- Os finais de rota são espaçados para uma mesma tropa não defender duas rotas. O inimigo chegar ao final da rota deve ser de fato um problema.
- As rotas são visíveis no mapa. Se uma rota nova abrir no meio da partida (por exemplo, inimigos saindo de uma cachoeira ou de um lago), o jogador recebe antes um sinal visual igual ao sinalizador, mostrando a saída e o caminho.
- Tela vertical, câmera elevada, castelo completo na base, portão frontal voltado para a zona de combate. Sem ataques pela retaguarda.

## 11. Combate

### 11.1 Movimento e alvo

- O inimigo sempre segue a rota e só para quando algo do jogador o bloqueia (tropa, herói, magia). Sem bloqueio, segue até o castelo. Exceção: o inimigo corpo a corpo vai buscar os arqueiros do jogador próximos da rota (seção 11.8).
- **Exceção: arqueiro inimigo** (muda a v0.8). Sempre que tiver um alvo dentro do alcance, ele para de andar para atacar. Quando o alvo morre ou sai do alcance, volta a seguir a rota. Alvos válidos: só unidades do jogador e herói; torre e castelo nunca são alvo do arqueiro inimigo (confirmado em 19/11). Sem guerreiro no alcance, ele continua avançando. O guerreiro atacado se move para contra-atacá-lo (seção 11.3).
- **Estabilidade de alvo** (muda a v0.8): a unidade que está bloqueando um inimigo fica nele até um dos dois morrer. Se a tropa do jogador vence, bloqueia o inimigo livre mais próximo dentro do raio de interceptação. Se o inimigo vence, a unidade que ajudava a bater nele assume o bloqueio na hora; ele só segue a rota se não houver nenhuma unidade do jogador próxima capaz de bloqueá-lo (seção 11.8). Exceções: a perseguição ao arqueiro de fora do raio (seção 11.3) e a troca de alvo do excedente (abaixo).
- **Troca de alvo do excedente** (novo na v0.9): uma unidade excedente, que ataca um alvo já bloqueado por outra, larga esse alvo para bloquear um inimigo livre que esteja dentro do raio de interceptação. Prioridade: primeiro bloquear todo inimigo livre possível, depois concentrar vários aliados no mesmo alvo. Cada tropa calcula por si.
- Sem limite de unidades por zona. O limite é o recurso.
- Construção em duas etapas: primeiro uma versão mínima (um bloqueio por inimigo, sem sobreposição de tropas), depois a completa, com a redistribuição e a sobreposição de raios (seção 11.6).

### 11.2 Intervalo de ataque

**O intervalo de ataque é estado da unidade** (muda a decisão de 17/11): continua contando durante o movimento e na troca de alvo. O ataque imediato só ocorre se o intervalo já tiver acabado. Isso fecha a brecha da retirada gratuita.

### 11.3 Arqueiro inimigo fora do raio

Muda a v0.6, em que a tropa não saía do raio:

- A unidade atacada persegue o atacante à distância, mesmo passando um pouco do raio, até cerca de metade do alcance do inimigo além da zona. Depois de abatê-lo, volta ao ponto definido pelo jogador. Esta é a medida única da perseguição em todo o documento (seções 9 e 17).
- Só persegue quem não está em corpo a corpo. Quem está bloqueando não se move e sofre o dano dos dois.
- Uma unidade livre próxima pode atacar o arqueiro de fora mesmo sem estar sendo atacada.
- No máximo 1 ou 2 unidades livres, as mais próximas, perseguem cada atacante à distância.
- Ao tocar na tropa, o jogo mostra o raio de atuação.

### 11.4 Fórmula de dano

**Decisão pendente** (o John pediu para não fechar agora). A fórmula percentual de 17/11 aguarda confirmação (seção 2.5). A pesquisa de 18/11 já foi feita (muda a v0.8, que a tratava como a fazer).

**Recomendação da pesquisa (não decidida):**

- Manter Dano = Ataque × 100 ÷ (100 + Defesa).
- Aumentar a escala de status em cerca de 10 vezes: Defesa de 0 a 200; Ataque por golpe de 10 a 100; HP de tropa de 100 a 600; inimigo comum de 50 a 400; chefe de 2.000 a 10.000.
- Evoluções de Defesa de +10 a +25 e de Ataque de +10% a +20% por nível.
- Cálculo em ponto flutuante, com arredondamento só na exibição, e dano mínimo 1.

O "+2 de ataque" da evolução da torre (seção 9) será revisto junto com a escala.

### 11.5 Regras de ataque

Novo na v0.9 (vem da v0.6, 17.2).

- **Acerto:** todo ataque básico acerta. Sem precisão nem esquiva no MVP.
- **Projéteis:** acompanham o alvo até o impacto e somem se ele morrer, sem buscar outro. Projéteis já disparados continuam quando a tropa recebe nova ordem.
- **Arqueiro do jogador:** só bloqueia se um inimigo o alcançar. Nesse caso, mantém o mesmo ataque e intervalo, sem penalidade. A penalidade é morrer rápido (seção 5.4).

### 11.6 Ponto de defesa e interceptação

Novo na v0.9 (vem da v0.6, 17.2).

- **Ponto de defesa:** a posição escolhida pelo jogador. É o centro da formação, a referência do raio de interceptação e o local de retorno e de reorganização.
- **Reação automática:** todas as unidades corpo a corpo podem sair do ponto de defesa para interceptar, dentro do raio de interceptação, e depois voltam (decidido em 23/11). Arqueiros não avançam.
- **Raio de interceptação:** igual para todas as tropas, cerca de três diâmetros de uma infantaria. Fica oculto e aparece ao selecionar a tropa, junto com o raio de deslocamento. Destinos inválidos são indicados.
- **Sobreposição de raios:** várias tropas podem reagir ao mesmo inimigo sem se fundir. Cada uma mantém composição, ponto de defesa, raio e formação. Faz parte da etapa completa da redistribuição (seção 11.1).
- **Controle coletivo:** sem movimento individual enquanto a tropa tiver duas ou mais unidades (seção 5.2).

### 11.7 Movimento durante o combate

Novo na v0.9 (vem da v0.6, 17.2).

- Mover a tropa durante o combate é permitido. A nova ordem interrompe ataques em preparação, libera os inimigos bloqueados, e a tropa toda segue ao novo destino.
- O inimigo liberado na retirada não persegue e retoma a rota. Sem lentidão, ataque de oportunidade, custo ou cooldown.
- Compatível com a 11.2: o intervalo de ataque continua como estado da unidade durante a retirada.

### 11.8 Decisões de 23/11/2026 (respostas à avaliação v0.9)

Estas regras valem sobre qualquer texto anterior que as contradiga.

- **Quem bloqueia.** Todas as unidades corpo a corpo da tropa podem sair para bloquear, não só a linha frontal, sempre dentro do raio de interceptação.
- **Bloqueio garantido.** O inimigo nunca segue a rota se houver uma unidade do jogador próxima capaz de bloqueá-lo. O rebalanceamento garante isso: se um inimigo fica livre, uma unidade que estava ajudando sai para bloqueá-lo.
- **Herança do bloqueio.** Quando o bloqueador morre, a unidade que ajudava a bater naquele inimigo assume o bloqueio na hora.
- **Arqueiros do jogador.** O inimigo corpo a corpo vai buscar os arqueiros do jogador que estejam próximos da rota. A distância exata ainda precisa ser definida.
- **Trava da torre.** A torre fica no primeiro alvo até ele morrer, mesmo que esteja bloqueado. Se ele sair do raio vivo, a torre passa ao inimigo mais próximo dentro do raio.
- **Renda por tempo.** Começa quando o jogador chama a primeira onda, com os dois toques no sinalizador.
- **Antecipação.** O jogador recebe na hora a renda que ganharia no tempo antecipado, mais uma pequena quantia extra. O valor do extra fica para a planilha.
- **Era.** A compra da era não muda nada imediato na batalha; ela só libera evoluções. Ideia para depois: ao evoluir uma tropa, as unidades em campo recuperam toda a vida, como no Kingdom Rush.
- **Bandeira.** Continua única; o jogador deve se antecipar. O botão do preset mostra o destino, por exemplo "Enviar para a rota A".
- **Ponto de torre duplo.** O raio da torre pode atingir duas rotas, mas a base não é caminhável, e a tropa precisa contornar para ir de uma rota à outra. A distância de interceptação é medida pelo caminho a pé, não em linha reta.
- **Critério de sucesso do MVP.** O MVP valida a movimentação, a evolução do castelo, as torres, o herói e, principalmente, a compra de tropas. O núcleo passa se a testadora pedir para jogar de novo sem sugestão, souber explicar por que perdeu e achar que repor tropas é uma decisão, não uma tarefa cansativa. Se dois desses sinais falharem, o núcleo muda antes de seguir.

## 12. Inimigos e ondas

- MVP: até três tipos, espelhando infantaria, arqueiro e cavalaria. Futuro: mais de 30 tipos (lanceiro, cães de caça, trolls, feiticeiros, gigantes de fogo e de gelo, murmilo, unidades mitológicas).
- Cada região do mapa tem inimigos próprios. Inimigos novos são apresentados e entram numa biblioteca consultável fora da partida.
- A cada onda sobem a dificuldade e a quantidade. A partir de certa onda aparecem inimigos melhorados, um sinal para evoluir, não um muro.
- A fase pode alterar pontualmente a ordem das ondas. Os tipos de inimigo da fase não mudam.
- Risco: espelhar as tropas pode deixar os inimigos genéricos no tema mitológico. Os inimigos temáticos devem chegar cedo.

## 13. Interface e tutorial

- Tocar no castelo abre um painel inferior com abas: Treinar Unidades, Evoluir Castelo e Melhorias. O campo continua parcialmente visível.
- No painel do castelo fica também a ação de definir a bandeira de ponto de encontro, o estandarte (novo na v0.9, seção 5.1). Posição inicial e área de toque seguem pendentes (seção 2.4).
- Treinar Unidades: carrossel de cartas com arte, nome, função, status, custo e ação. Abaixo, a composição da tropa (por exemplo 6/10), o custo acumulado por recurso e os botões Limpar, Repetir última tropa e Confirmar Tropa.
- HUD: recursos e onda no topo, ações e minimapa na lateral direita.
- **Tela de preparação da fase** (novo na v0.9 nesta seção): informações da fase, carrosséis de deus e de herói, definição de padrão, área do preset de estrelas e Iniciar jogo (seção 3.4).
- **Tela de constelações** (novo na v0.9 nesta seção): alocação e redistribuição de estrelas e presets de estrelas, fora das fases (seção 14).
- **Tutorial no MVP:** 4 dicas contextuais, cada uma mostrada uma vez:
  1. Castelo pulsando: "toque para treinar tropas".
  2. Carta de infantaria destacada até confirmar a tropa.
  3. "Toque na tropa e depois no mapa."
  4. Sinalizador: "toque para ver os inimigos; toque duas vezes rápido para chamar a onda".
- **Tutorial do jogo completo** (depois do MVP; novo na v0.9): ao baixar o jogo, uma apresentação guiada. No menu principal, uma área de tutoriais escritos.

## 14. Campanha, estrelas e progressão

- Mapa externo de fantasia, com regiões temáticas (vulcão, campina, montanhas de gelo), fases principais em sequência e fases secundárias não sequenciais.
- Cada fase tem nível de dificuldade e é balanceada individualmente (tropas, inimigos, drops). Cada região pode ter um deus dominante, sem tornar os outros inúteis.
- **Nível recomendado** (novo na v0.9): o nível recomendado da fase é o nível do herói. O jogador pode tentar sem ele.
- Estrelas pelas vidas restantes do castelo, em números inteiros (decidido em 19/11, com 20 vidas): de 20 a 17 = três, de 16 a 10 = duas, de 9 a 1 = uma. A recompensa por estrela é paga uma vez; ao melhorar, só a diferença.
- **Rejogar fase vencida** dá XP e recursos limitados (novo na v0.9).
- **Estrelas** só se ganham jogando, nunca com diamantes. São alocadas em constelações (decidido em 19/11), inspiradas na árvore passiva do Path of Exile, porém simplificadas. Cada estrelinha é uma característica melhorável das tropas; estrelas maiores são marcos (por exemplo, depois de três estrelas, a maior dá +5% de vida a toda a tropa; outra ramificação dá escudo adicional à infantaria). Constelações temáticas: Órion (cavalaria), Hércules (infantaria) e Ártemis (arqueiros). Redistribuição gratuita, só fora das fases, numa área específica de redistribuição de estrelas na seleção de fases (muda a v0.8, que dizia "área de melhorias", para não confundir com a aba Melhorias do castelo). Três presets de estrelas, salvos pelo jogador e aplicados com um toque; por enquanto, os presets salvam só as estrelas. O preset é escolhido para aquela combinação de deus e herói (novo na v0.9, seção 3.4). Objetivo: builds que combinam herói, deus, melhorias e forma de jogo conforme o mapa.
- **Diamantes:** comprados fora ou ganhos jogando, por drop de abate com chance percentual (Pendente) e por recompensa de vitória. Os dropados na partida só são recebidos se o jogador vencer (por exemplo, cerca de 200 numa partida). Comprar acelera, mas quem não paga consegue tudo jogando.
- **Derrota** (novo na v0.9): sem estrela, mas o jogador recebe um mínimo de diamantes proporcional às ondas vencidas. Essa consolação é separada dos diamantes dropados, que continuam só na vitória. Sair no meio conta como derrota.
- Exemplos de compra com diamantes: bênção que dobra os favores no início da partida; três vidas extras para o castelo (sobrevida, não vitória garantida). Esses consumíveis valem para uma partida, não são poder permanente (novo na v0.9).
- Monetização (passe de batalha, bolsa, vídeos opcionais): fora do MVP, tudo ainda proposta.

### 14.1 Progressão e reforço (ideias de 23/11/2026)

Três ideias aprovadas na direção geral e fora do MVP. Os detalhes, os números e as regras de compra (sem pay-to-win) ficam para depois.

- **Melhorias com estrelas.** Numa tela de melhorias, no estilo do Kingdom Rush, o jogador gasta as estrelas das fases. Haverá uma árvore de melhoria geral para as tropas, e não uma coluna por tipo, porque virão tropas novas, como o lanceiro. Também haverá melhorias gerais, por exemplo de economia. Os exemplos de números são só ilustrativos.
- **Tropa extra (mercenários ou patrulha).** Um botão na HUD chama, de tempos em tempos, uma tropa extra no mapa, como respiro em situação crítica sem recurso. Decidido em 23/11/2026: a tropa é fixa. As mudanças e variações dela ficam nas estrelas, como opção do jogador na área externa. Ela deve ser mais fraca e mais curta que uma tropa produzida, para não substituir a produção no castelo.
- **Nível do jogador.** É um XP geral, ganho a partir das estrelas conquistadas. O nível libera conteúdo no jogo como um todo, nunca poder dentro da fase. Por exemplo, liberar um deus exige um nível mínimo (como 15) e os cards necessários, obtidos em desafios.
- **Papel de cada camada:** o herói evolui por XP, as tropas evoluem com estrelas e o jogador libera conteúdo pelo nível.

### 14.2 Enredo: a defesa de Troia (esboço de 23/11/2026, a detalhar)

O jogador defende o reino de Troia. Cada fase é o ataque grego a um reino vassalo de Príamo, não ao castelo principal. Cada reino tem um deus de adoração ligado a ele, mas o jogador pode escolher outros deuses. O foco é nos deuses mais conhecidos.

- **Introdução animada (primeira abertura do app):** Páris leva Helena para Troia, a frota de Agamenon chega e Príamo convoca os reis aliados.
- **Cutscene antes de cada fase:** complementa a história e apresenta o que vai acontecer na fase.

| Região | Rei | Deus ligado | Chefe | Ideia |
| --- | --- | --- | --- | --- |
| Lícia | Sarpédon | Apolo; Thanatos aparece na história | Pátroclo | Primeira região; justifica Thanatos no MVP |
| Dardânia | Eneias | Afrodite | Diomedes |  |
| Trácia | Reso | Ares | Odisseu e Diomedes | Fase noturna |
| Amazonas | Pentesileia | Ares e Ártemis | Aquiles (1ª aparição) |  |
| Costa de Troia | Príamo | Zeus e Apolo | Ajax |  |
| Troia | Príamo e Heitor | Apolo | Aquiles | Final com o Cavalo de Troia: rota nova que se abre por dentro |

- **Chefes:** são heróis gregos, não monstros. O ciclope fica de fora ou vira evento especial.
- **Modo guiado (ideia):** ao começar, o jogo pergunta se o jogador quer seguir o enredo. Se sim, sugere ou seleciona o deus e o herói indicados para cada fase e apresenta deuses novos aos poucos. Se não, o jogador escolhe livremente.
- **Justificativa narrativa da escolha livre:** o deus favorece o herói escolhido. Exemplo: Hércules, filho de Zeus, justifica a proteção de Zeus.
- **A reavaliar:** presets de deus e herói, e evolução geral dos heróis pelo nível do jogador em vez de herói a herói, para não prejudicar quem troca.

## 15. Teste

- Testadores: John, o colega e poucas pessoas próximas (novo na v0.9, seção 2.6).
- Testadora prevista: a esposa do John, que conhece bem a franquia Kingdom Rush.
- Riscos a observar no teste:
  - A capacidade de bloqueio por unidade deixa passar inimigos demais ou de menos?
  - A renda por tempo supera o ganho por abate e recompensa esperar?
  - A torre é opcional demais ou domina a defesa? Algumas ondas devem ser difíceis só com tropa.
  - A trava da torre no primeiro alvo frustra quando um inimigo forte vem na frente?
  - O herói com movimento livre resolve demais sozinho?
  - A cavalaria morre sozinha antes da tropa chegar, e o jogador entende isso pela tela?
  - A faixa de três estrelas (perder no máximo 3 vidas) é estreita demais?
  - A pausa tática dá vantagem demais?
  - A conta de tempo fecha (dez ondas com espera de 1 a 1,5 minuto ocupam quase a fase toda)?
- Riscos já levantados (novo na v0.9):
  - Formação sem efeito no combate vira microgestão.
  - Todos compram a cavalaria pesada primeiro.
  - Herói farmando: alerta se ele fizer mais de 35% dos abates.
  - As três rotas cabem na tela vertical sem rolar demais?
  - A primeira torre vira sempre a mesma compra.

## 16. Pendências gerais

- Fórmula de dano e escala de status: decisão pendente; ver recomendação da pesquisa em 11.4 (muda a v0.8).
- Classificação dos inimigos por nível (comum, forte, chefe), junto com a seleção de inimigos do jogo todo.
- Tabelas de status, custos, economia e ondas.
- Custo e efeito de cada estrela das constelações.
- Reagrupamento só para as tropas do jogador (proposta).
- Benefícios específicos de cada era e nomes das eras.
- Vantagens dos outros deuses, Poderes Divinos e Unidades Mitológicas.
- Habilidades dos heróis.
- Chance de drop de diamantes.
- Regra de vantagem entre tropas e tipos de dano.
- Arquitetura online, antes de qualquer recurso de compra.
- História da campanha.

### 16.1 Dúvidas levantadas na compilação da v0.9 (a tratar depois)

- **Online no MVP:** o jogo é online obrigatório (2.5), mas a arquitetura online fica para depois do MVP (2.3). O MVP roda offline?
- **Tela de preparação no MVP:** traz deus, herói e preset de estrelas, mas o MVP tem um deus, um herói e não gasta estrelas. A tela entra no MVP?
- **Presets e composições:** os presets por faixa de recurso (MVP, 5.1) e as composições montadas fora da partida (depois do MVP, 2.3) são a mesma coisa?
- **Número de evoluções por linha:** com três eras e uma evolução por era, cada linha tem duas ou três evoluções? (afeta "comprar as três de uma vez", 5.5)
- **Evolução de torre e era:** a seção 8 diz que cada era libera evoluções de torre; a 9 diz que a primeira não exige era nova.
- **Tropa sem destino:** a 5.2 diz que ela fica parada no portão; a bandeira (5.1) manda toda tropa nova para o ponto de encontro. Qual vale, e quando?
- **Hércules:** é a constelação da infantaria (14) e também o herói do exemplo "Zeus e Hércules" (3.4).
- **Reagrupamento:** a 5.4 ainda o trata como proposta, mas a regra de troca de alvo (11.1) já define que o jogador concentra depois de bloquear todos os inimigos livres.
- **Raio de interceptação:** aparece só ao selecionar a tropa, ou também ao movê-la, como dizia a v0.6?

Vindas da v0.6 e não levadas antes (novo na v0.9):

- Limite de tropas por base de torre.
- Reforço, união ou edição de tropas incompletas.
- Se o jogador pode dar todos os comandos durante a espera entre ondas.
- Onde fica salvo o progresso do jogador.
- Defesa própria do castelo.
- Efeito mecânico de cada formação.
- Regras da bandeira: existe desde o início? Pode ser removida? O que acontece se ficar fora do território?

Saiu desta lista na v0.9: presets de tropa por faixa de recurso (entram no MVP, seção 5.1).

## 17. Mudanças em relação à v0.8

### 17.1 Principais mudanças da v0.9 (19/11/2026)

| Tema | v0.8 | v0.9 |
| --- | --- | --- |
| Regras de combate da v0.6 (17.2) | Não tinham entrado | Acerto garantido, projéteis, ponto de defesa, interceptação, movimento no combate e sobreposição de raios (11.5 a 11.7) |
| Arqueiro do jogador | Sem regra de bloqueio | Bloqueia 0; só bloqueia se for alcançado, sem penalidade (5.4) |
| Arqueiro inimigo | Só para quando bloqueado | Para para atacar quando tem alvo no alcance e depois retoma a rota (11.1) |
| Estabilidade de alvo | Fica no alvo até um morrer | Bloqueador fica; excedente troca para bloquear inimigo livre; exceção da perseguição (11.1) |
| Perseguição ao arqueiro | "Meio raio" (9) e "metade do alcance" (11.3) | Uma só medida: cerca de metade do alcance do inimigo além da zona (9, 11.3) |
| Presets de tropa por faixa | Em discussão | Entram no MVP (2.2, 5.1) |
| Herói no MVP | Sem habilidades ativas | Sem nenhuma habilidade (2.2, 6) |
| Derrota | Sem regra de recompensa | Sem estrela; mínimo de diamantes proporcional às ondas vencidas (14) |
| Fim de fase | Vitória e número de ondas pendentes na 2.4 | Zero vidas acaba na hora; vitória com a morte do último inimigo da última onda (3.5) |
| Evolução | Sem regra de recompra | Só se compra a versão nova, pelo mesmo preço; última era permite comprar as três de uma vez; card também para torres (5.5, 9) |
| Fórmula de dano | Pesquisa a fazer | Pesquisa feita, recomendação registrada; decisão pendente (11.4) |
| Produção e plataforma | Sem seção | Nova seção 2.6; som e música fora do MVP; critério de sucesso do MVP (2.1) |
| Tela de preparação | "Três toques" | Poucos toques para quem aceita os padrões; preset de estrelas por combinação deus e herói (3.4) |
| Interface | Sem ação da bandeira nem telas fora da partida | Estandarte no painel do castelo; telas de preparação e de constelações (13) |
| Pendências | Sem as da v0.6 | Sete pendências da v0.6 acrescentadas; decididas saíram (2.4, 16) |

**Mudanças de 23/11/2026:**

- Seção 11.8: respostas à avaliação v0.9 (bloqueio por toda a tropa, herança do bloqueio, inimigo busca arqueiros próximos, trava da torre, renda a partir da onda 1, antecipação, era sem efeito imediato, destino no botão do preset, ponto duplo e critério de validação do MVP). Os textos antigos das seções 4, 8, 9, 11.1 e 11.6 foram corrigidos.
- Seção 14.1: melhorias com estrelas, tropa extra fixa e nível do jogador (fora do MVP).
- Seções 4.1 e 5.4: cavalaria a 110 de Comida, com bloqueio duplo só na última evolução.
- Seção 4.1: abate do inimigo fraco, ondas de farm e orçamento de pontos por onda.

### 17.2 Histórico: correções da v0.8

| Contradição na v0.7 | Como ficou na v0.8 |
| --- | --- |
| Combate em bloco (11.1) x bloqueio por unidade (5.4) | Combate em bloco eliminado; vale o bloqueio por unidade |
| Faixas de estrelas sobrepostas em 30% e 90% | Faixas por vidas inteiras: 20 a 17, 16 a 10, 9 a 1 |
| Hades com 20%, abaixo de Thanatos com 25% | Hades sem definição; Thanatos é o deus do MVP com 25% |
| Dica 4 do tutorial x dois toques do sinalizador | Dica ajustada para os dois toques rápidos |
| Torre teria perdido a função de território | Erro da avaliação: o raio da torre continua sendo território |
| Confirmar e enviar em discussão | Tropa vai ao portão ou à bandeira de ponto de encontro |

## 18. Documentos de apoio

- [GDD v0.8 (versão anterior)](https://claude.ai/artifact/MMHF1dt5y9DdxvaAtsiRGj)
- [GDD Tower Defense Mitológico v0.6](https://claude.ai/code/artifact/a4bc37d1-8b57-4586-ab67-1fbca51e5826) (inclui a seção 17, fonte das regras de combate desta versão)
- [Pesquisa: fórmulas de combate e levantamento de Age of Mythology](https://claude.ai/code/artifact/0505d188-cc73-4081-a2d2-8f2e7c51c84c)
- [Avaliação Tower Defense Tactics v0.6 - 18/11/2026](https://claude.ai/code/artifact/2ef24a5a-3ec7-497e-9819-0789a859831d)
- [Compilado de riscos e decisões (18/11/2026)](https://claude.ai/code/artifact/770159b5-0db5-40ee-adde-b03a70edf93b)
- [Avaliação Tower Defense Tactics v0.7 - 19/11/2026](https://claude.ai/artifact/UFh1o1MW44zf6wTBFXfXVZ)
- [Tower Defense Tactics: decisões de 19/11/2026](https://claude.ai/artifact/LTYMurYdVCgdrJ3pGFz1bo)
