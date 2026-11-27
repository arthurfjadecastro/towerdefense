# GDD · Tower Defense Tactics · v0.10

Nov 26, 2026 · @John

Documento único com as definições do jogo até 26/11/2026. Itens marcados como **Pendente** ainda não foram decididos; valores marcados como **ponto de partida** serão ajustados no teste.

## 1. Visão do jogo

Jogo mobile vertical de tower defense tático com tema mitológico. O castelo é o centro: o jogador produz tropas, evolui o castelo por três eras, constrói torres e usa heróis e deuses para barrar ondas de inimigos que avançam por rotas até o castelo.

**Diferencial em relação ao Kingdom Rush:** lá a torre de quartel repõe unidades sozinha; aqui o jogador produz as tropas no castelo, por ação própria, sem reposição automática.

**Pilares de design**

- **Simples, mas exige pensar:** cada decisão em um lado (tropa, torre, castelo) custa no outro, e o jogador precisa pensar para não errar.
- **Clareza:** o jogador sempre vê o que vem pela frente (próxima onda, tipos de inimigo, alcance) antes de decidir.
- **Progressão que ajuda, mas não decide:** a tática vence a partida; melhorias permanentes são um extra.
- **Identidade visual:** o castelo muda de aparência conforme a era e o deus escolhido.

**Nem simples, nem complexo:** o jogo tem profundidade, mas a revela aos poucos. Cada sistema aparece só quando o jogador precisa dele (seção 13.2), e assim o jogo sempre traz a sensação de algo novo sem parecer complicado.

**Enredo:** o Capítulo 1 é a Guerra de Troia vista pelo lado troiano. Capítulos futuros trazem outras mitologias (por exemplo, egípcia e nórdica), cada um com campanha, heróis, deuses e inimigos próprios (seção 14).

**A campanha é o foco.** O enredo com clímax é o que faz o jogador querer terminar a campanha, em vez de baixar, jogar um pouco e apagar. O ponto de partida é forte: Agamenon usa o rapto de Helena como pretexto para atacar Troia e tomar suas riquezas, e o jogador, do lado troiano, decide como essa história termina.

**Referências:** Kingdom Rush (clareza de rotas e torres, chamada antecipada de ondas, estrelas e desafios), Age of Mythology (deuses, unidades míticas, eras) e árvores de evolução no estilo Path of Exile.

**Visão de longo prazo:** o núcleo é fixo e o conteúdo cresce em dados (seção 17). Novos capítulos, fases, heróis e deuses entram por atualização, sem refazer o jogo.

## 2. Escopo do MVP

O MVP testa o núcleo: movimentação, disposição do mapa e das torres, funcionamento do castelo e, principalmente, a produção de tropas. O balanceamento fino fica para depois. Regra de escopo: nada novo entra no MVP sem critério de validação próprio.

### 2.1 Três partes

1. Combate, economia e torre.
2. Eras e evoluções.
3. Herói e Favor Divino.

### 2.2 O que entra

- **Fase:** a praia de Troia, com cerca de 15 minutos, 10 ondas e 3 rotas. As ondas não usam necessariamente as três rotas ao mesmo tempo.
- **Inimigos:** só fracos, com níveis (o mesmo inimigo fica mais resistente nas ondas finais). Espelham infantaria, arqueiro e cavalaria. Cada um tira 1 vida do castelo.
- **Castelo:** três eras (nomes provisórios), pagas com Ouro.
- **Tropas:** infantaria, cavalaria e arqueiros, com evoluções fixas (sem a ramificação final). Tropas de 2 a 10 unidades, controle coletivo, bloco único, botão Repetir última tropa e presets por faixa de recurso.
- **Herói:** Heitor, sem nenhuma habilidade (nem ativa nem passiva), respawn de 60 segundos pago com Favor.
- **Deus:** nenhum. O retorno de Comida por unidade morta fica no padrão de 15%.
- **Torre:** um tipo, com 2 flechas por disparo, em pontos fixos.
- **Economia:** Comida, Ouro e Favor (seção 4).
- **Partida:** sinalizador, antecipação de onda, pausa de menu, pausa tática e aceleração 2x.
- **Tutorial:** dicas dentro da própria fase, explicando sinalizador, tropas, posicionamento e movimentação.
- **Estrelas:** calculadas pelas vidas do castelo.
- **Conexão:** offline.

### 2.3 O que fica fora

Deuses, Poder Divino e Unidade Mitológica; habilidades de herói e segundo herói; inimigos fortes, elites e chefes; ramificações finais de tropa e torre; tipos de dano e vantagem entre tropas; formação e postura; tropa extra (mercenários); campanha, mapa de campanha, fases livres e secundárias; tela de preparação; gasto de estrelas e tela de Melhorias; XP de herói; diamantes, loja e monetização; filme e cutscenes; arquitetura online; som e música.

### 2.4 Pendências que bloqueiam o MVP

- Tabela de status de tropas, herói, torre e inimigos (a fórmula de dano já está definida, seção 11.6).
- Lista das 10 ondas: quantidade, nível e rota de cada inimigo.
- Regras de mapa: tamanho dos raios, posição dos pontos de torre, comprimento das rotas.
- Dano e alcance da torre.
- Tempo de espera entre ondas.
- Interface mínima: painel do castelo, cartas, HUD, sinalizador e pausas.
- Bandeira de ponto de encontro: posição inicial e área de toque.

### 2.5 Critério de sucesso

O núcleo passa se a testadora pedir para jogar de novo sem sugestão, souber explicar por que perdeu e achar que repor tropas é uma decisão, não uma tarefa cansativa. Se dois desses sinais falharem, o núcleo muda antes de seguir.

### 2.6 Produção e plataforma

