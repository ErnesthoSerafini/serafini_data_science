# Mamadas do Ravi

App web (PWA) para registrar mamadas e medicamentos de um bebê, com histórico por dia, cálculo automático da próxima fórmula e das próximas doses de Colic Calm/Simeticona, e exportação do histórico em `.txt`.

Convertido a partir de um [artifact do Claude](https://claude.ai) para funcionar como aplicativo independente, salvando os dados no `localStorage` do navegador.

## Como usar

Abra `index.html` em qualquer navegador — não requer servidor nem instalação de dependências. Também pode ser hospedado como site estático (ex.: GitHub Pages) e instalado na tela inicial do celular como app (PWA), incluindo uso offline.

## Estrutura

- `index.html` — aplicativo completo (HTML/CSS/JS, sem dependências externas)
- `manifest.json` — manifesto do PWA
- `sw.js` — service worker para cache offline
- `icon.svg` — ícone do app

## Observação

Os dados ficam salvos apenas no navegador/dispositivo utilizado (não há sincronização entre dispositivos). Use o botão **Exportar** para salvar um backup do histórico.
