# Módulo 00 — Comece Aqui

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // Bem-vindo à Semana 02

Na Semana 01 você planejou. Nesta semana você constrói.

Se você seguiu a Semana 01 até o fim, seu repositório já tem uma pasta `/docs` com requisitos, histórias de usuário, um design system documentado e um protótipo navegável no Figma. Nada disso, sozinho, roda no navegador de ninguém. Um arquivo do Figma é uma representação da interface — não é a interface.

A Semana 02 existe para fechar essa distância: pegar o que foi decidido e transformar em HTML e CSS reais, que qualquer navegador consegue abrir e mostrar.

> **DE ONDE VIEMOS**
> Semana 01: ideia → problema → usuário → requisitos → histórias de usuário → fluxo → UX/UI → Figma → design system → arquitetura inicial.
>
> Essa sequência termina em decisões. A Semana 02 começa exatamente onde ela parou.

## // O que você vai construir

Três páginas, as mesmas três telas que você projetou no Figma:

- **Login**
- **Dashboard**
- **Perfil**

Ao final da semana, você deve conseguir abrir essas três páginas em um navegador, ver o layout que planejou, e redimensionar a janela sem que nada quebre — do tamanho de um monitor até o de um celular.

## // O que significa "interface web"

Uma interface web é a parte de um sistema que existe dentro de um navegador — o conjunto de páginas, elementos e estilos com os quais uma pessoa interage diretamente. "Frontend" é o nome que se dá ao trabalho de construir essa parte: tudo o que roda no navegador da pessoa que usa o sistema, em oposição ao "backend", que roda em um servidor, fora do alcance direto de quem usa.

Esta semana você trabalha inteiramente no frontend — e ainda em uma fatia específica dele: estrutura e aparência, sem comportamento dinâmico complexo.

## // O que NÃO será feito ainda

Isso precisa ficar muito claro antes de começar, porque é fácil confundir "a tela existe" com "a funcionalidade existe".

**Esta semana:**
- estrutura (HTML)
- visual (CSS)
- layout (Flexbox, Grid)
- responsividade (a tela se adapta a qualquer tamanho)

**Ainda não:**
- autenticação real
- banco de dados
- comunicação com uma API
- lógica de programação complexa
- qualquer coisa de backend

Um botão de "Entrar" pode — e deve — existir visualmente esta semana, sem autenticar ninguém de verdade. Isso não é uma limitação do seu trabalho; é o escopo certo para esta etapa. Autenticação de verdade é assunto de semanas futuras do clube, depois que a interface já existir.

> **CONCEITO — EM PALAVRAS SIMPLES**
> Uma página pode estar visualmente 100% pronta e funcionalmente 0% pronta ao mesmo tempo. Isso não é um problema — é exatamente o que "interface estática" significa, e é exatamente o entregável desta semana.

## // O que vamos usar da Semana 01

Três coisas, especificamente:

1. **O protótipo do Figma** — cada tela que você construir esta semana parte de uma tela que já existe lá. Você não está inventando layout novo, está traduzindo um layout já decidido.
2. **O design system** (`/docs/design-system.md`) — cores, tipografia e espaçamento que você definiu não são escolhidos de novo; eles viram valores reais no CSS.
3. **O projeto contínuo** — se você seguiu a Semana 01 com o Buscador de Grupos de Estudo (plataforma para estudantes encontrarem grupos de estudo), é esse mesmo projeto que ganha interface agora. Se sua equipe já tinha um projeto próprio, o raciocínio é idêntico — só troque o nome.

## // Da Semana 01 à Semana 02, num mapa só

```
SEMANA 01                          SEMANA 02
──────────                         ──────────
FIGMA                              ESTRUTURA DA PÁGINA
  ↓                                  ↓
                                    HTML
                                     ↓
                                    ESTILIZAÇÃO
                                     ↓
                                    CSS
                                     ↓
                                    LAYOUT
                                     ↓
                                    FLEXBOX / GRID
                                     ↓
                                    RESPONSIVIDADE
                                     ↓
                                    TAILWIND
                                     ↓
                                    TELA IMPLEMENTADA
```

A pergunta que guia a semana inteira:

> Como transformar uma interface planejada no Figma em uma página que o navegador consegue renderizar?

Todo módulo daqui para frente existe para responder um pedaço dessa pergunta. HTML, CSS, Flexbox, Grid, responsividade e Tailwind não são cinco assuntos soltos — são cinco ferramentas que resolvem partes diferentes do mesmo problema.

## // As duas trilhas

**Se você está começando** — nunca escreveu uma tag HTML, nunca abriu um arquivo `.css`. O caminho principal de cada módulo assume isso e não pula nenhuma etapa.

**Se você já tem experiência** — já construiu interfaces antes. Cada módulo tem blocos de aprofundamento, claramente marcados, depois do conteúdo essencial: componentização, design tokens em CSS, temas claro/escuro, acessibilidade avançada.

Ninguém trabalha em um projeto diferente. Todo mundo constrói as mesmas três telas — a profundidade é que muda.

## // Mapa da Semana 02

| Módulo | Conteúdo | Você vai conseguir |
|---|---|---|
| 00 | Comece aqui | Saber de onde vem e para onde vai esta semana |
| 01 | Como a web funciona | Explicar o que acontece entre abrir um arquivo e ver uma tela |
| 02 | HTML: estrutura | Estruturar uma página do zero |
| 03 | HTML semântico e formulários | Dar significado real à estrutura, construir o Login |
| 04 | CSS: como o navegador estiliza | Conectar CSS ao HTML e aplicar as primeiras regras |
| 05 | Box Model, tamanhos e espaçamento | Prever exatamente o tamanho de qualquer elemento |
| 06 | Flexbox | Alinhar e distribuir elementos em uma dimensão |
| 07 | CSS Grid | Organizar cards em duas dimensões |
| 08 | Responsividade | Adaptar o layout para qualquer largura de tela |
| 09 | Do Figma para o código | Decompor uma tela antes de codificar |
| 10 | Tailwind CSS | Escrever CSS através de utility classes |
| 11 | Design System em código | Transportar tokens do Figma para variáveis reais |
| 12 | Acessibilidade | Construir interfaces que funcionam para mais gente |
| 13 | Componentização e temas | Reconhecer padrões repetidos, tema claro/escuro |
| 14 | Projeto guiado | Construir Login, Dashboard e Perfil do início ao fim |
| 15 | Revisão, testes e entrega | Confirmar que o entregável está completo |

Cada módulo é um arquivo independente, mas foram escritos para serem lidos nesta ordem — HTML precisa existir antes de CSS, CSS básico precisa existir antes de Flexbox/Grid, e ambos precisam existir antes de Tailwind fazer algum sentido.

---

**Próximo módulo:** `01-como-a-web-funciona.md` — antes de escrever a primeira tag, entenda o que o navegador realmente faz com ela.

`Material de Estudo // Coffee & Code`
