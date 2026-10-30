# 🎮 MathCode — Aventura de Plataforma & Matemática

**MathCode** é um jogo educativo 2D de plataforma e raciocínio matemático desenvolvido para navegador web. Na aventura, você controla a raposinha **Pip**, acompanhada de seu fiel amigo dragãozinho **Pyrito**, explorando diferentes mundos repletos de obstáculos, plataformas móveis, caixas e moedas. Para avançar por cada fase, o jogador precisa resolver operações matemáticas que bloqueiam o caminho com paredes de pedra gigantes, unindo agilidade nos controles e cálculo mental.

---

## 📄 Documentação e Links Importantes

- **Repositório no GitHub:** [https://github.com/jaofaust/MathCode](https://github.com/jaofaust/MathCode)
- **Game Design Document (GDD) Atualizado:** Pode ser consultado diretamente no arquivo [**`GDD.md`**](./GDD.md) localizado na raiz deste repositório.

---

## 💻 Requisitos Necessários

O projeto foi construído utilizando tecnologias web nativas e não exige instalação de engines pesadas ou bancos de dados.

* **Sistema Operacional:** Qualquer sistema operacional desktop moderno (Windows 10/11, macOS, Linux Ubuntu/Debian/Fedora, ChromeOS).
* **Programas Necessários (Navegador Web):** Qualquer navegador atualizado com suporte a HTML5 Canvas e JavaScript ES6+:
  * Google Chrome (v90 ou superior)
  * Microsoft Edge (v90 ou superior)
  * Mozilla Firefox (v88 ou superior)
  * Safari (v14 ou superior) / Opera
* **Engine e Tecnologias Utilizadas:**
  * **HTML5 Nativo (`<canvas>` 2D API)**, **CSS3** e **JavaScript Vanilla (ES6+)** em arquivo único (`index.html`). Não utiliza engines externas (como Unity ou Godot) nem requer runtimes adicionais.
* **Periféricos:** Teclado físico (necessário para movimentação e ações do personagem) e mouse/trackpad (para clicar nos botões de menu e loja).
* **Conexão com a Internet:** **Opcional.** O jogo funciona 100% *offline*; a conexão com a internet é usada apenas para carregar a fonte tipográfica *Fredoka* via Google Fonts (caso esteja sem internet, o jogo utiliza automaticamente a fonte padrão do sistema).

---

## 📥 Como Baixar ou Clonar o Projeto

Você pode obter o projeto de duas maneiras:

### Opção 1: Clonando via Git (Terminal / Prompt de Comando)
Caso tenha o [Git](https://git-scm.com/) instalado em seu computador, execute o comando abaixo no terminal:

```bash
git clone https://github.com/jaofaust/MathCode.git
cd MathCode
```

### Opção 2: Baixando o Arquivo ZIP pelo Navegador
1. Acesse a página principal do repositório no GitHub.
2. Clique no botão verde **`<> Code`** no canto superior direito.
3. Selecione a opção **`Download ZIP`**.
4. Extraia o conteúdo do arquivo `.zip` baixado para uma pasta de sua preferência no computador.

---

## ⚙️ Instalação de Dependências e Configuração do Ambiente

**Não é necessário instalar nenhuma dependência, biblioteca externa ou configurar variáveis de ambiente.**
O jogo é *zero-dependency* (autocontido no arquivo `index.html`) e utiliza o próprio `localStorage` do navegador para salvar o progresso automaticamente.

---

## 🚀 Passo a Passo para Executar o Jogo

Escolha qualquer um dos métodos abaixo para abrir e jogar:

### Método 1: Execução Direta pelo Explorador de Arquivos (Recomendado)
1. Abra a pasta onde o projeto foi extraído ou clonado (`MathCode`).
2. Localize o arquivo **`index.html`**.
3. Dê **dois cliques** sobre o arquivo `index.html` (ou clique com o botão direito -> *Abrir com* -> escolha seu navegador, como Google Chrome, Edge ou Firefox).
4. O jogo será carregado imediatamente na janela do navegador.

### Método 2: Execução via Servidor HTTP Local (Opcional para Desenvolvedores)
Se preferir executar através de um servidor local:
* **Com Python 3:** Abra o terminal na pasta do projeto e execute `python -m http.server 8000`, depois acesse `http://localhost:8000` no navegador.
* **Com VS Code:** Instale a extensão *Live Server*, clique com o botão direito em `index.html` e selecione **"Open with Live Server"**.

---

## 🕹️ Como Iniciar uma Partida e Controles

### Como Iniciar uma Partida
1. Ao abrir o arquivo `index.html`, você verá a tela inicial sobreposta ao cenário com o título **MathCode** e uma breve introdução.
2. *(Opcional)* Clique em **"🛍️ Loja de roupinhas"** para visualizar, comprar ou equipar visuais para o Pip usando suas moedas acumuladas, e clique em **"Voltar"** para retornar à tela inicial.
3. Clique no botão laranja **"Começar"** (ou **"Continuar — Fase X"**, caso já tenha fases salvas anteriormente no navegador) para iniciar a partida imediatamente.

### Tabela de Controles

| Tecla / Comando | Ação no Jogo | O que cada comando faz |
| :--- | :--- | :--- |
| **`A`** ou **`Seta Esquerda (←)`** | Mover para a esquerda | Desloca a raposinha Pip horizontalmente para a esquerda. |
| **`D`** ou **`Seta Direita (→)`** | Mover para a direita | Desloca a raposinha Pip horizontalmente para a direita (em direção ao objetivo da fase). |
| **`Espaço`**, **`W`** ou **`Seta Cima (↑)`** | Pular | Faz o Pip saltar. Segurar a tecla por mais tempo resulta em um pulo mais alto; soltar rápido faz um pulo curto. Pular sobre caixas de madeira as destrói, e pular por baixo de um bloco numérico seleciona aquela resposta matemática. |
| **`Shift`** *(Esq./Dir.)* ou **`X`** | Ataque de Giro (*Spin*) | Faz o Pip girar rapidamente no próprio eixo. Quebra caixas de madeira próximas e também ativa blocos de resposta matemática ao encostar neles. |
| **`Clique Esquerdo do Mouse`** | Interagir com Menus | Utilizado para acionar os botões *"Começar"*, *"Continuar"*, *"Tentar de novo"*, *"Próxima fase"*, abrir a *"Loja de roupinhas"* e comprar/equipar itens. |

---

## 🎯 Objetivo, Regras Básicas, Vitória, Derrota e Progressão

### Objetivo do Jogador
Guiar o **Pip** desde o início do percurso até a **bandeira dourada** no final de cada fase, superando obstáculos de plataforma (abismos, espinhos e plataformas móveis) e resolvendo corretamente todas as equações matemáticas que bloqueiam o caminho com paredes de pedra.

### Regras Básicas e Mecânicas
1. **Paredes de Pedra e Perguntas Matemáticas:**
   * Cada fase é dividida em seções (de 2 a 4 seções por fase). Ao final de cada seção, há uma **parede de pedra** com olhinhos que acorda quando o Pip se aproxima e exibe uma **equação matemática** em uma placa acima dela.
   * Antes de cada parede, existem **3 ou 4 blocos amarelos flutuantes** contendo possíveis respostas numéricas.
   * Para responder, posicione-se abaixo do bloco com o valor correto e **pule batendo a cabeça nele** (ou use o **giro** com `Shift`/`X` próximo ao bloco).
2. **Acertos e Erros nas Contas:**
   * **Resposta Correta:** A parede de pedra abaixa liberando a passagem, os blocos daquela pergunta se desfazem e você recebe uma recompensa de **+10 moedas (🪙)**.
   * **Resposta Incorreta:** O bloco pisca em vermelho e treme, você perde **meia vida (−½ ❤️)** e o dragãozinho **Pyrito** mostra uma **dica pedagógica** na parte inferior da tela explicando como raciocinar sobre aquela operação.
3. **Coleta de Moedas e Caixas:**
   * **Moedas (🪙):** Espalhadas pelo cenário; cada moeda coletada soma **+1 moeda** ao seu saldo.
   * **Caixas de Madeira (📦):** Podem ser quebradas pulando em cima delas (o que impulsiona o Pip para o alto) ou usando o ataque de giro (`Shift`/`X`). Cada caixa quebrada concede **+2 moedas**.
4. **Loja do Pip (Customização):**
   * Entre uma fase e outra (ou antes de começar), o jogador pode gastar suas moedas na **Loja do Pip** para desbloquear e vestir **8 skins diferentes**: *Pip Clássico* (grátis), *Capa de Herói* (25 🪙), *Óculos Radicais* (35 🪙), *Chapéu de Mago* (45 🪙), *Faixa Ninja* (55 🪙), *Pijama de Dragão* (65 🪙), *Coroa Real* (80 🪙) e *Astronauta* (100 🪙).

### Condições de Vitória e Progressão
* **Vitória na Fase:** Abrir **todas** as paredes de pedra da fase atual e cruzar a **bandeira dourada (🚩)** localizada no final do percurso.
* **Progressão Contínua:**
  * Ao vencer uma fase, o progresso é salvo automaticamente no navegador (`localStorage`) e o jogador avança para a fase seguinte (`Fase + 1`).
  * O jogo percorre ciclicamente **5 biomas temáticos** com paletas e cenários próprios:
    1. *Vale dos Cogumelos*
    2. *Dunas Douradas*
    3. *Montanha Gelada*
    4. *Vulcão Rúnico*
    5. *Galáxia Neon*
  * **Curva de Dificuldade:** Conforme o jogador avança de fase, o número de paredes por fase aumenta (até 4 por nível), surgem mais abismos, espinhos e plataformas móveis mais rápidas, passam a existir 4 opções de resposta por pergunta (em vez de 3) e as operações evoluem gradualmente:
    * Multiplicação simples (`a × b = ?`)
    * Divisão exata (`a ÷ b = ?`)
    * Adição de dezenas (`a + b = ?`)
    * Subtração de dezenas (`a − b = ?`)
    * Expressões combinadas de multiplicação e soma (`a × b + c = ?`)
    * Descoberta de fator desconhecido (`a × ? = c`)
    * Expressões com parênteses (`(a + b) × c = ?`) e números maiores nas fases avançadas.

### Condições de Derrota e Penalidades
* O jogador inicia cada fase com **3 vidas completas (❤️❤️❤️)** exibidas no canto superior esquerdo (HUD).
* **Penalidades:**
  * **Cair em um buraco (abismo)** ou **encostar em espinhos no chão:** Custa **1 vida inteira (−1 ❤️)**. Caso ainda restem vidas, o Pip renasce automaticamente no último *checkpoint* seguro antes do obstáculo, com 1,5 segundo de invencibilidade temporária (piscando).
  * **Errar uma resposta matemática:** Custa **meia vida (−½ ❤️)**, transformando um coração cheio (❤️) em meio coração (💔) ou esvaziando-o (🖤).
* **Derrota (*Game Over*):** Quando as vidas chegam a **0 (🖤🖤🖤)**, a partida é encerrada com a tela de **"Fim de jogo 😵"**. O jogador pode clicar em **"Tentar de novo"** para reiniciar a fase atual com 3 vidas novas, **sem perder as moedas** que já havia coletado.

---

## ⚠️ Limitações Conhecidas da Versão Atual e Funcionalidades Não Implementadas

Para avaliação da versão atual do protótipo, considere as seguintes limitações conhecidas e itens planejados para versões futuras:

1. **Ausência de Áudio (SFX e Trilha Sonora):** O jogo ainda não possui efeitos sonoros (pulo, coleta de moeda, quebra de caixa, acerto/erro) nem música de fundo nos biomas.
2. **Sem Suporte a Controles Touch (Mobile):** Embora o layout visual se adapte a diferentes tamanhos de tela, ainda não há botões virtuais na tela (*touchscreen*) para jogar em celulares ou tablets — é necessário utilizar um teclado físico.
3. **Sem Tutorial Interativo Guiado dentro da Fase:** As instruções aparecem no painel inicial e na barra inferior de comandos, além das dicas contextuais do Pyrito ao errar contas, mas não há uma fase zero/tutorial passo a passo interativo.
4. **Sem Menu de Pausa ou Reinício Manual de Progresso na UI:** Não há uma tecla de pausa (`Esc`/`P`) durante a ação nem um botão na tela para zerar o *save* ou escolher fases anteriores (para reiniciar do zero na Fase 1, é necessário limpar o `localStorage` do navegador via *Inspecionar -> Aplicativo -> Armazenamento Local*).
5. **Roupas Apenas Cosméticas:** As skins da Loja do Pip alteram o visual do personagem, mas ainda não concedem bônus ou habilidades especiais de gameplay (como pulo duplo ou ímã de moedas).
6. **Geração Procedural de Fases:** Os obstáculos e perguntas são gerados proceduralmente a cada tentativa; por isso, ao reiniciar uma fase após *Game Over*, a disposição exata das plataformas e os números das equações mudam mantendo o mesmo nível de dificuldade.
