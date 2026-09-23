# Planeamento da versão 2

Registo das decisões tomadas antes de escrever o código da segunda versão do site.
A versão 1 (lateral à esquerda, fundo claro) já estava publicada em GitHub Pages; o objetivo
desta fase foi mudar a apresentação sem mudar o conteúdo.

## Objetivo

Paleta própria, header centrado com a foto, página em coluna única, contactos com ícones
e botão para descarregar o CV em PDF — tudo em HTML e CSS, com o que foi dado no módulo.

Restrição que me impus: **só técnicas que consiga explicar**. Ficaram de fora coisas que
apareciam nas referências visuais mas que não foram dadas nas aulas (`::after`, animações
ligadas ao scroll, `:not()`, fontes externas).

## Paletas consideradas

A ideia inicial era azul-marinho com letras castanhas. Testei o contraste e não funciona:
marinho e castanho são ambos escuros, e o texto ficava abaixo de 3:1 — ilegível. A solução
foi manter o castanho como **cor de destaque** (bronze) e usar uma cor clara para o texto.

| Paleta | Fundo | Texto | Destaque | Sensação |
|---|---|---|---|---|
| **Marinho & Bronze** (escolhida) | `#0f1b33` | areia `#ece6d9` | bronze `#d9ab6a` | quente e sóbria; a ideia original com o castanho no sítio certo |
| Marinho & Gelo | `#0b1a2e` | gelo `#dfe8f3` | turquesa `#5fd3c4` | mais "tech", fria |
| Papel & Marinho | papel `#f5f1ea` | marinho `#1f2a44` | terracota `#9a5122` | página clara com faixa marinho; a melhor para imprimir |

### Contrastes medidos (WCAG)

Mínimo exigido para texto normal: **4,5 : 1**. Todos os pares usados passam.

| Par | Rácio |
|---|---|
| texto `#ece6d9` sobre fundo `#0f1b33` | 13,8 : 1 |
| texto sobre cartões `#172647` | 12,0 : 1 |
| cinza `#aaa79b` sobre fundo | 7,1 : 1 |
| bronze `#d9ab6a` sobre fundo | 8,2 : 1 |
| marinho sobre bronze (texto no hover) | 8,2 : 1 |

## Decisões

| Decisão | Escolha | Porquê |
|---|---|---|
| Paleta | Marinho & Bronze | ver acima — contraste verificado em todos os pares |
| Layout | coluna única, 880px, sem grid no `body` | header, nav, main e rodapé empilham-se sozinhos; o Grid passa para dentro das secções, onde há mesmo duas dimensões |
| Largura | 880px em vez de 1200px | em coluna única, 1200px dava linhas de ~150 caracteres |
| Header | faixa a toda a largura + `div` interior centrado | o `header` pinta a faixa, o `div` limita e centra — um elemento não pode fazer as duas coisas |
| Foto | 160px, redonda, com anel bronze | vem da lateral para o topo; 200px ficava pesado no header |
| Contactos | 6 pílulas com ícones SVG inline | passam do `aside` para o `header`; inclui telefone, localização e PDF |
| Lateral (`aside`) | desaparece | o conteúdo deixa de estar "ao lado" — passa a `section` do `main` |
| Competências | `section#competencias` com `h3` para línguas e pontos fortes | uma secção, um `h2`; o resto são subsecções |
| Menu | fixo ao fazer scroll (`position: sticky`) | página comprida; obriga a `scroll-margin-top` nas secções |
| Experiência | Grid `1fr auto` — data à direita do título | o caso mais simples de duas colunas de tamanhos diferentes |
| Formação e línguas/pontos | uma classe `.grelha-2` (Grid `1fr 1fr`) nos dois sítios | uma regra, dois usos |
| Projetos | `repeat(auto-fit, minmax(240px, 1fr))` | adapta-se sozinho, sem media query |
| Mobile | só o que muda: título, foto, data por baixo, grelhas a 1 coluna | o layout base já é vertical, por isso a media query fica mais curta que na v1 |
| Extras | favicon SVG, `download` no PDF, `rel="noopener"` | elementos pequenos e fáceis de explicar |

## Esboços

- `esboco-v2-desktop.png` — estrutura final anotada com as técnicas de cada bloco
- `esboco-v2-mobile.png` — o que muda abaixo de 767px
- `stitch-v2-desktop.png` · `stitch-v2-mobile.png` — referência visual gerada a partir destas decisões (não é a versão final)

## Resultado

Ver `site-versao-1.png` e `site-versao-2.png` para o antes e depois, e `validacao-html-melhorias.png`
para a validação W3C da versão nova.
