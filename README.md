# Feira das Profissoes 2026

Apresentacao web estatica sobre tecnologia, IA, seguranca da informacao, soft skills e carreira em produtos digitais para a Feira das Profissoes 2026.

## Como abrir

Abra o arquivo `index.html` diretamente no navegador.

No GitHub, este `README.md` aparece automaticamente na pagina inicial do repositorio.

## Solucao aplicada

Data da atualizacao: 26/05/2026

A aplicacao foi revisada e recebeu correcoes focadas em acessibilidade, experiencia mobile e atualizacao de conteudo.

### Correcoes realizadas

1. Banco de perguntas acessivel no mobile

Foi adicionado um botao `?` nos controles flutuantes para abrir o banco de perguntas em telas pequenas. Antes, o botao principal ficava oculto abaixo de 920px e a funcionalidade dependia do atalho `q`, que nao e pratico em celulares.

2. Modal com gerenciamento de foco

O modal de perguntas agora:

- salva o elemento que abriu o modal;
- move o foco para o botao "Fechar" ao abrir;
- prende a navegacao por `Tab` dentro do modal;
- fecha com `Escape`;
- devolve o foco ao elemento anterior ao fechar.

3. Atalhos de teclado mais seguros

Os atalhos globais de navegacao deixam de interferir em elementos interativos como botoes, links, `summary`, campos de formulario e conteudos editaveis. Quando o modal esta aberto, apenas `Escape` e `Tab` sao tratados globalmente.

4. Botao de tema mais acessivel

O botao "Tema" agora possui `aria-pressed` e `aria-label` dinamicos para indicar se o tema claro ou escuro esta ativo.

5. Fonte Microsoft atualizada para 2026

A referencia da Microsoft foi atualizada de Work Trend Index 2025 para Work Trend Index 2026, mantendo o conteudo mais coerente com a proposta da apresentacao.

6. Contador inicial corrigido

O contador flutuante inicial foi ajustado de `1 / 8` para `1 / 9`, refletindo a quantidade real de secoes com classe `.slide`.

## Arquivos alterados

- `index.html`: correcoes de CSS, HTML, JavaScript e referencia externa.
- `README.md`: atualizado para documentar a solucao aplicada.

## Validacao

- Busca estatica com `rg` para confirmar os pontos alterados.
- Validacao de sintaxe do JavaScript embutido usando o Node.js empacotado no ambiente Codex.
- Conferencia manual dos trechos alterados no HTML.

Observacao: a abertura visual via `file:///.../index.html` no navegador embutido foi bloqueada pela politica de seguranca do ambiente, entao a validacao visual automatizada nao foi executada aqui.

## Referencias

- World Economic Forum - Future of Jobs Report 2025: https://www.weforum.org/publications/the-future-of-jobs-report-2025/digest/
- ISC2 - 2025 Cybersecurity Workforce Study: https://www.isc2.org/Insights/2025/12/2025-ISC2-Cybersecurity-Workforce-Study
- Microsoft - 2026 Work Trend Index Annual Report: https://news.microsoft.com/annual-work-trend-index-2026
- GitHub - Octoverse 2025: https://octoverse.github.com/
