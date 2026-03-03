### 1. Google Maps Platform (O Gigante Confortável)
É a escolha padrão da indústria, mas é uma faca de dois gumes para quem está começando com recursos limitados.

Cadastro e Start: O Google exige que você crie um projeto no Google Cloud e vincule um cartão de crédito válido logo de cara. Eles te dão 200 dólares mensais de crédito recorrente.

Uso no Código: É estupidamente fácil. No Expo/React Native, a biblioteca react-native-maps usa o Google Maps por padrão no Android. Documentação infinita, vídeos no YouTube aos milhares e endpoints de geocodificação perfeitos.

Evolução do App: O problema começa quando o MVP dá certo. A API de Rotas (Directions) e Autocomplete do Google são caras. Se o app viralizar ou o volume de entregas subir rápido, aqueles 200 dólares evaporam em dias, e a cobrança no cartão começa a doer pesado.

### 2. Mapbox (O Equilíbrio Perfeito para Startups)
O Mapbox foi criado exatamente para competir com o monopólio e os preços altos do Google. É a escolha preferida das novas gerações de aplicativos.

Cadastro e Start: Muito amigável para desenvolvedores. Você cria a conta, pega a chave de API e começa a codar. A cota gratuita é massiva (100.000 visualizações de mapa grátis por mês) e até 100.000 requisições de rotas (Directions) gratuitas.

Uso no Código: Tem um SDK próprio maravilhoso para React Native (@rnmapbox/maps). Permite um nível de personalização visual absurdo (você pode fazer o mapa ficar dark mode puro, mudar a cor das ruas, tirar os nomes de estabelecimentos concorrentes do mapa, etc.).

Evolução do App: Quando você ultrapassa o limite gratuito, o valor cobrado por milhar de requisições é significativamente mais barato que o Google. É uma transição financeira muito mais saudável.

### 3. OpenStreetMap (A Rota "Faça Você Mesmo")
O OSM é a "Wikipedia dos Mapas". Os dados são abertos e mantidos pela comunidade.

Cadastro e Start: Zero burocracia, não tem API Key oficial centralizada. Você simplesmente aponta para os servidores públicos do OSM para puxar as imagens do mapa (Tiles).

Uso no Código: Aqui o jogo engrossa. No ambiente web (React/Next.js), o OSM é fácil de usar com a biblioteca Leaflet. Mas no ambiente Mobile (Expo/React Native), usar OSM nativamente exige bibliotecas de terceiros menos mantidas ou gambiarras com WebViews. Além disso, os servidores públicos de OSM bloqueiam quem faz muitas requisições por segundo.

Evolução do App: É aqui que a mágica da infraestrutura entra. Para usar rotas e geolocalização no OSM para um sistema de Micro SaaS sem pagar licenças, você pode subir o motor OSRM (Open Source Routing Machine) dentro de uma VPS própria (Linux). Você clona os dados do Brasil inteiro no seu servidor. A partir daí, o custo é fixo (o preço da sua VPS), não importa se você faz mil ou 1 milhão de requisições de rotas por dia.