- **Equipe:** John e Arthur, usando IA e o Claude Code. Sem prazo fixo, com prioridade para a qualidade.
- **Motor:** Godot.
- **Plataforma:** celular e tablet; só Android no início, iOS depois.
- **Conexão:** offline até o lançamento; online obrigatório em produção. Se a conexão cair, o jogo pausa e oferece continuar.
- **Arte:** há algumas artes; o estilo final não está fechado.
- **Construção do combate em duas etapas:** primeiro uma versão mínima (um bloqueio por inimigo), depois a completa, com redistribuição e sobreposição de raios.

## 3. Estrutura da partida

1. O jogador escolhe a fase no mapa e, na tela de preparação, o deus, o herói e o preset de melhorias.
2. A fase começa com castelo simples, saldo inicial e portão voltado para a zona de combate.
3. A primeira onda não tem contagem: o jogador a inicia pelo sinalizador. As seguintes começam sozinhas depois de um tempo de espera.
4. O jogador produz tropas, constrói torres, move tropas e heróis e evolui o castelo.
5. A fase termina com vitória ou derrota, e as vidas restantes definem as estrelas.

### 3.1 Sinalizador e antecipação

Antes de cada onda, um sinalizador na base da rota mostra o ponto de início e o caminho. O jogador só vê a próxima onda.

- **Um toque** abre um painel com os inimigos da onda e o botão "antecipar onda".
- **Toque duplo** também antecipa, direto. Se no teste houver antecipação sem querer, o toque duplo sai.
- Ao antecipar, o jogador recebe na hora a renda do tempo pulado (Comida, Ouro e Favor) mais um extra proporcional ao tempo antecipado (seção 4.3).
- Antecipar com inimigos vivos soma as duas ondas: é risco contra tempo.

### 3.2 Pausa e aceleração

- **Pausa de menu:** um menu cobre o mapa, sem comandos.
- **Pausa tática:** congela o jogo com o mapa visível; o jogador olha e seleciona, mas não dá ordens.
- **Aceleração:** até 2x, acelerando tudo, inclusive a contagem da onda. Nunca é requisito para estrelas.

### 3.3 Tela de preparação

Ao selecionar a fase, o jogador vê as informações dela (características e inimigos, alguns ocultos por interrogações) e escolhe deus, herói e preset de melhorias em carrosséis. A tela abre com o padrão definido pelo jogador ou com a última escolha. Nas fases de campanha, as escolhas seguem as regras da seção 14.

### 3.4 Fim de fase e vidas

- **Vitória:** quando morre o último inimigo da última onda.
- **Derrota:** quando as vidas chegam a zero, ou na hora em que um chefe chega ao castelo, mesmo com vidas sobrando. A onda do chefe é avisada antes. Sair no meio da fase conta como derrota.
- **Vidas:** o castelo tem 20. Ao chegar, o inimigo tira vidas e some: comum 1, forte 2, elite 3 (valores de exemplo).
- **Estrelas:** de 20 a 17 vidas, três; de 16 a 10, duas; de 9 a 1, uma. Nas fases com desafio, há uma quarta estrela (seção 14.5).
- **Feedback:** vidas como corações; o castelo se deteriora visualmente (por exemplo, pegando fogo).
- **Tela de resultado:** estrelas, recompensas e, quando houver, o card de novo herói ou deus disponível.
- **Exceção:** no duelo entre Heitor e Aquiles, perder não encerra a campanha; abre outro caminho (seção 14.3).

## 4. Economia

Três recursos dentro da partida, que zeram ao fim da fase.

| Recurso | De onde vem | Para que serve |
| --- | --- | --- |
| Comida | Renda por tempo, abates, retorno por unidade morta | Comprar tropas |
| Ouro | Renda por tempo, abates | Torres, eras, evoluções de tropa e de torre |
| Favor Divino | Renda por tempo (no MVP); abates e outros usos depois | Reviver o herói; Poder Divino e bônus temporários depois |

### 4.1 Custos e saldo inicial (ponto de partida)

| Item | Custo |
| --- | --- |
| Arqueiro (por unidade) | 50 de Comida |
| Infantaria (por unidade) | 70 de Comida |
| Cavalaria (por unidade) | 110 de Comida |
| Construir torre | 300 de Ouro |
| Castelo para a 2ª era | 500 de Ouro |
| Castelo para a 3ª era | 800 de Ouro |
| Saldo inicial | 1.000 de Ouro e 1.000 de Comida |

O custo da tropa é a soma das unidades. O saldo inicial, o número de torres e o de rotas variam por fase; os valores acima servem para o primeiro teste (outro exemplo: 500 de Ouro).

### 4.2 Abate e renda

- **Inimigo fraco:** 15 a 20 de Comida e 8 a 10 de Ouro. O Ouro é baixo de propósito, para ser disputado entre torre, era e evolução.
- **Inimigo forte:** 3 vezes o fraco (45 a 60 de Comida, 24 a 30 de Ouro). Elites e chefes dão recompensa maior (valores pendentes).
- O ganho por abate cresce conforme a onda.
- **Renda por tempo:** 1 de Comida e 1 de Ouro por segundo, a partir do momento em que o jogador chama a primeira onda.

### 4.3 Antecipação

Ao antecipar, o jogador recebe na hora a renda do tempo pulado (inclusive o Favor) mais um extra de até 10% do que a onda rende em abates. O extra é proporcional ao tempo antecipado: máximo logo que a onda aparece, que é mais difícil, e perto de zero no fim da espera.

### 4.4 Retorno por unidade morta

Cada unidade que morre devolve 15% do seu custo em Comida, por unidade, na hora. Alguns deuses mudam esse percentual (por exemplo, Thanatos devolve 25%). O custo das tropas é o mesmo para todos os deuses.

### 4.5 Favor Divino

- **No MVP:** rende 1 a cada 2 segundos, só por tempo. Reviver o herói custa cerca de 150 de Favor (ponto de partida); o Favor inicial fica perto disso, cerca de 100, para a primeira morte não demorar muito a ser paga.
- **No jogo completo (ideia registrada):** 1 por segundo mais 50% do Ouro de cada abate, com outros usos além de reviver, como bônus temporários (exemplo: +10% de ataque e defesa por 3 ondas). Os usos e os valores serão definidos depois.

