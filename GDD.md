# 📘 Game Design Document (GDD) — MathCode

**Versão do Documento:** 1.0 (Atualizado)  
**Título do Jogo:** MathCode — Aventura de Plataforma & Matemática  
**Gênero:** Plataforma 2D / Educativo (Edutainment) / Ação Lateral (*Side-scroller*)  
**Plataforma Alvo:** Web Browser (Desktop — Windows, macOS, Linux)  
**Público-Alvo:** Crianças e estudantes do Ensino Fundamental (anos iniciais e finais) e entusiastas de jogos casuais de plataforma.

---

## 1. Visão Geral do Jogo (High Concept)

**MathCode** combina a fluidez e a diversão dos jogos clássicos de plataforma 2D com a resolução dinâmica de desafios aritméticos. O jogador assume o papel de **Pip**, uma raposinha aventureira que viaja por cinco mundos fantásticos ao lado de seu amigo dragão **Pyrito**. Em cada fase, muros de pedra mágicos bloqueiam a passagem e só se abrem quando o jogador resolve a equação exibida e golpeia o bloco numérico com a resposta certa. Em caso de erro, o jogo não pune de forma frustrante: o dragãozinho Pyrito oferece dicas pedagógicas sobre como decompor ou resolver a operação.

---

## 2. Personagens e Narrativa

* **Pip (Protagonista Jogável):** Uma raposinha ágil com mochila de explorador. Possui movimentos precisos de corrida, salto variável e ataque giratório (*spin*). Pode ser personalizada com 8 trajes diferentes na loja.
* **Pyrito (Companheiro / Mentor):** Um pequeno dragão roxo e dourado que voa acompanhando o Pip durante toda a jornada. Ele comemora quando uma parede se abre ou quando a fase é concluída, e atua como tutor pedagógico dando dicas de cálculo sempre que o jogador escolhe um bloco incorreto.
* **Paredes Guardiãs:** Estruturas de pedra viva que dormem até que o jogador se aproxime. Ao acordarem, revelam o enigma matemático que precisa ser solucionado para liberar o caminho.

---

## 3. Mecânicas de Gameplay (Core Loop)

O ciclo principal de gameplay (*Core Loop*) consiste em:
1. **Explorar e Superar Obstáculos:** Percorrer o cenário da esquerda para a direita saltando sobre abismos, desviando de espinhos, utilizando plataformas móveis e quebrando caixas em busca de moedas.
2. **Calcular e Resolver:** Aproximar-se da Parede Guardiã, ler a equação matemática e identificar a resposta correta entre os 3 ou 4 blocos flutuantes disponíveis.
3. **Progredir e Personalizar:** Concluir todas as seções da fase até alcançar a bandeira dourada e utilizar as moedas acumuladas na **Loja do Pip** para comprar novas skins antes de avançar para o próximo bioma.

### 3.1. Física e Movimentação do Personagem
Para garantir uma sensação responsiva nos controles (*game feel*), o Pip conta com:
* **Pulo de Altura Variável:** Soltar a tecla de pulo cedo reduz a velocidade vertical ascendente, permitindo pulos curtos ou longos.
* **Coyote Time (0,15s):** Permite que o jogador ainda consiga pular por uma fração de segundo após sair da borda de uma plataforma.
* **Jump Buffer (0,12s):** Registra o comando de pulo mesmo que pressionado levemente antes de tocar o chão.
* **Squash & Stretch:** Animações elásticas procedurais ao pular, aterrissar, girar e renascer.
* **Ataque de Giro (*Spin*):** Ataque rápido de 0,35s com *cooldown* de 0,2s que destrói caixas ao redor (raio de 62px) e ativa blocos de resposta (raio de 78px).

### 3.2. Sistema de Vidas e Checkpoints
* **Vidas Iniciais:** 3 corações (❤️❤️❤️) por fase.
* **Dano Ambiental (Buracos e Espinhos):** Retira **1 vida inteira (−1 ❤️)** e reposiciona o jogador no último *checkpoint* seguro, concedendo 1,5s de invencibilidade.
* **Erro Matemático:** Retira **meia vida (−½ ❤️)** e aciona a dica pedagógica do Pyrito para incentivar uma nova tentativa consciente, sem retroceder a posição do jogador.
* **Game Over:** Ao zerar as 3 vidas, a fase é reiniciada, mas todas as moedas coletadas permanecem salvas na carteira do jogador.

---

## 4. Progressão Pedagógica e Dificuldade Matemática

O gerador de desafios matemáticos (`gen(L)`) adapta o tipo de operação e a magnitude dos números de acordo com a fase atual (`L`) e a seção da fase (`i`):

