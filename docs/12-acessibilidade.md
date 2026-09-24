# Módulo 12 — Acessibilidade

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // Antes de começar

Acessibilidade não é um módulo isolado que você "faz por último" — é por isso que boa parte do que você precisa já apareceu, espalhado, nos módulos anteriores: `<label>` no Módulo 03, `<button>` em vez de `<div>` clicável no Módulo 03, hierarquia de headings no Módulo 02, foco visível mencionado no Módulo 04. Este módulo reúne tudo isso, explica o porquê com mais profundidade, e adiciona o que ainda faltava.

## // O que acessibilidade realmente significa aqui

> **ACESSIBILIDADE — EM PALAVRAS SIMPLES**
> É construir uma interface que funcione para o maior número possível de pessoas — incluindo quem não usa mouse, quem tem baixa visão, quem usa leitor de tela, quem tem dificuldade motora para cliques precisos.

Não é um recurso "extra" para um grupo pequeno de pessoas — é, na prática, testar se sua interface depende de uma única forma de uso (mouse, visão perfeita, precisão de clique) para funcionar.

## // Revisão: o que você já fez sem chamar de "acessibilidade"

| Prática | Módulo | Por que ajuda acessibilidade |
|---|---|---|
| HTML semântico (`<header>`, `<nav>`, `<main>`) | 03 | Leitores de tela navegam por essas regiões |
| `<label for="...">` conectado ao `id` do campo | 03 | Leitor de tela anuncia o rótulo certo ao focar o campo |
| `<button>` em vez de `<div onclick>` | 03 | Recebe foco pelo teclado e é anunciado como botão |
| `alt` em imagens | 02 | Leitor de tela descreve a imagem; aparece se a imagem falhar |
| Hierarquia de headings sem pular níveis | 02 | Leitores de tela navegam a página pela estrutura de headings |

## // O que ainda falta: contraste

> **CONTRASTE — EM PALAVRAS SIMPLES**
> É a diferença de luminosidade entre o texto e o fundo atrás dele. Contraste baixo demais torna o texto difícil de ler — não só para pessoas com baixa visão, mas para qualquer pessoa em uma tela com brilho fraco ou sob luz solar direta.

Existe um padrão de referência chamado WCAG (Web Content Accessibility Guidelines) que define níveis mínimos de contraste. Você não precisa calcular isso manualmente — existem ferramentas gratuitas de checagem de contraste (busque "WCAG contrast checker") onde você insere as duas cores do seu design system e recebe um veredito. Faça esse teste com a combinação principal de texto/fundo do seu projeto.

## // Tamanho de fonte e área de toque

- **Tamanho de fonte**: evite textos menores que 16px para conteúdo principal — tamanhos muito pequenos são difíceis de ler, especialmente em telas de celular.
- **Área de toque**: botões e links precisam de uma área clicável/tocável mínima — uma referência comum é aproximadamente 44x44px. Um botão visualmente pequeno, mas com padding suficiente, ainda pode ter uma área de toque adequada.

## // Foco e `focus-visible`

Você já viu, no Módulo 04, que o navegador mostra um contorno padrão ao focar um elemento pelo teclado (tecla Tab). É comum ver projetos removendo esse contorno por estética:

```css
/* NÃO FAÇA ISSO SEM SUBSTITUIR */
button:focus {
    outline: none;
}
```

> **QUEM É PREJUDICADO**
> Alguém que navega inteiramente pelo teclado — por preferência, ou por não conseguir usar mouse com precisão — depende desse contorno para saber onde está na página. Removê-lo sem colocar outra indicação visual no lugar deixa essa pessoa "perdida", sem saber qual elemento está ativo.

Se você quiser mudar a aparência do foco por motivos visuais, substitua por algo igualmente visível:

```css
/* Alternativa consciente */
button:focus-visible {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
}
```

`:focus-visible` (diferente de `:focus`) aplica o estilo só quando o navegador entende que o foco veio de navegação por teclado — não em todo clique de mouse. Isso evita o contorno aparecer em situações onde ele visualmente incomoda mais do que ajuda, sem removê-lo de onde ele é essencial.

## // Navegação por teclado — introdução

Teste rápido: pegue qualquer uma das suas três telas, clique em um espaço vazio da página, e navegue só com a tecla Tab (Shift+Tab para voltar). Pergunte:

- A ordem de navegação faz sentido (segue a ordem visual/lógica da tela)?
- Dá para chegar em todo elemento interativo (campos, botões, links) só com o teclado?
- O elemento focado está sempre visível?

Se qualquer resposta for "não", esse é um problema de acessibilidade real, não hipotético.

## // Estados que não dependem só de cor