### 4.6 Regras gerais

- Terminar a fase com recurso sobrando não é problema: é resultado de boa estratégia.
- Perder recurso por estratégia errada é decisão do jogador.
- Evoluções de tropa e de torre têm custos próprios (seções 5.7 e 9).

## 5. Tropas

**Unidade** é o combatente individual. **Tropa** é o agrupamento que o jogador monta e comanda. Três linhas, todas disponíveis desde o início: infantaria (hoplitas), cavalaria e arqueiros. Cada tropa tem de 2 a 10 unidades, e tropa mista é permitida.

### 5.1 Montagem e compra

- O jogador escolhe unidades nas cartas e monta a tropa. Durante a montagem o saldo não muda: a tela mostra o custo acumulado, abatido só ao confirmar.
- Uma carta fica vermelha quando o saldo não cobre o acumulado mais ela. O botão Confirmar só habilita com 2 unidades (máximo 10).
- A compra é instantânea: ao confirmar, a tropa sai do castelo e vai para a bandeira.
- **Repetir última tropa:** um botão recompra a última composição.
- **Presets por faixa de recurso:** o jogador salva composições para pouco, médio e muito recurso. Na partida: castelo, preset, confirmar. O botão mostra o destino, por exemplo "Enviar para a rota A".
- **Sem reforço:** uma tropa incompleta não é completada; o jogador produz outra.
- **Sem teto de tropas no mapa:** a Comida é o limite natural.

### 5.2 Bandeira de ponto de encontro

Há uma única bandeira (o estandarte), definida no painel do castelo e visível no mapa. Tudo o que for produzido vai para ela. Bandeira esquecida numa rota calma é erro de estratégia do jogador, sem aviso automático.

### 5.3 Comando e movimento

- Tocar na tropa e depois no mapa mostra o caminho e a move.
- **Controle coletivo:** não há movimento individual enquanto a tropa tiver 2 ou mais unidades.
- **Área de movimento:** a tropa pode ir a qualquer ponto das rotas e ao raio do castelo. Ficar perto de uma torre é vantagem, não regra.
- **Ponto de defesa:** o lugar para onde o jogador mandou a tropa. Depois de cada combate, ela volta para lá.
- **No caminho:** se a tropa enviada encontra um inimigo no trajeto, ela para e luta; se vencer, segue até o destino.
- **No MVP, a tropa anda em bloco único.** Formações e postura ficam para depois (seção 20).

### 5.4 Posição e identificação

- **Sem sobreposição:** se já há uma tropa no ponto, a próxima fica ao lado, acima ou abaixo, em fileiras. Cada tropa tem área de toque própria e continua bloqueando mesmo deslocada para o lado.
- **Porta-estandarte:** cada tropa tem um membro com uma bandeira que mostra o emblema do tipo, sempre visível. Isso garante a leitura também para quem tem daltonismo.
- **Cores:** a cor-base indica o tipo (cavalaria vermelho, arqueiros verde, infantaria laranja, mista com tom próprio), e cada tropa recebe um tom único enquanto estiver no mapa. A forma final depende da arte.

### 5.5 Papéis

| Linha | Papel | Característica |
| --- | --- | --- |
| Infantaria | Linha de frente | Barata, bloqueia o avanço e aguenta dano. Fica decisiva com as evoluções |
| Cavalaria | Reação rápida | Mais cara, mais vida, um pouco mais de status e maior velocidade |
| Arqueiros | Dano à distância | Baratos e frágeis, raio maior que o corpo a corpo, ficam atrás |

No MVP, as unidades se comparam só por status (vida, ataque, defesa). Tipos de dano e vantagem entre tropas ficam para depois.

### 5.6 Capacidade de bloqueio

O inimigo excedente segue a rota.

| Unidade | Bloqueia |
| --- | --- |
| Infantaria | 1; passa a 2 na última evolução |
| Cavalaria | 1; passa a 2 na última evolução |
| Arqueiro | 0; só bloqueia se for alcançado, mantendo ataque e intervalo. A penalidade é morrer rápido |
| Herói | 2; 3 como possível evolução ou item |

### 5.7 Evolução de tropas

Cada linha tem três evoluções, compradas com Ouro e em sequência:

| Evolução | Exige | Cavalaria | Infantaria | Arqueiro |
| --- | --- | --- | --- | --- |
| 1ª | 2ª era | 200 | 130 | 90 |
| 2ª (a última do MVP) | 3ª era | 350 | 220 | 160 |
| 3ª: ramificação em dois caminhos | Depois do MVP | Pendente | Pendente | Pendente |

- Os custos são proporcionais ao preço de cada tropa, com a cavalaria como base. O arqueiro barato em massa é compensado pelas fragilidades dele.
- A evolução vale para todas as unidades da linha, as que já estão em campo e as futuras.
- **A unidade evoluída custa mais Comida:** +20% a cada evolução, acumulado (exemplo: infantaria 70, 84 e cerca de 101).
- Um toque na evolução mostra um card com ganhos de status, mudança visual e custo. Evoluções bloqueadas aparecem esmaecidas, com a era exigida.
- A ramificação final oferece duas opções com uma vantagem cada (característica, não habilidade ativa). A escolha é definitiva.

## 6. Heróis

- Unidade única, com status superiores aos das tropas. Não é imortal.
- **Movimento livre:** circula por todas as rotas e lugares, inclusive na ponta da rota.
- **Bloqueia os 2 primeiros inimigos** que encontrar, sem distinguir tipo. Bloquear 3 fica como possível evolução ou item.
- **Respawn:** ao morrer, espera de 60 segundos; depois o jogador paga Favor para ele voltar, sempre no portão. O custo é alto de propósito, para o herói ser usado com estratégia e não sacrificado.
- **Retrato no HUD:** cada herói em campo tem um retrato, como no Kingdom Rush. O toque seleciona, e o retrato mostra a vida e o tempo de volta. As habilidades ficam ao lado do retrato.
- No início da partida, herói e torre fazem o farm inicial de recurso.
- **Diferentes, não melhores:** heróis desbloqueáveis mudam o estilo, não a força.