| Nível de Dificuldade (`T`) | Tipo de Operação | Exemplo | Dica Pedagógica do Pyrito |
| :---: | :--- | :---: | :--- |
| **0** | Multiplicação (Tabuada 3 a 9) | `6 × 7 = ?` | *"Pense na tabuada ou decomponha a conta em partes menores!"* |
| **1** | Divisão Exata | `42 ÷ 7 = ?` | *"Divisão é o contrário: quantas vezes 7 cabe em 42?"* |
| **2** | Adição de Dezenas | `28 + 35 = ?` | *"Some as dezenas primeiro e depois as unidades!"* |
| **3** | Subtração de Dezenas | `64 − 29 = ?` | *"Tire as dezenas e depois as unidades."* |
| **4** | Multiplicação + Adição | `4 × 8 + 15 = ?` | *"Primeiro a multiplicação, depois a soma!"* |
| **5** | Fator Desconhecido (Álgebra Inicial) | `6 × ? = 54` | *"Quantas vezes 6 cabe em 54?"* |
| **6+** | Expressões com Parênteses | `(4 + 5) × 6 = ?` | *"Resolva o que está entre parênteses primeiro!"* |

* **Escalonamento Contínuo:** A partir da Fase 7, os desafios alternam entre os modelos avançados incrementando os operandos proporcionalmente ao nível atual, garantindo desafio infinito.
* **Distratores Inteligentes:** As opções incorretas são geradas próximas ao valor real (variação de ±12% ou mínimo de ±3), evitando alternativas óbvias demais e estimulando o cálculo exato.

---

## 5. Mundos (Biomas) e Direção de Arte

O jogo utiliza gráficos vetoriais renderizados proceduralmente via Canvas 2D com contornos marcados estilo *cartoon* (`#2b1b3d`) e suporte a tema claro/escuro na página. As fases alternam entre **5 biomas**:

1. **Vale dos Cogumelos:** Céu azul celeste, grama verde vibrante e cogumelos gigantes coloridos ao fundo.
2. **Dunas Douradas:** Pôr do sol alaranjado, areias douradas e cactos estilizados.
3. **Montanha Gelada:** Clima glacial em tons de azul-claro e branco com pinheiros nevados.
4. **Vulcão Rúnico:** Atmosfera dramática em roxo escuro e laranja vulcânico com cristais incandescentes.
5. **Galáxia Neon:** Cenário espacial noturno em azul-profundo, turquesa neon e cristais brilhantes.

---

## 6. Economia e Sistema de Recompensas (Loja do Pip)

* **Fontes de Moedas:**
  * Moeda flutuante no cenário: **+1 🪙**
  * Quebrar caixa de madeira: **+2 🪙**
  * Acertar resposta matemática: **+10 🪙**
* **Itens Cosméticos Disponíveis na Loja:**
  1. **Pip Clássico:** Grátis (Padrão)
  2. **Capa de Herói:** 25 🪙
  3. **Óculos Radicais:** 35 🪙
  4. **Chapéu de Mago:** 45 🪙
  5. **Faixa Ninja:** 55 🪙
  6. **Pijama de Dragão:** 65 🪙
  7. **Coroa Real:** 80 🪙
  8. **Astronauta:** 100 🪙

* **Persistência de Dados:** O estado do jogador (`{ coins, L, own, eq }`) é gravado automaticamente no `localStorage` do navegador sob a chave `mathcode`.

---

## 7. Interface do Usuário (UI / HUD)

* **HUD Superior Esquerdo:**
  * Indicador de Vidas (`❤️` / `💔` / `🖤`)
  * Contador de Moedas Totais (`🪙`)
  * Contador de Caixas Quebradas na Fase (`📦`)
  * Indicador de Fase Atual e Nome do Bioma (`Fase X · Nome do Bioma`)
* **Câmera Dinâmica:** Segue o jogador suavemente e aplica um leve *zoom in* (`1.12x`) automático quando o Pip se aproxima de uma Parede Guardiã ativa para destacar a equação e os blocos de resposta.
* **Balão de Mensagens (`#hint`):** Exibe notificações de início/fim de fase e dicas educativas do Pyrito.

---

## 8. Limitações Atuais e Roadmap Futuro

* **Limitações da Versão Atual:**
  * Jogo focado em navegadores Desktop com teclado físico (sem controles *touch* na tela).
  * Ausência de efeitos sonoros e trilha musical (Web Audio API planejada para versão futura).
  * Ausência de botão de pausa e seletor de níveis / reset de progresso pela interface.
* **Próximos Passos (Roadmap):**
  * Implementação de efeitos sonoros sintetizados via *Web Audio API* (sem arquivos externos).
  * Adição de controles *touchscreen* na tela para dispositivos móveis.
  * Fase tutorial guiada interativa no primeiro acesso.
  * Menu de seleção de fases e estatísticas de acertos por operação matemática.
