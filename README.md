# CobraJuris — Código-fonte

Cobrança automatizada para empresas: painel, devedores, importação de planilha, mensagens, agendamentos e relatórios.

## Como abrir

Não precisa de instalação nem servidor. Duas opções:

1. **Duplo-clique em `index.html`** — abre direto no navegador.
2. **VS Code + extensão "Live Server"** — clique direito em `index.html` → "Open with Live Server" (recomendado ao editar, recarrega sozinho).

O app roda inteiramente no navegador (React via CDN, sem build/`npm install`). Os dados ficam salvos no `localStorage` do navegador.

## Estrutura de pastas

```
index.html          ← abra este arquivo — ponto de entrada do site
README.md
src/
  styles.css        ← TODO o visual: cores, fontes, espaçamento e estilo de cada tela
  ui-kit.js          ← ícones (SVG) + componentes de interface (Button, Input, Badge, StatCard, Table…)
  data-store.js      ← dados de exemplo + estado da aplicação (localStorage) + leitor de planilha (CSV/XLSX)
  screens.js         ← todas as telas do produto (login, painel, devedores, importação, mensagens, agendamentos, relatórios, configurações, chat)
  app.js             ← inicialização: monta o App na página
  fonts/             ← arquivos das fontes (Outfit, Work Sans, IBM Plex Mono)
```

Apenas 5 arquivos de código — organizados por responsabilidade, não por tela — para ficar fácil de navegar no VS Code.

**Nota técnica:** `ui-kit.js`, `screens.js` e `app.js` usam JSX (a sintaxe do React), então o `index.html` já os carrega embutidos em blocos `<script type="text/babel">` — isso evita um bloqueio do navegador que impede abrir esses arquivos por duplo-clique (`file://`). Os arquivos em `src/` continuam sendo a fonte de verdade para leitura e edição; se você editar `screens.js`, por exemplo, copie o trecho alterado também para dentro do `index.html` (ou use o Live Server, que não tem essa limitação e permite manter tudo em arquivos separados).

## Onde editar o quê

- **Cores e visual** → `src/styles.css`. As cores da marca estão no topo, em `:root` (`--green-600` é o verde principal). Mude ali e o site inteiro atualiza.
- **Textos e comportamento de uma tela** → `src/screens.js`. Cada tela é uma função (`DashboardScreen`, `DevedoresScreen`, `MensagensScreen`, etc.) — use Ctrl+F para achar.
- **Dados de exemplo (devedores, modelos de mensagem)** → `src/data-store.js`, no topo (`CJ_DEVEDORES`, `CJ_TEMPLATES`).
- **Ícones novos** → `src/ui-kit.js`, no objeto `ICON_PATHS`.

## Sobre este projeto

Este é um protótipo navegável (front-end apenas) — não envia WhatsApp/SMS/e-mail de verdade e não tem banco de dados. Para virar produto real é preciso conectar um back-end (banco de dados + APIs de disparo).