### 6.1 Habilidades (depois do MVP)

Cada herói começa com uma habilidade própria e libera outras ao subir de nível: no máximo duas ou três ativas, as demais passivas. Exemplo: Heitor tem o brado da vitória, que dá bônus temporário de ataque e defesa às tropas próximas.

Recuperação de vida (depois do MVP): o herói recupera vida aos poucos, coisa que as tropas não fazem. O jogador pode recuá-lo para perto do castelo para curar, ficando sem ele na luta.

### 6.2 Progressão

- Até 10 níveis, por XP ganho nas partidas em que participou, com barra própria fora da partida. O XP depende da dificuldade da fase.
- Repetir fases para ganhar XP é opção do jogador, com ganho limitado.
- A dificuldade das fases segue a campanha, não o nível do herói: experimentar um herói novo não é punido.

### 6.3 Heróis no Capítulo 1

- **Jogáveis:** heróis troianos (Heitor, Eneias, Páris, Sarpédon, Pentesileia, Mêmnon). O jogo começa com Heitor.
- **Gregos:** são chefes da campanha (Aquiles, Ajax, Odisseu, Diomedes, Agamenon). Depois das batalhas contra eles, podem ser desbloqueados e usados fora da campanha.
- **Desbloqueio:** um herói troiano aparece como coadjuvante numa fase da campanha; depois dessa fase, fica disponível para desbloqueio (seção 15.4).

## 7. Deuses

- O jogador escolhe um deus antes da fase. O deus dá vantagens numa camada diferente da do herói: economia, custo e bônus de linhas de tropa. Exemplo de vantagem: Thanatos devolve 25% da Comida das unidades mortas.
- **Diferentes, não melhores.** Alguns deuses ajudam em certas fases (por exemplo, inimigos de fogo pedem um deus com proteção contra incêndio), mas outros também vencem.
- Cada deus muda a aparência do castelo (bandeiras, elementos visuais, uma estátua).
- Cada deus terá vantagens e um Poder Divino.
- **Deus da última era:** ao chegar à última era, o jogador escolhe um deus, que pode ser diferente do principal, e ele concede uma Unidade Mitológica, que se move como o herói e usa poderes próprios sem comando. Risco: isso ajuda mais quem já está ganhando.
- **No Capítulo 1:** os deuses seguem a campanha, com foco nos mais conhecidos do lado de Troia (Apolo, Afrodite, Ares, Ártemis). Os deuses iniciais estão **Pendentes**.
- **Desbloqueio:** como o herói, o deus aparece como sugerido numa fase da campanha; depois de passar dela, fica disponível para desbloqueio, com um card de "novo deus" na tela de resultado.
- **MVP:** sem deus.

## 8. Castelo e eras

- O castelo é o centro funcional: produz tropas e evolui. As tropas podem ficar dentro do raio dele.
- **Três eras**, com nomes provisórios (Pendente). A evolução usa Ouro e leva cerca de 5 segundos, com o castelo crescendo na tela; durante a obra ele funciona normalmente.
- **A era só libera evoluções** de tropa e de torre. A compra não muda nada imediato na batalha, e as tropas mantêm seus status até a evolução ser comprada.
- **Era como resgate:** quem sente as tropas morrendo e guardou recurso pode evoluir de era para liberar evoluções. É escolha de quem economizou, não ajuda automática.
- Sem teto de unidades por era: o limite é o recurso.
- Evoluções do castelo mostram um card com ganhos, mudança visual e custo antes da compra.

## 9. Torres

- Construídas só em pontos fixos ao longo das rotas, cerca de 3 a 4 por fase (varia por fase). Custam 300 de Ouro.
- Pode-se construir num ponto de rota ainda fechada, como risco de decisão.
- **Torre x arqueiros:** a torre não exige recompra e ataca mais rápido.
- **Disparo:** várias flechas em sequência; a torre do MVP começa com 2 flechas por disparo.
- **Trava de alvo:** a torre fica no primeiro inimigo que entra no raio até ele morrer, mesmo que esteja bloqueado. Se ele sair vivo do raio, a torre passa ao inimigo mais próximo dentro do raio. Com inimigos de rotas diferentes, ataca sempre o primeiro, o que cria o dilema de qual rota defender.
- Inimigos comuns não destroem torres. Só inimigos específicos, como um chefe, poderão destruí-las ou desabilitá-las por um tempo.
- **Um tipo de torre**, que evolui assim:

| Evolução | Custo (ponto de partida) | Exige | Efeito |
| --- | --- | --- | --- |
| 1ª | 150 de Ouro | Nenhuma era | Mais raio e mais ataque |
| 2ª | 300 de Ouro | 2ª era | Pendente |
| Ramificação em dois caminhos | Pendente | Última era, depois do MVP | Exemplo: flechas rápidas contra um alvo ou catapulta com dano em área |

Cada evolução mostra um card com ganhos, mudança visual e custo. Novos tipos de torre ficam para pacotes de expansão (seção 20).

## 10. Mapa e rotas

- Tela vertical, câmera elevada, castelo completo na base, portão voltado para a zona de combate. Sem ataques pela retaguarda.
- O raio do castelo recebe várias entradas de rota. Os finais de rota são espaçados, e o inimigo chegar ao fim da rota deve ser de fato um problema.
- O MVP tem 3 rotas; nas outras fases, o número de rotas varia. As ondas podem chegar por rotas diferentes em momentos diferentes.
- **Ponto de torre duplo:** o raio de uma torre pode atingir duas rotas, mas a base dela não é caminhável, e a tropa precisa contornar para ir de uma rota à outra.
- **Rota fechada:** aparece no mapa desde o início, com um portão ou escombros. Antes de abrir, o jogo mostra de onde os inimigos vão sair e quais são, como no Kingdom Rush.
- **Fase como template:** cada fase é um mapa-base mais uma configuração (rotas e pontos ativos, saldo, ondas, regras). Detalhes na seção 17.

