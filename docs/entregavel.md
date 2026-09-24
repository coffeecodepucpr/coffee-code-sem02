# Entregável — Semana 02

`SEM 02 // Interface Web — Parte 1: Layout`

Use este arquivo como checklist final antes de considerar a Semana 02 concluída. Ele reúne o que é **obrigatório** — os desafios extras em `desafios.md` são opcionais.

## // O que você deve ter em mãos agora

Se você seguiu os módulos em ordem, seu repositório agora deve ter, além de tudo o que veio da Semana 01: três páginas HTML (Login, Dashboard, Perfil), completas, estilizadas, responsivas e conectadas a um `styles.css` compartilhado, construído em cima do design system definido na Semana 01.

## // Checklist do entregável

### > Estrutura

- [ ] `login.html`, `dashboard.html` e `perfil.html` existem e abrem sem erros.
- [ ] As três páginas compartilham o mesmo `css/styles.css`.
- [ ] A estrutura de pastas está organizada (`css/`, `docs/`, arquivos HTML na raiz ou em `pages/`).

### > HTML

- [ ] Cada página tem a estrutura mínima completa (`<!DOCTYPE>`, `<html lang>`, `<head>` com `charset` e `viewport`, `<title>` específico).
- [ ] HTML semântico usado corretamente (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` onde fizer sentido).
- [ ] Hierarquia de headings sem pular níveis.
- [ ] Formulário de Login com `<label>` conectado a cada campo via `for`/`id`.
- [ ] Toda ação clicável usa `<button>`, nunca `<div onclick>`.
- [ ] Toda imagem tem `alt` descritivo.

### > CSS / Layout

- [ ] `box-sizing: border-box` aplicado globalmente.
- [ ] `styles.css` conectado corretamente nas três páginas (caminhos relativos corretos).
- [ ] Navbar (ou equivalente) usa Flexbox, consistente nas três telas.
- [ ] Grid de cards do Dashboard usa CSS Grid.
- [ ] Cores, tipografia e espaçamento vêm de CSS Custom Properties em `:root`, não de valores soltos espalhados pelo código.

### > Responsividade

- [ ] `<meta name="viewport">` presente nas três páginas.
- [ ] Layout testado em pelo menos três larguras (~375px, ~768px, ~1200px).
- [ ] Nenhuma rolagem horizontal indesejada em nenhuma das larguras testadas.
- [ ] Abordagem mobile-first usada nas media queries.

### > Consistência

- [ ] Button, Card, Input e Navbar usam a mesma classe CSS em todo lugar que aparecem.
- [ ] `/docs/design-system.md` atualizado com a seção de implementação (tokens usados no código).

### > Acessibilidade

- [ ] Contraste de texto/fundo verificado na paleta principal.
- [ ] `:focus-visible` visível em elementos interativos (nenhum `outline: none` sem substituto).
- [ ] Nenhum estado depende só de cor para ser identificado.
- [ ] Navegação completa por teclado testada em pelo menos uma das telas.

### > Projeto

- [ ] As três telas do protótipo do Figma (Semana 01) estão implementadas, mesmo que com ajustes.
- [ ] Histórico de commits organizado, com mensagens claras, refletindo o progresso módulo a módulo.

## // O que NÃO é esperado nesta semana

Para deixar claro e evitar ansiedade desnecessária:

- Não é esperado nenhum backend, banco de dados ou autenticação real.
- Não é esperado JavaScript funcional (um botão de tema manual, por exemplo, é desafio opcional, não obrigatório).
- Não é esperada perfeição visual pixel a pixel comparado ao Figma — pequenos ajustes de espaçamento e proporção são normais e esperados ao migrar de um design estático para HTML/CSS real.
- Não é esperado que Tailwind tenha sido usado — CSS puro é uma entrega igualmente válida.

> **A BELEZA NÃO É O CRITÉRIO**
> Um projeto com estrutura simples, HTML semântico correto, CSS organizado em variáveis e responsividade funcional vale mais, nesta avaliação, do que um projeto visualmente elaborado mas com `<div>` genérica no lugar de `<button>`, sem `label`, ou que quebra completamente no celular. Estrutura e fundamentos são o que está sendo avaliado esta semana — não estética.

## // Como revisar antes de entregar

> **O TESTE MAIS IMPORTANTE DESTA SEMANA**
> Peça para outra pessoa — um colega de equipe, alguém de outro grupo do Coffee & Code, ou você mesmo revisando depois de um tempo — abrir suas três páginas, sem nenhuma explicação sua, e: preencher o formulário de Login, navegar até o Dashboard, ver o Perfil, tudo isso redimensionando a janela para simular um celular em algum momento. Essa pessoa consegue fazer tudo isso sem travar ou ficar confusa?

Se a resposta for sim, sua entrega está no caminho certo. Se não, volte ao módulo correspondente e ajuste — isso não é falha, é exatamente o tipo de ajuste que esta revisão final existe para capturar antes do prazo.

## // Onde tirar dúvidas

Os encontros semanais do Coffee & Code existem para isso. Chegue com uma pergunta específica — "meu grid não está quebrando para 2 colunas no tablet, já tentei X e Y" é muito mais rápido de resolver do que "não entendi nada de CSS Grid".

Se quiser se aprofundar além do que foi pedido, veja `desafios.md`.

## // O que vem na Semana 03

A Semana 02 termina com três telas estáticas, visualmente prontas e responsivas — mas sem nenhum comportamento dinâmico ainda. Um clique em "Entrar" não faz nada de verdade; os cards do Dashboard são sempre os mesmos, não importa quem esteja "logado". É exatamente essa lacuna — comportamento, interatividade, dados que mudam — que as próximas semanas do clube começam a preencher.

Bom trabalho até aqui.

`Material de Estudo // Coffee & Code`
