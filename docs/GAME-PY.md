### 1. Pygame-CE (Community Edition) - O Clássico que Ganhou um "Turbo"
Se você procurar tutoriais antigos, vai achar o pygame original. Esqueça ele. O mercado adotou o Pygame-CE (Community Edition).

A Evolução (2024-2026): O projeto original ficou estagnado, então a comunidade fez um "fork" (uma bifurcação) e criou o Pygame-CE. Nas versões recentes (2.4 e 2.5+), ele ficou infinitamente mais rápido e ganhou suporte melhorado para resoluções modernas e controles de videogame.

A Pegada: É programação "raiz". Ele te dá uma tela preta e diz: "desenhe os pixels". Você controla a física, a gravidade, as colisões no braço. É excelente para entender os fundamentos da lógica de jogos (o famoso Game Loop).

### 2. Python Arcade - O Moderno e Elegante
Se o Pygame é um carro manual antigo, o Arcade é um carro automático moderno.

A Evolução (2024-2026): Com a consolidação da versão 3.0, o Arcade se tornou o queridinho dos desenvolvedores Python. Ele já usa os recursos modernos da linguagem, como Type Hinting (tipagem) e decoradores.

A Pegada: Ele foi construído em cima de OpenGL, o que significa que ele tem aceleração de hardware nativa (roda direto na Placa de Vídeo). Você consegue colocar milhares de elementos (sprites) na tela sem o FPS cair, algo que o Pygame sofre para fazer. É a melhor escolha para jogos 2D de plataforma (estilo Mario).

### 3. Ursina Engine - O 3D "Para Preguiçosos" (No bom sentido!)
Historicamente, fazer jogos 3D em Python era uma dor de cabeça. A Ursina mudou isso e virou uma febre em Game Jams e no YouTube nos últimos anos.

A Evolução (2024-2026): Amadureceu muito na manipulação de shaders e texturas, construída em cima de um motor super parrudo da Disney chamado Panda3D.

A Pegada: A sintaxe é incrivelmente simples. Com 10 linhas de código você abre uma janela, cria um cubo 3D, coloca uma textura de grama e faz a câmera girar. É perfeito para criar clones de Minecraft ou jogos de tiro "Low Poly" rapidamente.

Menção Honrosa: Godot (GDScript) - O Pulo do Gato
Eu sei que você pediu bibliotecas Python, mas eu não seria um bom assistente se não te desse essa dica de mercado: se você quer fazer um jogo comercial pesado e publicar nas lojas de celular ou na Steam, o caminho mais natural para um desenvolvedor Python é usar o Godot Engine.

Por que? A linguagem nativa dele (GDScript) foi desenhada para ser praticamente idêntica ao Python (usa indentação, não usa chaves {}). Você aprende em um fim de semana e tem em mãos um motor que hoje concorre com a Unity.