## 11. Combate

O inimigo sempre segue a rota em direção ao castelo e só para quando algo do jogador o bloqueia ou quando um alvo entra no raio dele. O castelo é sempre o objetivo.

### 11.1 Raios

- Cada unidade, do jogador ou inimiga, tem um raio: um círculo em volta dela. Só entra em combate quando algo entra nesse raio.
- **Raio corpo a corpo:** igual para todas as unidades corpo a corpo (cerca de três diâmetros de uma infantaria, ponto de partida).
- **Raio do arqueiro:** maior, para fazer sentido o ataque à distância.
- **O raio enxerga; o terreno decide se dá para chegar.** A unidade só sai do lugar se o caminho a pé até o inimigo couber no raio; se não couber, só observa. Isso evita que uma tropa no ponto de torre duplo corra para a rota do outro lado.
- Ao selecionar a tropa, o jogo mostra o raio dela.

### 11.2 Início e fim do combate

- O combate começa quando os raios se cruzam e só termina quando uma das unidades morre ou quando o jogador dá uma ordem.
- Depois do combate, a tropa volta ao seu ponto de defesa.
- O inimigo que fica livre procura outra unidade dentro do raio dele; sem nenhuma, segue para o castelo.

### 11.3 Bloqueio

- **Todas as unidades corpo a corpo** da tropa podem sair para bloquear, não só a linha da frente.
- **Bloqueio garantido:** o inimigo nunca segue a rota se houver uma unidade do jogador por perto capaz de bloqueá-lo. Se um inimigo fica livre, uma unidade que estava ajudando sai para bloqueá-lo.
- **Herança do bloqueio:** quando o bloqueador morre, a unidade que ajudava a bater naquele inimigo assume o bloqueio na hora.
- **Troca do excedente:** uma unidade que ataca um alvo já bloqueado larga esse alvo para bloquear um inimigo livre ao alcance. Prioridade: primeiro bloquear todo inimigo livre possível, depois concentrar vários no mesmo alvo.
- Sem limite de unidades por área: o limite é o recurso.

### 11.4 Arqueiros

- **Arqueiro do jogador:** não avança para bloquear. Se um inimigo corpo a corpo o alcança, ele bloqueia mantendo ataque e intervalo.
- **Inimigo contra arqueiros do jogador:** o inimigo corpo a corpo ataca o arqueiro que entrar no raio dele. Se o arqueiro sair do raio ou morrer, o inimigo volta à rota.
- **Arqueiro inimigo:** quando tem um alvo no alcance, para de andar e ataca; quando o alvo morre ou sai do alcance, volta a seguir a rota. Só ataca unidades e heróis, nunca torre nem castelo.
- **Não há perseguição automática** ao arqueiro inimigo que atira de fora do raio: cabe ao jogador mover a tropa até ele. Por isso, a tela precisa deixar claro quando uma tropa está sendo atingida de longe.

### 11.5 Retirada e movimento durante o combate

- Mover a tropa durante o combate é permitido. A ordem interrompe os ataques, solta os inimigos bloqueados, e a tropa toda segue para o novo destino.
- O inimigo solto **ignora a tropa que está recuando** e segue para o castelo, a não ser que outra unidade entre no raio dele. Assim a retirada sempre funciona.
- Sem lentidão, ataque de oportunidade, custo ou recarga na retirada.
- **Intervalo de ataque:** é estado da unidade e continua contando durante o movimento e na troca de alvo. O ataque imediato só ocorre se o intervalo já tiver acabado, o que fecha a brecha da retirada gratuita.

### 11.6 Fórmula de dano

**Dano = ataque × 100 ÷ (100 + defesa).** Defesa 100 corta o dano pela metade, e a defesa nunca zera o dano. Cálculo em ponto flutuante, com arredondamento só na exibição, e dano mínimo 1.

Escala recomendada para a tabela de status (ponto de partida): defesa de 0 a 200; ataque por golpe de 10 a 100; vida de tropa de 100 a 600; inimigo comum de 50 a 400; chefe de 2.000 a 10.000. Evoluções de defesa de +10 a +25 e de ataque de +10% a +20% por nível.

### 11.7 Regras de ataque

- Todo ataque básico acerta. Sem precisão nem esquiva.
- Projéteis acompanham o alvo até o impacto e somem se ele morrer, sem buscar outro. Projéteis já disparados continuam quando a tropa recebe nova ordem.

## 12. Inimigos e ondas

| Nível | O que é | Vidas que tira | No MVP |
| --- | --- | --- | --- |
| Comum (fraco) | Inimigo básico | 1 | Sim, com níveis de resistência ao longo das ondas |
| Forte | Mais vida e dano | 2 (exemplo) | Não |
| Elite | Mais vida e dano; alerta visual na primeira aparição; recompensa maior. Criaturas mitológicas entram como elite | 3 (exemplo) | Não |
| Chefe | Mais vida e dano; onda avisada antes | Derrota imediata se chegar ao castelo | Não |

- Elites e chefes não têm regra própria de combate: são só mais fortes.
- No Capítulo 1, os inimigos são o exército grego, e os chefes são heróis gregos. Criaturas mitológicas podem vir dos deuses que apoiam os gregos.
- A cada onda sobem a dificuldade e a quantidade. A partir de certa onda aparecem inimigos melhorados, um sinal para evoluir, não um muro.
- Cada região tem inimigos próprios. Inimigos novos são apresentados e entram numa biblioteca consultável fora da partida.
- **Ondas por fase:** de 10 a 15, conforme a dificuldade; a fase do MVP tem 10, em cerca de 15 minutos.
- **Ondas 1 e 2 são de farm:** só inimigos fracos, poucos, para o jogador juntar recurso.
- **Orçamento por onda (proposta a validar):** o fraco vale 1 ponto e o forte 3; a onda n vale 10 + 3 × (n − 1) pontos (onda 1 = 10 pontos; onda 10 = 37).
- A fase pode alterar a ordem das ondas; os tipos de inimigo da fase não mudam.

