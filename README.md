# ☕ Coffee & Code — SEM 02 | Interface Web (Parte 1: Layout)

```text
> module: sem-02
> tema: interface web — layout
> status: online
> coffee loaded ✓
```

Material da **Semana 02** da trilha do Coffee & Code, o clube de tecnologia da PUCPR.

Na Semana 01 você planejou. Nesta semana você constrói. Aquele protótipo do Figma é uma representação da interface — não é a interface. Um arquivo do Figma não roda no navegador de ninguém.

A Semana 02 existe para fechar essa distância: pegar o que foi decidido e transformar em HTML e CSS reais. No fim da semana você abre as suas três telas no navegador, redimensiona a janela até o tamanho de um celular, e nada quebra.

## Por onde começar

👉 **[docs/00-comece-aqui.md](docs/00-comece-aqui.md)** — leia este primeiro. Ele explica o caminho da semana e como estudar.

Depois, siga os módulos na ordem:

| # | Módulo | Sobre |
|---|---|---|
| 01 | [Como a web funciona](docs/01-como-a-web-funciona.md) | Navegador, servidor, e o papel de HTML/CSS/JS |
| 02 | [HTML](docs/02-html.md) | Estrutura: tags, elementos, pai/filho/irmão |
| 03 | [HTML semântico e formulários](docs/03-html-semantico-e-formularios.md) | Significado no markup e o formulário de Login |
| 04 | [CSS](docs/04-css.md) | Seletores, cascade, conectando CSS ao HTML |
| 05 | [Box Model e unidades](docs/05-box-model-e-unidades.md) | `border-box`, padding, margin, px/rem/%/vh |
| 06 | [Flexbox](docs/06-flexbox.md) | Eixos, alinhamento, distribuição |
| 07 | [Grid](docs/07-grid.md) | Linhas, colunas, `fr` — e quando não usar Flexbox |
| 08 | [Responsividade](docs/08-responsividade.md) | Viewport, breakpoints, mobile-first |
| 09 | [Do Figma para o código](docs/09-figma-para-codigo.md) | Decompondo uma tela antes de codificar |
| 10 | [Tailwind](docs/10-tailwind.md) | Utility-first CSS com Tailwind v4 |
| 11 | [Design System no código](docs/11-design-system-no-codigo.md) | Tokens do Figma como CSS Custom Properties |
| 12 | [Acessibilidade](docs/12-acessibilidade.md) | Contraste, foco, navegação por teclado |
| 13 | [Componentização e temas](docs/13-componentizacao-e-temas.md) | Componentes reutilizáveis, tema claro/escuro |
| 14 | [Projeto guiado](docs/14-projeto-guiado.md) | Construindo as três telas, do início ao fim |

E, para consultar quando precisar:

- 💻 [Exemplo executável](docs/example/) — as três telas em HTML/CSS puro, para consulta
- 🎯 [Desafios](docs/desafios.md) — opcionais, para ir além do pedido
- ✅ [Entregável](docs/entregavel.md) — checklist final antes de fechar a semana

## O exemplo executável

A pasta [`docs/example/`](docs/example/) tem uma implementação de referência das três telas, em HTML e CSS puro. Baixe o repositório e abra o `index-semana02.html` no navegador para navegar entre elas.

É material de **consulta, não gabarito**. O seu projeto tem as suas próprias telas, decididas na Semana 01 — o exemplo serve para você ver uma solução possível quando travar, não para copiar.

## O entregável

Ao final da Semana 02, o repositório do **seu projeto** (não este aqui) deve ter as três telas do seu protótipo implementadas:

```text
login.html
dashboard.html
perfil.html
css/
└── styles.css    ← compartilhado pelas três
```

As três páginas precisam abrir sem erros, usar HTML semântico, compartilhar o mesmo CSS construído sobre os tokens do seu design system, e funcionar de ~375px até ~1200px sem rolagem horizontal.

O checklist completo está em [docs/entregavel.md](docs/entregavel.md).

> **A beleza não é o critério.** Estrutura simples com HTML semântico correto, CSS organizado em variáveis e responsividade funcional vale mais, nesta semana, do que um visual elaborado com `<div>` no lugar de `<button>` e que quebra no celular.

## O que não entra nesta semana

Para evitar ansiedade desnecessária: nada de backend, banco de dados ou autenticação real. JavaScript funcional não é esperado. Tailwind é opcional — CSS puro é uma entrega igualmente válida. E não se espera fidelidade pixel a pixel ao Figma: pequenos ajustes ao migrar de um design estático para HTML/CSS real são normais.

## Projeto contínuo

Todos os módulos usam o mesmo projeto fictício da Semana 01: o **Buscador de Grupos de Estudo**, uma plataforma para estudantes encontrarem colegas estudando a mesma matéria. Se você tem um projeto próprio, o raciocínio de cada módulo se aplica da mesma forma — só troque o nome.

## Como funciona

O Coffee & Code é **100% online**. Cada módulo foi escrito para ser autossuficiente: você estuda no seu ritmo, pode avançar mais rápido, voltar em semanas anteriores e consultar o material durante o projeto.

Os encontros semanais, também online, existem para tirar dúvidas, revisar conceitos, programar junto e mostrar o que você produziu — **não para dar aula**:

- 🗓️ **quarta-feira** — 20h00 às 21h30
- 🗓️ **sábado** — 10h00 às 11h30

Os dois trabalham o mesmo conteúdo. Escolha o que couber melhor na sua semana, e não precisa ficar o horário inteiro na call.

## Travou?

Chega no encontro ou no Discord com uma pergunta específica. `"travei em X, já tentei Y"` costuma ser resolvido muito mais rápido do que `"não entendi nada do módulo Z"`.

E lembra: não saber alguma coisa não é problema. Saber pesquisar faz parte da área.

## Diagramas

Todos os diagramas usados nos módulos estão em [`docs/assets/`](docs/assets/), em formato SVG editável.

## Semanas anteriores

- [SEM 01 — Kickoff & Design System](https://github.com/coffeecodepucpr/coffee-code-sem01)

---

```text
HTTP 418 — I'm a teapot
> ready to code
```
