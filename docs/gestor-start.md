# Gestor Start

## Objetivo

Definir a sequencia de criacao do projeto `Gestor de Aulas`, partindo da modelagem de dominio para uma aplicacao real em Flask, organizada em MVC e com componentes reaproveitaveis.

Este arquivo e o roteiro de execucao do projeto.

Ele responde:

1. Em que ordem o sistema sera criado.
2. Como a arquitetura sera organizada.
3. Quais partes devem nascer primeiro.
4. Como manter reuso e clareza desde o inicio.

## Direcao de Arquitetura

O projeto sera construido com foco em:

1. MVC como base estrutural.
2. Separacao clara de responsabilidade.
3. Reuso de componentes visuais e de logica.
4. Crescimento incremental.

### Leitura pratica do MVC neste projeto

- `Model`: representa os objetos do dominio e depois os dados persistidos.
- `View`: templates HTML e componentes visuais reutilizaveis.
- `Controller`: recebe a acao, organiza a regra e entrega a resposta.

Como estamos em Flask, a organizacao pode usar:

- `models` para dominio e persistencia
- `controllers` para fluxo e regra de entrada
- `routes` para endpoints e navegacao
- `templates` para views
- `services` para regras de negocio reutilizaveis

## Principios de Construcao

Antes de codar, manter estas regras:

1. Nao misturar regra de negocio com template.
2. Nao colocar tudo em `app.py`.
3. Nao acoplar a estrutura ao banco cedo demais.
4. Criar primeiro o dominio, depois a navegacao, depois persistencia.
5. Tudo que se repetir duas vezes deve virar componente ou servico.

## Sequencia de Criacao

## Etapa 1: Fundacao do Projeto

Primeiro criamos a base tecnica minima.

Objetivo:

- Subir a aplicacao.
- Definir a organizacao de pastas.
- Preparar o projeto para crescimento.

Itens:

1. Criar `app.py`.
2. Criar `config.py`.
3. Criar a pasta `app/`.
4. Criar a estrutura inicial de MVC.
5. Definir ponto de entrada e registro de rotas.

Estrutura inicial recomendada:

```text
flask-api/
|-- app.py
|-- config.py
|-- .env
`-- app/
    |-- controllers/
    |-- models/
    |-- routes/
    |-- services/
    |-- templates/
    |   |-- layouts/
    |   |-- pages/
    |   `-- components/
    `-- static/
        |-- css/
        |-- js/
        `-- img/
```

Resultado esperado:

- Aplicacao Flask rodando.
- Estrutura limpa.
- Base pronta para evoluir sem bagunca.

## Etapa 2: Dominio em Objetos

Agora transformamos a ideia em classes de dominio, ainda sem depender totalmente do banco.

Objetivo:

- Modelar o sistema pelo que ele faz.
- Garantir clareza antes da persistencia.

Objetos iniciais:

1. `Usuario`
2. `PlanoTreinamento`
3. `Trilha`
4. `Modulo`
5. `Conteudo`
6. `SessaoTreino`
7. `Meta`
8. `Progresso`
9. `Avaliacao`

Ordem sugerida de modelagem:

1. `Usuario`
2. `PlanoTreinamento`
3. `Trilha`
4. `Modulo`
5. `Conteudo`
6. `SessaoTreino`
7. `Meta`
8. `Progresso`
9. `Avaliacao`

Resultado esperado:

- Classes conceituais definidas.
- Relacoes claras entre os objetos.
- Regras de negocio prontas para virar implementacao.

## Etapa 3: Regras de Negocio em Services

Antes de montar telas complexas, separamos a logica reutilizavel.

Objetivo:

- Evitar controllers inchados.
- Centralizar a inteligencia do sistema.

Services iniciais recomendados:

1. `plano_service`
   organiza prioridade e proximos passos.

2. `progresso_service`
   calcula avancos por conteudo, modulo e trilha.

3. `sessao_service`
   registra sessoes e consolida tempo estudado.

4. `meta_service`
   compara metas planejadas com execucao real.

5. `avaliacao_service`
   registra dificuldade, retencao e confianca.

Resultado esperado:

- Regras centralizadas.
- Reuso de logica.
- Base pronta para controllers simples.

## Etapa 4: Controllers e Fluxo da Aplicacao

Com o dominio e os services definidos, criamos o fluxo principal.

Objetivo:

- Organizar entradas do sistema.
- Fazer a aplicacao responder com clareza.

Controllers iniciais:

1. `home_controller`
   responsavel pelo dashboard inicial.

2. `trilha_controller`
   gerencia trilhas de aprendizado.

3. `modulo_controller`
   gerencia modulos de uma trilha.

4. `conteudo_controller`
   gerencia conteudos estudaveis.

5. `sessao_controller`
   registra sessoes de estudo.

6. `meta_controller`
   cria e acompanha metas.

7. `progresso_controller`
   entrega a leitura da evolucao.

Resultado esperado:

- Fluxo principal da aplicacao definido.
- Cada controller com responsabilidade enxuta.

## Etapa 5: Rotas

Agora ligamos navegacao e controllers.

Objetivo:

- Criar entradas claras.
- Separar navegacao por area funcional.

