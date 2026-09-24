# Módulo 14 — Projeto Guiado: Login, Dashboard e Perfil

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // Para que serve este módulo

Este módulo não ensina nenhum conceito novo. Ele existe para juntar, em ordem, tudo o que os Módulos 01 a 13 ensinaram separadamente — e mostrar como as três telas do projeto se constroem, do início ao fim, em um único fluxo de trabalho.

Se algum passo abaixo não fizer sentido, é sinal de que vale revisar o módulo correspondente antes de continuar, em vez de simplesmente copiar o código.

## // Antes de começar: a estrutura de pastas

```text
projeto/
├── index.html          (redireciona ou apresenta o projeto)
├── login.html
├── dashboard.html
├── perfil.html
├── css/
│   └── styles.css
└── docs/
    ├── requisitos.md
    ├── historias-de-usuario.md
    ├── design-system.md
    └── arquitetura.md
```

## // Etapa 1 — Estrutura HTML das três telas (Módulos 02 e 03)

Para cada tela, siga a mesma sequência:

1. Escreva a estrutura mínima (`<!DOCTYPE html>` até `</html>`), com `<title>` específico da tela.
2. Adicione `<header>` com navegação (igual nas três telas, para consistência).
3. Adicione `<main>` com o conteúdo específico daquela tela.
4. Use tags semânticas (`<section>`, `<form>`, `<nav>`) em vez de `<div>` genérica sempre que fizer sentido.

**Login** — formulário com e-mail, senha, botão "Entrar", link para cadastro.
**Dashboard** — navbar, e uma área principal com busca e grid de cards de grupos.
**Perfil** — navbar, avatar, informações do usuário, botões de ação.

## // Etapa 2 — Análise antes do CSS (Módulo 09)

Antes de estilizar qualquer tela, desenhe a árvore de componentes dela (se ainda não fez isso no Módulo 09). Para o Dashboard, por exemplo:

```text
Dashboard
├── Navbar
└── Main
    ├── Busca
    └── CardGrid
        ├── Card
        ├── Card
        └── Card
```

## // Etapa 3 — CSS base e Box Model (Módulos 04 e 05)

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: var(--font-family-base, sans-serif);
    background-color: var(--color-background, #f7f2ed);
    color: var(--color-text, #241c18);
}
```

Conecte `css/styles.css` às três páginas com `<link rel="stylesheet" href="css/styles.css">`, ajustando o caminho relativo conforme a posição de cada arquivo HTML.

## // Etapa 4 — Design tokens (Módulo 11)

Adicione o bloco `:root` com as variáveis do seu design system, no topo do `styles.css`, antes de qualquer outra regra.

## // Etapa 5 — Layout com Flexbox e Grid (Módulos 06 e 07)

- **Navbar** (todas as telas): Flexbox, `justify-content: space-between`, `align-items: center`.
- **Formulário de Login**: Flexbox, `flex-direction: column`, `gap`.
- **Grid de cards do Dashboard**: CSS Grid, `grid-template-columns: repeat(3, 1fr)`, `gap`.
- **Dentro de cada card**: Flexbox, `flex-direction: column`.
- **Avatar + informações do Perfil**: Flexbox, `align-items: center`, `gap`.

## // Etapa 6 — Responsividade (Módulo 08)

Para cada tela, nesta ordem:

1. Escreva o CSS base pensando em mobile (uma coluna, elementos empilhados).
2. Adicione `@media (min-width: 768px)` para o layout de tablet.
3. Adicione `@media (min-width: 1024px)` para o layout de desktop.
4. Teste redimensionando o navegador em cada tela.

## // Etapa 7 — Componentização (Módulo 13)

Revise: Button, Card, Input e Navbar usam a mesma classe CSS em todo lugar que aparecem? Se você percebeu alguma variação não intencional entre eles, este é o momento de unificar.

## // Etapa 8 — Acessibilidade (Módulo 12)

Checklist final por tela:

- [ ] Hierarquia de headings sem pular níveis.
- [ ] Todo campo de formulário tem `label` conectado via `for`/`id`.
- [ ] Toda ação usa `<button>`, nunca `<div onclick>`.
- [ ] Toda imagem tem `alt` descritivo.
- [ ] Contraste de texto/fundo verificado.
- [ ] `:focus-visible` visível em todos os elementos interativos.
- [ ] Navegação completa por teclado testada.

## // Etapa 9 — (Opcional) Tailwind ou tema escuro (Módulos 10 e 13)

Se você optou por Tailwind, esta é a etapa de reconstruir componentes com utility classes, mantendo os mesmos tokens visuais. Se está implementando tema escuro, esta é a etapa de testar a alternância entre `data-theme="light"` e `data-theme="dark"`.

## // Checklist de fechamento das três telas

- [ ] `login.html`, `dashboard.html` e `perfil.html` existem e abrem sem erros no navegador.
- [ ] As três compartilham o mesmo `styles.css`.
- [ ] As três usam as mesmas variáveis de design system.
- [ ] As três têm a mesma navbar, visualmente consistente.
- [ ] As três funcionam em pelo menos três larguras de tela (mobile, tablet, desktop).
- [ ] Nenhuma tela depende de `position: absolute` para a estrutura principal.
- [ ] O checklist de acessibilidade da Etapa 8 está completo nas três.

## // Erros comuns ao juntar tudo

| Erro | Por que acontece | Como corrigir |
|---|---|---|
| Cada tela com um `styles.css` diferente | Copiar e colar sem consolidar | Uma única fonte de estilos compartilhada entre as três |
| Navbar visualmente diferente entre as telas | Estilizar cada tela isoladamente | Reutilize exatamente a mesma classe/estrutura da navbar nas três |
| Esquecer de testar responsividade em alguma das três | Focar só na tela "principal" | Repita o teste de redimensionamento em cada uma das três telas, não só na primeira |

## // Aplicando no projeto da semana

Esta é a aplicação — não existe uma atividade separada. Ao final deste módulo, as três telas devem estar completas o suficiente para passar pelo checklist do Módulo 15.

Commit final desta etapa: `git commit -m "Finaliza estrutura, layout e responsividade das três telas"`.

## // Checkpoint

> **ANTES DE SEGUIR, PENSE NISTO**
> Se você tivesse que explicar para alguém, em três frases, por que a ordem HTML → CSS base → layout → responsividade → acessibilidade fez sentido (em vez de, por exemplo, começar pela responsividade), o que você diria?

Resposta possível: sem HTML, não existe o que estilizar. Sem CSS base e Box Model entendidos, layout (Flexbox/Grid) fica imprevisível, porque os tamanhos das caixas não se comportam como esperado. E sem um layout principal já funcionando, não tem sentido adaptar esse layout para telas menores — responsividade ajusta algo que já existe, não substitui a etapa de criar esse algo primeiro.

## // Resumo do módulo

- [ ] Consigo repetir, de memória, a sequência de etapas usada para construir uma tela do zero.
- [ ] As três telas do meu projeto (Login, Dashboard, Perfil) passaram por todas as nove etapas.
- [ ] O checklist de fechamento das três telas está completo.

---

**Próximo módulo:** `15` — antes de considerar a semana concluída, uma revisão final contra os critérios reais do entregável (veja `entregavel.md`).

`Material de Estudo // Coffee & Code`
