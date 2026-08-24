# Diário do Ravi

App web (PWA) para registrar mamadas, medicamentos e crescimento de um bebê: histórico por dia com edição/exclusão, cálculo automático da próxima fórmula e das próximas doses de medicamentos (personalizáveis), acompanhamento de peso/altura com gráfico de evolução por idade em meses, e exportação do histórico em `.txt`.

Convertido a partir de um [artifact do Claude](https://claude.ai) para funcionar como aplicativo independente, salvando os dados no `localStorage` do navegador.

## Como usar

Abra `index.html` em qualquer navegador — não requer servidor nem instalação de dependências. Também pode ser hospedado como site estático (ex.: GitHub Pages) e instalado na tela inicial do celular como app (PWA), incluindo uso offline.

O nome exibido no app e a data de nascimento (usada para calcular a idade em meses no gráfico de crescimento) podem ser ajustados a qualquer momento pelo botão **⚙** no topo da tela.

## Sincronização entre celulares (opcional)

Por padrão os dados ficam só no navegador/dispositivo utilizado. Para que dois celulares (ex.: pai e mãe) vejam os mesmos registros em tempo real, é possível ligar o app a um banco Firebase Realtime Database gratuito:

1. Crie um projeto e um Realtime Database em [console.firebase.google.com](https://console.firebase.google.com) e registre um app Web para obter o objeto `firebaseConfig`.
2. Preencha a constante `firebaseConfig` no início do `<script>` de `index.html` com esses valores (fica vazia por padrão, `{}`, o que mantém o app 100% local).
3. Nas regras do Realtime Database, use algo como:
   ```json
   { "rules": { "families": { "$familyId": { ".read": true, ".write": true } } } }
   ```
4. No app, abra **⚙ → Sincronização entre celulares → Criar sincronização** em um aparelho, e **Já tenho um código** no outro, usando o código gerado.

Sem o `firebaseConfig` preenchido, essa seção mostra "Sincronização ainda não configurada" e o app continua funcionando 100% offline.

## Estrutura

- `index.html` — aplicativo completo (HTML/CSS/JS, sem dependências externas além do SDK do Firebase quando a sincronização está configurada)
- `manifest.json` — manifesto do PWA
- `sw.js` — service worker para cache offline
- `icon.svg` — ícone do app

## Observação

Sem sincronização configurada, os dados ficam salvos apenas no navegador/dispositivo utilizado. Use o botão **Exportar** a qualquer momento para salvar um backup do histórico em `.txt`.