## 13. Interface e tutorial

- **Painel do castelo:** tocar no castelo abre um painel inferior com as abas **Treinar** e **Evoluções**, e a ação de definir a bandeira. O campo continua parcialmente visível.
- **Treinar:** carrossel de cartas com arte, nome, função, status, custo e ação. Abaixo, a composição da tropa (por exemplo 6/10), o custo acumulado e os botões Limpar, Repetir última tropa e Confirmar. Os presets ficam no mesmo painel, com o destino no botão.
- **Evoluções:** eras do castelo e evoluções de tropa, com cards. A torre evolui tocando nela no mapa.
- **HUD:** recursos e onda no topo; vidas; ações na lateral; retratos dos heróis com vida, tempo de volta e habilidades.
- **Melhorias:** tela fora da partida onde o jogador gasta as estrelas (seção 15.1).

### 13.1 Tutorial

- **No MVP:** dicas dentro da própria fase, explicando o sinalizador, as tropas, o posicionamento e a movimentação.
- **No jogo:** a 1ª fase da campanha é guiada e curta, só com Heitor. Até o fim da 2ª onda o jogador já viu o jogo funcionando, com foco nas tropas. Elites e outros elementos aparecem nas fases seguintes.
- **Filme de introdução:** passa entre "Iniciar jogo" e o mapa da campanha.
- **Tutoriais escritos:** numa área do menu principal.

### 13.2 Introdução gradual dos sistemas

Cada sistema aparece só quando o jogador precisa dele. O jogo tem a mesma quantidade de coisas, mas nunca parece complexo de uma vez, e cada avanço traz algo novo. Exemplo de ordem (a detalhar):

1. **Primeiras fases:** Comida, Ouro, tropas, torre e estrelas.
2. **Logo depois:** o herói e o Favor.
3. **Mais adiante:** eras e evoluções, deuses, tela de Melhorias.
4. **Depois da primeira região:** cartas, fragmentos, diamantes e fases livres.

Cada sistema novo chega com uma apresentação curta na hora em que aparece.

## 14. Campanha e enredo

### 14.1 Capítulos

O jogo é organizado em capítulos, cada um com uma mitologia, uma campanha principal fiel a ela, heróis, deuses, inimigos e mapas próprios. O **Capítulo 1 é a Guerra de Troia**. Capítulos futuros (por exemplo, egípcio e nórdico) entram como expansões, por atualização. O nome "capítulo" evita confusão com as temporadas de um futuro passe de batalha.

### 14.2 Capítulo 1: a defesa de Troia

O jogador defende Troia pelo lado troiano. Cada fase é um ataque grego a um reino vassalo do rei Príamo, até a própria Troia. O jogador "escreve a história de Troia" com o seu desempenho.

- **Prólogo (filme de introdução):** Agamenon, rei de Micenas, usa o rapto de Helena, esposa de seu irmão Menelau, como pretexto para atacar Troia e tomar suas riquezas. A frota grega chega, e Príamo convoca os reis aliados.
- **Cutscene antes de cada fase:** complementa a história e apresenta o que vai acontecer.
- **Início:** a campanha começa na praia, com o desembarque grego, e segue pelas invasões aos reinos vassalos de Príamo.
- **Cronologia:** as fases seguem os marcos da guerra vistos pelo lado troiano (desembarque na praia, cidades aliadas, templo de Apolo Timbreu, duelos, ataque noturno à Trácia, incêndio dos navios, Lícia, rio Escamandro, reforços, cerco final). A ordem exata está **Pendente**.
- **Chefe final:** Agamenon, nos dois caminhos.

Esboço das regiões (a detalhar):

| Região | Rei | Deus ligado | Chefe |
| --- | --- | --- | --- |
| Praia de Troia | Heitor no comando | A definir | A definir |
| Dardânia | Eneias | Afrodite | Diomedes |
| Lícia | Sarpédon | Apolo (Thanatos aparece na história) | Pátroclo |
| Trácia | Reso | Ares | Odisseu e Diomedes (fase noturna) |
| Amazonas | Pentesileia | Ares e Ártemis | A definir |
| Troia | Príamo | Apolo e Zeus | Agamenon |

### 14.3 O duelo entre Heitor e Aquiles

É o ápice da campanha, a fase mais crítica, mas não o final. É jogado só com Heitor, sem coadjuvante. O resultado abre caminhos diferentes:

| Resultado | Desfecho |
| --- | --- |
| Perder a fase | Aquiles vence e Heitor morre |
| Vencer com 1 ou 2 estrelas | Os dois morrem |
| Vencer com 3 estrelas | O jogador escolhe se Heitor vive (e Aquiles morre) |

- Perder o duelo não encerra a campanha: abre outro roteiro. O jogador pode rejogar o duelo.
- Os caminhos mudam o meio da campanha (algumas fases, chefes, cutscenes e mapas) e se unificam no final, com o mesmo objetivo.
- Se Heitor morre na história, ele sai das fases seguintes daquele caminho. Fora da campanha, continua selecionável.

### 14.4 Heróis e deuses na campanha

- **Nas fases de campanha**, só podem ser escolhidos heróis troianos e deuses do lado de Troia. Aquiles nunca defende Troia na história.
- **Modo guiado:** a campanha sugere ou seleciona o deus e o herói de cada fase, apresentando deuses novos aos poucos. Quem segue a sugestão ganha um bônus de recompensa.
- **Coadjuvante:** só algumas fases específicas do roteiro trazem um segundo herói da história, controlável, ao lado do principal. Essas fases são balanceadas para dois heróis, como no Kingdom Rush Alliance. Depois de apresentado, o coadjuvante fica disponível para desbloqueio.
- **1ª fase:** só Heitor.
- **Herói repetido:** se o jogador escolhe como principal o coadjuvante da fase, Heitor entra como secundário.
- **Justificativa narrativa:** o deus escolhido favorece o herói do jogador.

