# Revisao da aplicacao

Data da revisao: 26/05/2026

## Escopo

Aplicacao revisada: `index.html`

O projeto e uma apresentacao web estatica para a Feira das Profissoes 2026, com HTML, CSS e JavaScript embutidos em um unico arquivo. A revisao considerou estrutura, navegacao, responsividade, acessibilidade, conteudo, manutencao e referencias externas.

## Resumo executivo

A aplicacao esta funcionalmente simples e bem adequada ao formato de apresentacao: nao depende de build, possui layout responsivo, navegacao por botoes/teclado, tema claro/escuro, modal de perguntas e modo de impressao.

Os principais pontos de melhoria estao em acessibilidade e experiencia em mobile. O banco de perguntas fica oculto em telas menores, o modal nao gerencia foco, e o atalho global de teclado pode interferir em controles nativos como botoes e accordions. Tambem ha oportunidades de manter o conteudo mais alinhado a 2026, especialmente nas referencias de mercado.

## Achados

### Alta prioridade

1. Banco de perguntas fica inacessivel para usuarios mobile

No CSS responsivo, os botoes com `.hide-sm` sao ocultados abaixo de 920px. Isso remove o botao "Perguntas dos alunos" da interface mobile, e nao existe outro controle visivel para abrir o modal. O atalho `q` ainda existe, mas nao e descobrivel nem pratico em celular.

Impacto: usuarios em celular/tablet perdem uma funcionalidade importante da apresentacao.

Recomendacao: manter um botao compacto para perguntas no controle flutuante ou criar um menu/icone acessivel em mobile.

Arquivos/linhas relacionadas: `index.html` linhas 534 e 491.

2. Modal de perguntas nao gerencia foco

O modal usa `role="dialog"` e `aria-modal="true"`, mas ao abrir nao move o foco para dentro do modal, nao prende a navegacao por Tab e nao restaura o foco ao botao que abriu o modal quando fecha.

Impacto: usuarios de teclado e leitores de tela podem continuar navegando por elementos ao fundo, perdendo contexto.

Recomendacao: ao abrir, salvar o elemento ativo, focar o botao "Fechar" ou o titulo do modal, implementar focus trap enquanto o modal estiver aberto e restaurar o foco no fechamento.

Arquivos/linhas relacionadas: `index.html` linhas 850, 932 e 936.

### Media prioridade

3. Atalhos globais interferem em elementos interativos

O listener global de `keydown` captura `Space`, `ArrowRight`, `ArrowLeft`, `PageDown` e `PageUp` em todo o documento. Isso pode conflitar com a ativacao nativa de botoes, accordions (`summary`) e outros elementos focaveis, principalmente dentro do modal.

Impacto: o usuario pode tentar abrir um item de FAQ com espaco e acabar avancando slide.

Recomendacao: ignorar atalhos quando `event.target` estiver dentro de `button`, `a`, `summary`, `input`, `textarea`, `select`, `[contenteditable]` ou quando o modal estiver aberto, exceto `Escape`.

Arquivos/linhas relacionadas: `index.html` linhas 940 a 950.

4. Indicacao visual e semantica do tema e limitada

O botao "Tema" alterna entre claro e escuro, mas nao informa o estado atual para tecnologias assistivas e nao comunica se o proximo clique vai ativar ou desativar o modo claro.

Impacto: baixa previsibilidade para usuarios de leitor de tela e menor clareza para apresentadores.

Recomendacao: adicionar `aria-pressed`, atualizar o texto ou `aria-label` dinamicamente e considerar uma indicacao visual de estado.

Arquivos/linhas relacionadas: `index.html` linhas 536 e 927.

5. Conteudo se apresenta como 2026, mas parte das fontes ja tem versoes/atualizacoes de 2026

A apresentacao esta posicionada como conteudo de 2026, mas a secao de fontes usa majoritariamente referencias de 2025. Isso e aceitavel para WEF Future of Jobs 2025 e GitHub Octoverse 2025, mas a Microsoft ja possui o Work Trend Index 2026 publicado, o que pode deixar a narrativa de IA/agentes menos atual.

Impacto: o material pode parecer menos atualizado em uma palestra de 2026.

Recomendacao: revisar a secao de fontes e, quando fizer sentido, incluir ou substituir pela referencia Microsoft Work Trend Index 2026. Manter o WEF 2025 e valido porque o relatorio cobre o periodo 2025-2030.

Referencias verificadas:

- World Economic Forum - Future of Jobs Report 2025: https://www.weforum.org/publications/the-future-of-jobs-report-2025/digest/
- ISC2 - 2025 Cybersecurity Workforce Study: https://www.isc2.org/Insights/2025/12/2025-ISC2-Cybersecurity-Workforce-Study
- Microsoft - 2026 Work Trend Index Annual Report: https://news.microsoft.com/annual-work-trend-index-2026
- GitHub - Octoverse 2025: https://octoverse.github.com/

### Baixa prioridade

6. Contadores textuais podem gerar pequena confusao

Os slides de conteudo usam marcadores como "1 de 7" ate "7 de 7", mas a pagina possui tambem os slides "Inicio" e "Fontes". O contador flutuante calcula todos os `section.slide`, entao a experiencia real e de 9 secoes.

Impacto: pequena inconsistencia entre a numeracao editorial e a navegacao real.

Recomendacao: decidir se "Inicio" e "Fontes" fazem parte da contagem. Se fizerem, padronizar para 1 de 9. Se nao fizerem, ajustar o contador flutuante para contar apenas slides principais.

Arquivos/linhas relacionadas: `index.html` linhas 544, 576, 604, 630, 656, 689, 730, 771, 812 e 845.

7. JavaScript, CSS e HTML estao todos no mesmo arquivo

Para uma apresentacao estatica pequena, isso funciona bem. Porem, conforme o conteudo crescer, a manutencao de estilos, interacoes e conteudo em um unico arquivo ficara mais dificil.

Impacto: maior custo para evoluir a aplicacao, revisar alteracoes e reaproveitar componentes.

Recomendacao: se o projeto continuar crescendo, separar em `styles.css` e `script.js`, mantendo o HTML focado em estrutura e conteudo.

## Pontos positivos

- Aplicacao simples de distribuir: basta abrir o HTML.
- CSS responsivo cobre bem a mudanca de grids para uma coluna.
- Existe suporte a impressao/PDF via `@media print`.
- Links externos usam `target="_blank"` com `rel="noopener"`.
- A navegacao por teclado existe e cobre setas, PageUp/PageDown, espaco e Escape.
- O conteudo tem boa progressao narrativa para apresentacao educacional.

## Validacao realizada

- Estrutura do repositorio verificada: apenas `index.html`.
- Leitura estatica do HTML, CSS e JavaScript.
- Busca de pontos sensiveis com `rg`.
- Conferencia web das principais referencias externas.

Observacao: a tentativa de abrir `file:///C:/projetos/FIEB-2026/FIEB-2026/index.html` no navegador embutido foi bloqueada pela politica de seguranca do ambiente. Por isso, esta revisao nao inclui validacao visual automatizada no navegador.

## Recomendacao de proxima iteracao

Priorizar os tres ajustes que mais melhoram a experiencia real:

1. Expor o banco de perguntas tambem no mobile.
2. Corrigir foco e acessibilidade do modal.
3. Ajustar os atalhos globais para nao interferirem em controles interativos.
