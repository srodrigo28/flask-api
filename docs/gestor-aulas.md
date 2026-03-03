# Gestor de Aulas

## Objetivo

Criar um gestor de treinamento focado em aprendizado continuo, controle de evolucao e organizacao de estudo.

A ideia inicial e trabalhar primeiro com os objetos do dominio, antes de transformar isso em estrutura de dados, banco ou tabelas.

O sistema precisa ajudar em quatro frentes:

1. Organizar o que estudar.
2. Controlar o que ja foi feito.
3. Medir a evolucao real.
4. Ajustar o plano conforme o aprendizado amadurece.

## Direcao Inicial

O foco nao e comecar por telas complexas ou banco de dados.

O foco e definir os objetos centrais que existem no sistema, suas responsabilidades e como eles se relacionam.

Esse documento serve como base para:

1. Modelagem de dominio.
2. Regras de negocio.
3. Futuras classes Python.
4. Estrutura de dados e persistencia.

## Objetos Principais

### 1. Usuario

Representa a pessoa que esta estudando.

Responsabilidade:

- Guardar identidade e contexto do aprendiz.
- Definir preferencia de ritmo e foco.
- Ser o centro do plano de treinamento.

Exemplos de papel:

- Quem esta aprendendo.
- Qual area quer desenvolver.
- Qual ritmo deseja manter.

### 2. PlanoTreinamento

Organiza a estrategia geral de aprendizado.

Responsabilidade:

- Definir a ordem do estudo.
- Separar prioridades.
- Responder o que vem agora.

Exemplos de papel:

- Plano principal da semana.
- Plano de foco mensal.
- Roteiro por objetivo tecnico.

### 3. Trilha

Representa um macrotema de evolucao.

Responsabilidade:

- Agrupar assuntos grandes.
- Dar direcao por area de conhecimento.

Exemplos:

- Flask
- APIs
- SQL
- Frontend
- Arquitetura

### 4. Modulo

Divide uma trilha em blocos menores.

Responsabilidade:

- Quebrar a trilha em partes controlaveis.
- Melhorar clareza e ritmo de execucao.

Exemplos:

Dentro da trilha `Flask`:

- Rotas
- Templates
- Blueprints
- Autenticacao

### 5. Conteudo

E a unidade pratica de aprendizado.

Responsabilidade:

- Representar exatamente o que sera estudado.
- Permitir conclusao, revisao e repeticao.

Exemplos:

- Aula
- Artigo
- Exercicio
- Projeto pequeno
- Revisao

### 6. SessaoTreino

Registra uma sessao real de estudo.

Responsabilidade:

- Registrar quando o estudo aconteceu.
- Medir duracao.
- Relacionar o estudo a um conteudo.
- Capturar como foi a experiencia.

Exemplos:

- Estudo de 45 minutos em rotas Flask.
- Revisao de 20 minutos em SQL.

### 7. Meta

Define um alvo de execucao.

Responsabilidade:

- Criar compromisso claro.
- Medir esforco planejado contra esforco realizado.

Exemplos:

- 5 horas por semana
- 4 sessoes por semana
- 3 conteudos concluidos
- 1 modulo finalizado

### 8. Progresso

Representa o estado atual de evolucao.

Responsabilidade:

- Mostrar o quanto ja foi avancado.
- Consolidar status de trilha, modulo ou conteudo.
- Permitir leitura objetiva da evolucao.

Exemplos:

- Conteudo com 60% de progresso
- Modulo concluido
- Trilha em andamento

### 9. Avaliacao

Registra percepcao de dominio e dificuldade.

Responsabilidade:

- Medir como o aprendizado foi absorvido.
- Apoiar ajustes no plano de estudo.

Exemplos:

- Dificuldade alta
- Confianca baixa
- Retencao media

## Relacoes Entre os Objetos

Estrutura conceitual inicial:

- Um `Usuario` pode ter varios `PlanoTreinamento`.
- Um `PlanoTreinamento` organiza varias `Trilha`.
- Uma `Trilha` possui varios `Modulo`.
- Um `Modulo` possui varios `Conteudo`.
- Um `Usuario` registra varias `SessaoTreino`.
- Uma `SessaoTreino` pode estar ligada a um `Conteudo`.
- Um `Usuario` define varias `Meta`.
- Um `Usuario` acumula varios registros de `Progresso`.
- Um `Usuario` pode registrar varias `Avaliacao`.

## Regras de Modelagem

Para manter o dominio limpo, cada objeto deve ter uma responsabilidade clara.

Regras iniciais:

- `Usuario` nao calcula progresso sozinho.
- `Trilha` nao guarda historico de sessoes.
- `SessaoTreino` nao organiza o plano inteiro.
- `Progresso` representa estado, nao conteudo.
- `PlanoTreinamento` organiza prioridade e sequencia.

Essas separacoes evitam bagunca quando o sistema crescer.

## Nucleo Minimo Para Comecar

Se quisermos iniciar com uma versao enxuta, o nucleo mais importante e:

1. `Usuario`
2. `PlanoTreinamento`
3. `Trilha`
4. `Modulo`
5. `Conteudo`
6. `SessaoTreino`
7. `Meta`
8. `Progresso`

Com esse conjunto, ja e possivel:

- Definir o que estudar.
- Quebrar o estudo em etapas.
- Registrar sessoes reais.
- Medir evolucao.
- Ajustar o ritmo.

## Exemplo Conceitual

Exemplo de uso do dominio:

- `Usuario`: Rodrigo
- `PlanoTreinamento`: Evolucao Backend
- `Trilha`: Flask
- `Modulo`: Rotas
- `Conteudo`: Criar endpoints com GET e POST
- `SessaoTreino`: 45 minutos
- `Avaliacao`: dificuldade 4 de 5
- `Progresso`: conteudo 60%

Esse exemplo ja mostra como transformar vontade de aprender em controle pratico.

## Visao de Produto

Esse gestor nao deve nascer como um simples cadastro de aulas.

Ele deve nascer como um sistema de disciplina e evolucao.

Ou seja:

- Menos foco em catalogo.
- Mais foco em clareza do proximo passo.
- Mais foco em constancia.
- Mais foco em historico de crescimento.

Se o sistema nao ajudar a responder:

- O que estudar agora?
- O que foi concluido?
- Onde estou travando?
- Como estou evoluindo?

entao ele ainda nao esta cumprindo o objetivo.

## Proximo Passo

Depois desta fase de objetos, a proxima etapa e detalhar cada objeto em tres partes:

1. Atributos essenciais.
2. Comportamentos e metodos.
3. Regras de negocio.

So depois disso faz sentido transformar o dominio em:

1. Classes Python.
2. Estrutura de dados.
3. Modelos de banco.
4. Rotas e interfaces.