### 14.5 Tipos de fase e estrelas

| Tipo | Escolha de herói e deus | Estrelas |
| --- | --- | --- |
| Fase de campanha | Segue a história | 3 |
| Fase de campanha já vencida com 3 estrelas | Livre, sem seguir o roteiro, inclusive heróis gregos desbloqueados | 4ª estrela, com um desafio adicional |
| Fase livre ou secundária | Livre desde o início | 3, mais a 4ª estrela com desafio extra |

- A 4ª estrela é um extra: a campanha sozinha basta para o jogador ficar forte.
- **Fases secundárias:** liberadas uma ou duas a cada avanço na campanha. Dão o mesmo que a campanha, com bônus reduzido.
- **Depois da campanha:** o jogo continua com missões e fases novas por atualização, reaproveitando mapas com rotas, regras e desafios diferentes (exemplo: vencer sem torres).

### 14.6 Mapa da campanha

O mapa reflete Troia e mostra as fases de campanha com uma marcação própria, ao lado das fases livres e secundárias, como missões principais e secundárias em Skyrim. Cada fase tem nível de dificuldade e é balanceada individualmente.

## 15. Progressão

Cada camada evolui por um caminho: o herói por XP, as tropas por estrelas e o jogador libera conteúdo pelo nível. Nenhuma delas é obrigatória para vencer: a tática decide.

### 15.1 Estrelas e Melhorias

- Estrelas só se ganham jogando, nunca com diamantes. A recompensa por estrela é paga uma vez; ao melhorar o resultado, só a diferença.
- O jogador gasta as estrelas na tela **Melhorias**, no estilo do Kingdom Rush: uma árvore geral para as tropas (não uma coluna por tipo, porque virão tropas novas, como o lanceiro) e melhorias gerais, por exemplo de economia.
- Redistribuição gratuita, só fora das fases. Três presets de melhorias, aplicados com um toque.
- Rejogar fase vencida dá XP e recursos limitados.

### 15.2 Nível do jogador

XP geral, ganho a partir das estrelas. O nível libera conteúdo no jogo como um todo, nunca poder dentro da fase.

### 15.3 Diamantes

- Comprados fora do jogo ou ganhos jogando: por recompensa de vitória e por drop de abate com chance percentual (Pendente). Os dropados na partida só são recebidos se o jogador vencer.
- **Derrota:** sem estrela, mas o jogador recebe um mínimo de diamantes proporcional às ondas vencidas. Sair no meio conta como derrota.
- **Consumíveis de uma partida** (exemplos): bênção que dobra o Favor no início; três vidas extras para o castelo, que contam para as estrelas. São sobrevida, não vitória garantida, e não são poder permanente.
- Quem não paga consegue tudo jogando; comprar só acelera.

### 15.4 Desbloqueio de heróis e deuses

Heróis e deuses aparecem primeiro na campanha. Depois da fase em que surgem, ficam disponíveis para desbloqueio com moeda do jogo (diamantes ou cartas e fragmentos ganhos nas fases). Os detalhes de como desbloquear, como mostrar isso ao jogador e de onde vêm os recursos estão **Pendentes**.

### 15.5 Tropa extra (depois do MVP)

Um botão no HUD chama, de tempos em tempos, uma tropa extra de mercenários, como respiro em situação crítica. A tropa é fixa, mais fraca e mais curta que uma tropa produzida, para não substituir a produção no castelo. As variações dela são escolhidas nas Melhorias.

## 16. Modelo de negócio

- **Gratuito**, para alcançar o máximo de jogadores. Precisa ser rentável para garantir o futuro do projeto e contratações.
- **Anúncios recompensados:** opcionais e sempre fora da partida; o jogador escolhe assistir em troca de recursos.
- **Pular vídeos:** compra que dá a recompensa do anúncio sem assistir.
- **Começa com anúncios e cosméticos.** O passe de batalha vem quando a equipe crescer, porque exige conteúdo novo constante.
- **Nada de pagar para ganhar:** o que se vende é conforto, aparência e conteúdo, nunca poder para vencer a fase. O jogador deve sentir vontade de investir.
- **Loja:** o que se compra com diamantes tem conteúdo conhecido (por exemplo, fragmentos de um herói escolhido). Recompensas aleatórias, como baús, só se ganham jogando. A Lei 15.211/2025 (ECA Digital) proíbe caixas de recompensa pagas em jogos acessíveis a menores.
- **Pendente:** estudo de mercado antes de detalhar o resto.

## 17. Arquitetura do jogo

O jogo é construído em três camadas: o núcleo é código e fica fixo, e todo o resto é dado e cresce. Herói, deus, inimigo, fase ou capítulo novo é conteúdo novo, nunca código novo.

&#91;embedded content: Arquitetura do jogo · 3 camadas\]

- **Núcleo:** as regras que não mudam entre fases ou capítulos: relógio da partida em passos fixos, movimento e raios, bloqueio e escolha de alvo, combate e fórmula de dano. Os passos fixos deixam a partida reproduzível e pronta para ficar online depois.
- **Sistemas:** regras genéricas que leem o conteúdo: economia, ondas e rotas, castelo e evolução, modificadores (todo bônus de deus, item ou melhoria tem o mesmo formato), fim de fase, progressão, loja e prêmios, campanha e salvamento.
- **Conteúdo como dados:** cada herói, deus, tropa, inimigo, torre e item é uma ficha com status, arte e efeitos, que segue um contrato (a lista de campos que todo item daquele tipo tem). No Godot, cada ficha é um Resource. Entra um novo sem mexer no núcleo.
- **Fase como template:** cada fase é um mapa-base (terreno, castelo, todos os pontos de torre e rotas possíveis) mais uma configuração: rotas abertas, ondas e inimigos, saldo inicial, regras de desafio, heróis e deuses permitidos e recompensas. Uma fase nova se faz preenchendo dados, não editando cena por cena.
- **Capítulo como pacote:** um capítulo novo é uma pasta com mapas-base, fichas de heróis, deuses e inimigos e a lista de fases. O núcleo e os sistemas continuam os mesmos.

