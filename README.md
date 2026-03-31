# GeoObras ARTESP R1

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/pt-BR/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
[![Leaflet](https://img.shields.io/badge/Leaflet-199900?logo=leaflet&logoColor=white)](https://leafletjs.com/)
[![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?logo=chart.js&logoColor=white)](https://www.chartjs.org/)

**GeoObras ARTESP R1** é uma aplicação web de interface única (SPA) projetada para facilitar a gestão, visualização e edição da Programação Anual de Obras e Revitalização, em conformidade com o Schema R0 da ARTESP.

A aplicação combina um editor de dados tabular avançado com um mapa interativo (Leaflet), permitindo a associação de informações de obras a geometrias geoespaciais (pontos, linhas e polígonos) de forma intuitiva e eficiente. Além disso, agora inclui visualizações analíticas e um registro de alterações para um controle ainda maior dos dados.

> **Nota:** Este é um projeto de código aberto desenvolvido para demonstrar a estrutura e as funcionalidades de uma ferramenta de gestão de dados geoespaciais para o setor rodoviário. Ele **não é uma ferramenta oficial** da ARTESP.

## 🌟 Principais Funcionalidades

- **📊 Dashboard Analítico Avançado:** Visualize estatísticas gerais sobre as obras, incluindo totais, distribuição por programa e lote, identificação de obras sem geometria e uma **Linha do Tempo (Gantt)** para o planejamento de prazos.
- **🗺️ Editor de Obras Integrado:** Edite dados diretamente em uma tabela robusta com recursos de busca, filtragem, classificação e **validação em tempo real** baseada no schema ARTESP R0.
- **📍 Mapeamento Visual Multi-camadas:** Adicione, edite e associe geometrias (pontos, linhas, polígonos) às obras usando os controles de desenho do Leaflet. Explore diferentes visualizações com **9 opções de mapas base** (Google, Carto, Esri, OpenTopoMap).
- **📥/📤 Importação e Exportação:** Importe arquivos GeoJSON e exporte seus dados nos formatos **GeoJSON** (validado) e **CSV**.
- **💾 Salvamento Local:** Dados são automaticamente salvos no `localStorage` do navegador, permitindo retomar o trabalho a qualquer momento.
- **🔄 Histórico de Ações e Desfazer/Refazer:** Sistema completo de **Undo/Redo** e um **registro de alterações** por obra, permitindo rastrear quem mudou o quê e quando.
- **🎨 Interface Responsiva e Moderna:** Design limpo e profissional com sidebar navegável e **recolhível**, notificações (toast), cards de detalhes flutuantes e temas claros.
- **🏷️ Gerenciamento de Tags:** Edição visual e simplificada para campos de múltiplos valores, como `local`, usando seletores de tags ao invés de campos de texto puros.
- **📜 Registro de Atividades:** Visualize o histórico de todas as alterações feitas em cada obra diretamente no card de detalhes.

---

## 📋 Pré-requisitos

- Navehador web moderno (Chrome, Firefox, Edge, Safari) com JavaScript habilitado.
- Acesso à internet para carregar os mapas base (tiles do OpenStreetMap/Esri/Google).

---

## ⚙️ Instalação e Uso Local

Esta aplicação não requer um servidor complexo ou dependências de Node.js. Ela é um arquivo HTML estático que pode ser executada localmente ou servida por qualquer servidor web estático.

### Opção 1: Executar Localmente (Recomendado para Testes)

1.  **Clone ou baixe este repositório:**
    ```bash
    git clone https://github.com/seu-usuario/geoobras-artesp-r1.git
    cd geoobras-artesp-r1
    ```

2.  **Use uma extensão de servidor local:**
    A forma mais simples é usar uma extensão como o [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) no Visual Studio Code. Com a extensão instalada, clique com o botão direito no arquivo `index.html` e selecione "Open with Live Server".

3.  **Abra no navegador:**
    A aplicação será aberta automaticamente em uma nova aba no seu navegador, geralmente no endereço `http://127.0.0.1:5500`.

### Opção 2: Servir com Python (Navegadores mais restritos)

Alguns navegadores bloqueiam requisições AJAX (`fetch`) quando o arquivo é aberto diretamente do sistema de arquivos (`file://`). Se você encontrar problemas, use um servidor simples:

1.  Com o Python 3 instalado, naveve até a pasta do projeto:
    ```bash
    cd /caminho/para/geoobras-artesp-r1
    ```

2.  Inicie o servidor HTTP:
    ```bash
    python -m http.server
    ```

3.  Abra o navegador e acesse `http://localhost:8000`.

---

## 🗂️ Guia de Uso

A interface é dividida em três principais seções, acessíveis pela barra lateral esquerda, que agora pode ser recolhida para ganhar mais espaço na tela.

### 1. Dashboard
O painel inicial oferece uma visão geral e análises dos dados:
- **Cards Estatísticos:** Total de obras, obras com e sem geometria, e número de lotes distintos.
- **Gráficos de Barras:** Visualize a distribuição das obras por `Programa` e por `Lote`.
- **🆕 Linha do Tempo (Gantt):** Um gráfico interativo que visualiza a duração e o período de todas as obras com datas de início e fim válidas, permitindo uma clara visualização do cronograma.
- **Tabela de Recentes:** Lista as últimas 8 obras cadastradas ou atualizadas, com um link rápido para o editor.

### 2. Editor de Obras
O coração da aplicação, onde você gerencia os dados.

#### Tabela de Dados
- **Edição Direta:** Clique em qualquer célula para editar seu valor. A alteração é salva automaticamente e validada em tempo real. Campos inválidos são destacados em vermelho.
- **Busca Global:** Use a barra de busca no topo para filtrar linhas com base em qualquer termo.
- **Filtros por Coluna:** Clique no botão "Filtros" para exibir uma linha de filtros individuais para cada coluna.
- **Classificação:** Clique no cabeçalho de qualquer coluna para ordenar os dados (ascendente/descendente).
- **Colagem em Lote:** Copie dados de uma planilha (Excel/Google Sheets) e cole diretamente na tabela para preencher várias células de uma vez.
- **🆕 Edição de Tags:** Para o campo `local` e no modal de edição, clique nos tags para adicionar ou remover locais de forma visual, evitando erros de digitação.
- **Ações por Linha:**
    - **Editar:** Abre um modal com todos os campos da obra para edição.
    - **🚨 `geo`:** Indica que a obra não possui geometria. Clique para entrar no "modo de associação". O próximo desenho que você fizer no mapa será vinculado a esta obra.
    - **Excluir:** Remove a obra e sua geometria associada.

#### Mapa Interativo
- **Visualização:** As obras com geometria são exibidas no mapa. Clique em um elemento para destacar a linha correspondente na tabela e abrir o card de detalhes.
- **🆕 Múltiplos Mapas Base:** Alterne entre diferentes camadas de mapa (Google Roadmap, Satélite, Híbrido, Terreno, CartoDB, Esri, etc.) usando o seletor de camadas no canto superior direito do mapa.
- **Controles de Desenho:**
    - **Point (Ponto):** Para marcar locais específicos (ex: pontes, viadutos).
    - **LineString (Linha):** Para trechos contínuos (ex: recapeamento, sinalização).
    - **Polygon (Polígono):** Para áreas (ex: canteiro de obras, parks).
- **Editar/Excluir Geometrias:** Selecione a geometria no mapa e use as ferramentas de edição/remoção do painel de controle do Leaflet Draw.

#### Card de Detalhes Flutuante
Clique em uma linha da tabela ou em uma geometria no mapa para abrir um card com informações detalhadas sobre a obra.
- **Campos Editáveis:** A maioria dos campos pode ser editada diretamente no card.
- **🆕 Visualização de Histórico:** Um novo painel mostra o registro das últimas alterações feita na obra, com data, hora, campo modificado e os valores antigos e novos.
- **Cópia de WKT:** Botão para copiar a geometria em formato WKT para a área de transferência.
- **🆕 Minimizar:** Minimize o card para um cabeçalho compacto para ganhar espaço de tela.
- **Arrastar e Redimensionar:** Mova o card de lugar ou ajuste seu tamanho para melhor visualização.

### 3. Configurações
Personalize o comportamento do aplicativo:
- **Aparência da Tabela:** Ajuste o tamanho da fonte e a altura das linhas.
- **Auto-salvamento:** Ative/desative o salvamento automático e ajuste o intervalo.
- **Limpeza de Dados:** Apague todos os dados salvos no navegador (`localStorage`).
- **Validação ARTESP:** Ative/desative a validação de formatos específicos (ex: Lote, Rodovia) e a exigência de geometria na exportação.

---

## 🧩 Estrutura do Projeto

O projeto é intencionalmente simples e contém apenas um arquivo principal:

```
geoobras-artesp-r1/
├── index.html          # O arquivo único da aplicação (HTML, CSS e JS)
├── README.md           # Este arquivo de documentação
└── LICENSE             # Arquivo de licença (opcional, mas recomendado)
```

Todo o código JavaScript, CSS e HTML está contido dentro do `index.html`. Isso facilita a distribuição e o deploy, tornando a aplicação uma verdadeira "Single Page Application" estática.

---

## 🤝 Como Contribuir

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma *issue* para relatar bugs, sugerir novas funcionalidades ou enviar um *pull request* com melhorias.

**Passos para Contribuir:**
1. Faça um *fork* deste repositório.
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`).
3. Comite suas mudanças (`git commit -m 'Adiciona nova funcionalidade'`).
4. Faça o push para a branch (`git push origin feature/nova-funcionalidade`).
5. Abra um *Pull Request*.

---

## 🛣️ Sobre o Schema ARTESP R0

A aplicação foi desenvolvida para seguir a estrutura de dados definida no Schema R0 da ARTESP para a Programação Anual de Obras. Os principais campos e suas validações foram implementados para garantir a integridade dos dados:

- **Lote:** Validação com a lista de lotes permitidos (`L01`, `L06`, etc.).
- **Rodovia:** Validação por expressão regular para diferentes formatos (ex: `SP-123`, `SPM12345A`).
- **Programa:** Validação com os valores (`REVIT`, `CAPEX`, `NS`).
- **Unidade:** Validação com a lista de unidades de medida.
- **Local:** Validação com a lista de códigos de localização, suportando múltiplos valores separados por `;`.
- **Geometria:** Opcional durante a edição, mas sua presença pode ser exigida na exportação.

Para uma referência completa, consulte a [documentação oficial do schema]([https://github.com/seu-usuario/geoobras-artesp-r1/blob/main/docs/SCHEMA_ARTESP_R0.md](https://dadosabertos.artesp.sp.gov.br/dataset/programacao-de-obras/resource/cd8f9bb4-3a78-4c7f-99c8-f289da731e10).