```html
<!-- Só a cor indica erro (ruim) -->
<input class="campo-vermelho">

<!-- Cor + texto explícito (melhor) -->
<input class="campo-erro" aria-describedby="erro-email">
<span id="erro-email">E-mail inválido</span>
```

Pessoas com daltonismo (uma parcela relevante da população) podem não perceber a diferença entre um campo "normal" e um "com erro" se a única pista for a cor. Sempre acompanhe indicações de cor com texto, ícone, ou outra pista não dependente de cor.

## // Bom exemplo × mau exemplo

**Mau exemplo:**

```html
<div class="botao-fake" onclick="entrar()">Entrar</div>
```

**Bom exemplo:**

```html
<button type="submit">Entrar</button>
```

Já visto no Módulo 03 — repetido aqui porque é, sozinho, um dos erros de acessibilidade mais comuns e mais fáceis de evitar.

## // Aprofundamento

Para quem já tem o essencial consolidado:

- **Landmarks** — as tags semânticas (`<header>`, `<nav>`, `<main>`, `<footer>`) já funcionam como landmarks (marcos de navegação) para leitores de tela. Você pode reforçar isso com atributos ARIA (`role="navigation"`), mas geralmente as tags semânticas corretas já bastam.
- **ARIA, com cautela** — atributos `aria-*` (como `aria-label`, `aria-describedby`) complementam HTML quando a semântica nativa não é suficiente. Eles **não substituem** HTML semântico mal utilizado — adicionar `role="button"` em uma `<div>` não devolve o comportamento nativo de teclado que um `<button>` já tem de graça. Use ARIA para complementar, não para corrigir uma escolha de tag errada.
- **`prefers-reduced-motion`** — uma media query que detecta se a pessoa configurou o sistema para reduzir animações (importante para quem tem sensibilidade a movimento). Fica como referência para quando o projeto tiver animações.
- **Contraste WCAG** — nível AA é a referência mínima comum para projetos profissionais; nível AAA é mais rigoroso.

## // Erros comuns

| Erro | Por que acontece | Como corrigir |
|---|---|---|
| Remover `outline` do foco sem substituto | Parece "mais limpo" visualmente | Use `:focus-visible` com um estilo alternativo, nunca remova sem substituir |
| Cor como único indicador de estado | Parece suficiente visualmente | Acompanhe com texto ou ícone |
| `<div>` ou `<span>` fazendo papel de botão | Parece mais fácil de estilizar | Use `<button>` e estilize ele — CSS resolve toda a aparência |
| ARIA usada para "consertar" HTML errado | Parece um atalho | Corrija a tag primeiro; ARIA complementa, não substitui |

## // Prática guiada

1. Navegue pela tela de Login usando só o teclado (Tab, Shift+Tab, Enter). Anote qualquer ponto onde a navegação não fez sentido.
2. Verifique o contraste entre o texto e o fundo dos seus botões principais, usando uma ferramenta de checagem de contraste WCAG.
3. Confirme que nenhum estado (erro, sucesso, desabilitado) depende só de cor — adicione texto ou ícone onde faltar.

## // Pratique sozinho

> **DESAFIO**
> Adicione um estilo de `:focus-visible` customizado, usando as cores do seu design system, a todos os elementos interativos do projeto (botões, links, campos). Teste navegando por Tab em todas as três telas.

## // Aplicando no projeto da semana

1. Confirme HTML semântico, `label`/`for`, `button` (não `div`) e `alt` nas três telas (revisão do que já foi feito nos módulos anteriores).
2. Verifique contraste da paleta principal com uma ferramenta WCAG.
3. Adicione `:focus-visible` customizado.
4. Garanta que nenhum estado depende só de cor.
5. Commit: `git commit -m "Revisa e reforça acessibilidade nas três telas"`.

## // Checkpoint

> **ANTES DE SEGUIR, PENSE NISTO**
> Seu botão não tem nenhum estado de foco visível. Quem é prejudicado por isso, especificamente?

Resposta: qualquer pessoa navegando pelo teclado — seja por preferência, seja por não conseguir usar mouse com precisão (uma deficiência motora, por exemplo). Sem indicação visível de foco, essa pessoa perde a referência de onde está na página, tornando a navegação praticamente inutilizável.

## // Resumo do módulo

- [ ] Sei listar pelo menos cinco práticas de acessibilidade que já apareceram nos módulos anteriores.
- [ ] Sei o que é contraste e como checá-lo.
- [ ] Sei por que remover `outline` sem substituto prejudica navegação por teclado, e sei usar `:focus-visible`.
- [ ] Sei por que estados não deveriam depender só de cor.
- [ ] Testei minhas três telas navegando só com o teclado.

---

**Próximo módulo:** `13-componentizacao-e-temas.md` — reconhecendo padrões repetidos, e um primeiro tema claro/escuro.

`Material de Estudo // Coffee & Code`