Detalhes dos contratos, do sistema de modificadores e das decisões técnicas no documento de consulta "Mapa de sistemas do jogo" (seção 21).

## 18. Teste do MVP

**Testadores:** John, Arthur e poucas pessoas próximas. Testadora prevista: a esposa do John, que conhece bem o Kingdom Rush. O critério de sucesso está na seção 2.5.

Riscos a observar:

- A capacidade de bloqueio deixa passar inimigos demais ou de menos?
- A renda por tempo supera o ganho por abate e recompensa esperar?
- A torre é opcional demais ou domina a defesa? A primeira torre vira sempre a mesma compra?
- A trava da torre no primeiro alvo frustra?
- O herói resolve demais sozinho? Alerta se fizer mais de 35% dos abates.
- A faixa de três estrelas (perder no máximo 3 vidas) é estreita demais?
- A pausa tática dá vantagem demais?
- A conta de tempo fecha (10 ondas com espera de 1 a 1,5 minuto em cerca de 15 minutos)?
- As três rotas cabem na tela vertical sem rolar demais?
- As tropas em fileiras são fáceis de selecionar com o dedo?
- O toque duplo no sinalizador antecipa ondas sem querer?
- O jogador percebe quando uma tropa está levando flechadas de longe?
- Quantas unidades o jogador bom tem na onda 10, e o celular aguenta?

## 19. Pendências

**Para o MVP**

- Tabela de status (tropas, herói, torre, inimigos) e lista das 10 ondas.
- Regras de mapa: raios, pontos de torre, comprimento das rotas; dano e alcance da torre; tempo de espera entre ondas.
- Interface mínima; posição inicial, área de toque e regras da bandeira (existe desde o início? pode ser removida?).
- Tropa sem bandeira definida: para no portão ou vai a um ponto padrão?
- Se o jogador pode dar todos os comandos durante a espera entre ondas.
- Efeito da 2ª evolução da torre.

**Para o jogo**

- Desbloqueio de heróis e deuses: como mostrar, como desbloquear e de onde vêm os recursos.
- Deuses iniciais; vantagens, Poder Divino e Unidade Mitológica de cada deus.
- Habilidades de cada herói.
- Ordem das fases do Capítulo 1 e chefes que faltam; número de ramificações pensando no custo de produção.
- Duelo: mostrar as possibilidades ao jogador ou deixá-lo descobrir; se os caminhos já jogados ficam guardados.
- No caminho em que Heitor morreu, quem entra quando o herói escolhido repete o coadjuvante: outro troiano já desbloqueado ou dois heróis escolhidos pelo jogador.
- Usos e valores do Favor no jogo completo.
- Nomes e benefícios específicos de cada era.
- Custo e efeito das ramificações de tropa e de torre.
- Recompensa de elites e chefes; chance de drop de diamantes.
- Regra de vantagem entre tropas e tipos de dano.
- Arquitetura online e onde fica salvo o progresso.
- Monetização, depois do estudo de mercado.
- Defesa própria do castelo.

## 20. Ideias para depois

Ideias aprovadas na direção, guardadas para detalhar mais tarde. Nada aqui foi descartado.

- **Constelações:** a mesma árvore de Melhorias apresentada como constelações temáticas (por exemplo, Órion, Hércules e Ártemis), inspiradas na árvore passiva do Path of Exile, com estrelas maiores como marcos.
- **Formação e postura:** menu da tropa no HUD com posicionamento, formação (coluna, fileira, bloco) e postura, como no Age of Mythology.
- **Reagrupamento** ou união de tropas incompletas.
- **Bônus temporários com Favor** (exemplo: +10% de ataque e defesa por 3 ondas).
- **Evolução que cura:** ao evoluir uma tropa, as unidades em campo recuperam toda a vida, como no Kingdom Rush.
- **Novos tipos de torre** em pacotes de expansão: torre de magia ligada a Apolo, gelo, veneno, óleo quente.
- **Troca de Ouro por Comida**, só se o teste mostrar jogadores travados com Ouro parado.
- **Cartas de inimigo:** cada inimigo tem uma pequena chance de soltar uma carta, com visuais e raridades diferentes, para completar um álbum com recompensas.
- **Itens da mitologia** como recompensas (relíquias de heróis, oferendas aos deuses, ambrosia), a detalhar no catálogo de itens.
- **Cavalo de Troia** como evento de uma fase final (sugestão).
- **Ciclope** e outras criaturas como eventos especiais.
- **Coleções, outros recursos e drops raros** durante a partida; itens que dão bloqueio 3 ao herói.
- **Capítulos de outras mitologias** (egípcia, nórdica) e o modo livre misturando heróis de capítulos diferentes.
- **Som e música.**

## 21. Documentos de consulta

Material de apoio, sem valor de decisão. O que vale é este documento.

- [Mapa de sistemas do jogo](https://claude.ai/artifact/1Hbf1yQKfqSyVdW2PAgUkT): contratos, modificadores e decisões técnicas.
- [Catálogo de itens e economia](https://claude.ai/artifact/VTV365SW48UQhQcAuqcPg5): proposta de moedas, itens, fontes, ralos e monetização.
- [Wireframe do jogo](https://claude.ai/artifact/4FWsqVuj1uuXq1BGGqu2s2): 8 telas.
- [Avaliação de 25/11/2026](https://claude.ai/artifact/4D7YfoWHY4W1y2wCHH4AMk): banca de 6 avaliadores e propostas de ondas e economia.
- [Pesquisa de fórmulas de combate e Age of Mythology](https://claude.ai/code/artifact/0505d188-cc73-4081-a2d2-8f2e7c51c84c).
- Pesquisa de evolução, estrelas e monetização: no projeto, em claude/pesquisa-evolucao-estrelas-monetizacao.md.