Rotas iniciais sugeridas:

1. `/`
   dashboard inicial

2. `/trilhas`
   listar e criar trilhas

3. `/trilhas/<id>`
   ver detalhes da trilha

4. `/modulos/<id>`
   ver detalhes do modulo

5. `/conteudos/<id>`
   ver detalhes do conteudo

6. `/sessoes`
   listar e registrar sessoes

7. `/metas`
   listar e criar metas

8. `/progresso`
   painel de evolucao

Resultado esperado:

- Navegacao previsivel.
- Sistema navegavel do dashboard ate o controle de estudo.

## Etapa 6: Views e Componentes Reaproveitaveis

Aqui nasce a parte visual, com foco em reuso.

Objetivo:

- Evitar repetir layout.
- Criar uma interface consistente.
- Facilitar crescimento da aplicacao.

### Componentes visuais iniciais

Em `templates/components/`, criar:

1. `header.html`
   cabecalho principal.

2. `sidebar.html`
   navegacao lateral.

3. `page_title.html`
   titulo e subtitulo padrao das telas.

4. `card.html`
   cartao reutilizavel para resumos e blocos.

5. `progress_card.html`
   cartao de progresso.

6. `goal_card.html`
   cartao de metas.

7. `session_card.html`
   cartao de sessoes recentes.

8. `empty_state.html`
   estado vazio para listas sem dados.

9. `form_field.html`
   campo padrao de formulario.

10. `alert.html`
    mensagens de feedback.

### Layouts iniciais

Em `templates/layouts/`, criar:

1. `base.html`
   layout principal.

2. `dashboard_layout.html`
   estrutura de paginas autenticadas ou internas.

### Paginas iniciais

Em `templates/pages/`, criar:

1. `home.html`
2. `trilhas.html`
3. `trilha_detail.html`
4. `modulo_detail.html`
5. `conteudo_detail.html`
6. `sessoes.html`
7. `metas.html`
8. `progresso.html`

Resultado esperado:

- Interface consistente.
- Reaproveitamento real de blocos.
- Menos duplicacao visual.

## Etapa 7: Persistencia e Estrutura de Dados

So depois do dominio estar claro, passamos para dados persistidos.

Objetivo:

- Transformar os objetos em modelos persistentes.
- Preservar a logica definida antes.

Ordem recomendada:

1. Converter `Usuario` em model persistente.
2. Converter `PlanoTreinamento`.
3. Converter `Trilha`.
4. Converter `Modulo`.
5. Converter `Conteudo`.
6. Converter `SessaoTreino`.
7. Converter `Meta`.
8. Converter `Progresso`.
9. Converter `Avaliacao`.

Resultado esperado:

- Estrutura de dados alinhada com o dominio.
- Persistencia sem improviso.

## Etapa 8: Dashboard de Evolucao

Depois da base pronta, criamos o painel principal.

Objetivo:

- Transformar dados em leitura pratica.
- Mostrar o que estudar e como esta a evolucao.

Blocos do dashboard:

1. Proximo conteudo sugerido.
2. Trilha em foco.
3. Tempo estudado na semana.
4. Metas da semana.
5. Sessoes recentes.
6. Modulos atrasados ou travados.
7. Resumo de progresso geral.

Resultado esperado:

- O sistema passa a orientar o estudo.
- O usuario entende rapidamente seu estado atual.

## Etapa 9: Refinamento e Escalabilidade

Depois do MVP funcionando, refinamos.

Objetivo:

- Melhorar manutencao.
- Preparar evolucoes futuras.

Evolucoes futuras:

1. Autenticacao.
2. Multiusuario.
3. Historico de revisao.
4. Recomendacao automatica de proximos conteudos.
5. Relatorios por periodo.
6. Tags por dificuldade ou categoria.
7. Priorizacao inteligente por desempenho.

## Ordem Real de Execucao Recomendada

Se formos executar sem dispersao, a ordem ideal e:

1. Estrutura do projeto em MVC.
2. Objetos do dominio.
3. Services de regra de negocio.
4. Controllers.
5. Rotas.
6. Layout base.
7. Componentes reutilizaveis.
8. Paginas principais.
9. Persistencia.
10. Dashboard de evolucao.

Essa ordem reduz retrabalho.

## Primeira Entrega Pratica

A primeira entrega concreta do projeto deve conter:

1. Aplicacao Flask iniciando corretamente.
2. Estrutura MVC criada.
3. Layout base funcionando.
4. Dashboard inicial renderizando.
5. Estrutura dos objetos principais definida.
6. Primeiro fluxo navegavel entre home e trilhas.

Isso ja cria uma base real para continuar.

## Decisao de Desenvolvimento

Vamos trabalhar assim:

1. Primeiro definimos corretamente.
2. Depois implementamos por camadas.
3. Cada camada nasce reutilizavel.
4. Tudo que for repetido vira componente.

## Proximo Passo

Com este roteiro definido, a proxima etapa pratica ideal e:

1. Criar a estrutura real de pastas do projeto em MVC.
2. Criar o `app.py` e o `config.py`.
3. Criar o `base.html`.
4. Criar os primeiros objetos do dominio.

Esse e o ponto certo para iniciar a implementacao.
