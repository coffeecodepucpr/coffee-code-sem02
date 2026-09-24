# Módulo 03 — HTML Semântico e Formulários

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // Antes de começar

No Módulo 02 você viu a diferença entre `<div>Entrar</div>` e `<h1>Entrar</h1>` — o segundo carrega significado, o primeiro não. Este módulo aprofunda exatamente esse ponto, e fecha a estrutura completa da tela de Login com um formulário de verdade.

## // O problema: divs dentro de divs dentro de divs

Um padrão comum em código HTML mal estruturado:

```html
<div>
  <div>
    <div>Buscador de Grupos de Estudo</div>
  </div>
  <div>
    <div>Início</div>
    <div>Grupos</div>
    <div>Perfil</div>
  </div>
</div>
```

Pare e pergunte: o que cada `<div>` representa aqui? Sem ler o conteúdo de dentro, é impossível saber. A primeira poderia ser um cabeçalho, um rodapé, um aviso — não tem como saber só olhando a tag.

> **O PONTO PRINCIPAL**
> `<div>` é um elemento genérico — ele agrupa conteúdo, mas não diz nada sobre o que esse conteúdo *é*. Usar `<div>` para tudo é como rotular todas as caixas de uma mudança como "coisas".

## // HTML semântico

> **HTML semântico — em palavras simples**
> É usar tags que descrevem o papel do conteúdo, em vez de tags genéricas — de forma que o significado esteja no próprio HTML, antes de qualquer CSS.

Reescrevendo o exemplo anterior com significado:

```html
<header>
  <h1>Buscador de Grupos de Estudo</h1>
</header>
<nav>
  <a href="inicio.html">Início</a>
  <a href="grupos.html">Grupos</a>
  <a href="perfil.html">Perfil</a>
</nav>
```

Agora um `<header>` é claramente um cabeçalho, e `<nav>` é claramente uma área de navegação — para quem lê o código, para o navegador, e para ferramentas que dependem de significado.

### > As principais tags semânticas

| Tag | Representa |
|---|---|
| `<header>` | Cabeçalho de uma página ou seção |
| `<nav>` | Área de navegação (menu, links principais) |
| `<main>` | Conteúdo principal da página — deve existir só uma vez |
| `<section>` | Uma seção temática de conteúdo |
| `<article>` | Um conteúdo independente, que faria sentido sozinho |
| `<footer>` | Rodapé de uma página ou seção |

## // Por que isso importa de verdade

Três motivos concretos, não só "boa prática":

1. **Leitura e manutenção** — quem abre seu código (inclusive você, meses depois) entende a estrutura sem precisar ler cada linha de conteúdo.
2. **Acessibilidade** — leitores de tela (usados por pessoas com deficiência visual) navegam por região semântica. Um leitor de tela anuncia "navegação" ao chegar em um `<nav>` — em uma `<div>` genérica, ele não tem essa informação.
3. **SEO, como complemento** — mecanismos de busca usam a estrutura semântica para entender do que a página trata. Isso não é o foco desta semana, mas é um efeito colateral positivo de fazer a coisa certa.

> **`BUTTON` ≠ `DIV` CLICÁVEL**
> **Errado:** `<div onclick="...">Entrar</div>` — visualmente pode até parecer um botão, mas para o navegador é uma div qualquer. Não recebe foco pelo teclado, não é anunciado como botão por leitores de tela, e depende de JavaScript até para o clique funcionar.
>
> **Certo:** `<button>Entrar</button>` — é um botão de verdade. Recebe foco pelo teclado (tecla Tab), é anunciado corretamente, e já vem com comportamento de clique embutido, sem precisar de nada extra.

O mesmo vale para `<label>` e `alt`, que você já viu no Módulo 02: eles não são detalhes visuais, são significado que o HTML carrega antes mesmo do CSS entrar em cena.

## // Formulários

> **FORM — EM PALAVRAS SIMPLES**
> Um formulário é uma forma estruturada de coletar informação que uma pessoa preenche, para ser processada de algum jeito.

Mesmo sem nenhum backend esta semana (lembra do Módulo 00: nada de autenticação real ainda), o formulário de Login já representa, estruturalmente, o que vai acontecer quando o backend existir: campos que a pessoa preenche, e um botão que dispara uma ação.

### > Os elementos de um formulário

```html
<form>
  <label for="email">Email</label>
  <input type="email" id="email" name="email" placeholder="voce@exemplo.com" required>

  <label for="senha">Senha</label>
  <input type="password" id="senha" name="senha" required>

  <button type="submit">Entrar</button>
</form>
```

| Elemento/Atributo | O que faz |
|---|---|
| `<form>` | Agrupa os campos que pertencem à mesma submissão |
| `<label>` | Rótulo de um campo — `for` conecta ao `id` do campo correspondente |
| `<input type="email">` | Campo de texto, com validação básica de formato de e-mail pelo próprio navegador |
| `<input type="password">` | Campo de texto que esconde o que é digitado |
| `placeholder` | Texto de exemplo, que desaparece ao digitar — não substitui o `label` |
| `name` | Identifica o campo quando o formulário é enviado a um servidor (importante para semanas futuras, com backend) |
| `required` | Impede o envio se o campo estiver vazio, sem precisar de nenhum código extra |
| `<button type="submit">` | Botão que tenta enviar o formulário |

### > Por que `for` e `id` precisam combinar

```html
<label for="email">Email</label>
<input type="email" id="email">
```

O valor de `for` no label precisa ser idêntico ao `id` no input. Essa conexão faz duas coisas: clicar no texto "Email" foca automaticamente o campo, e leitores de tela anunciam corretamente qual rótulo pertence a qual campo. Sem essa conexão, o label é só um texto solto ao lado do campo — visualmente parecido, estruturalmente desconectado.

## // Estados de foco

Quando você navega por um formulário usando a tecla Tab, o navegador destaca visualmente o campo ativo — isso se chama estado de **foco**. Você não precisa fazer nada para que ele exista (o navegador já mostra um contorno padrão), mas vai ser importante lembrar dele quando chegarmos a CSS (Módulo 04) e Acessibilidade (Módulo 12): remover esse contorno sem colocar outra indicação visual no lugar prejudica diretamente quem navega pelo teclado.

## // Bom exemplo × mau exemplo

**Mau exemplo:**

```html
<div>Email</div>
<input type="text">
<div>Senha</div>
<input type="text">
<div onclick="entrar()">Entrar</div>
```

Nenhum `label` conectado, senha em um campo `text` comum (mostra os caracteres!), e um botão que na verdade é uma div.

**Bom exemplo:**

```html
<form>
  <label for="email">Email</label>
  <input type="email" id="email" name="email" required>

  <label for="senha">Senha</label>
  <input type="password" id="senha" name="senha" required>

  <button type="submit">Entrar</button>
</form>
```

## // Erros comuns

| Erro | Por que acontece | Como corrigir |
|---|---|---|
| `for` e `id` não combinam | Digitar rápido, ou copiar/colar sem ajustar | Sempre confira os dois lado a lado |
| Usar `type="text"` para senha | Esquecer que existe um tipo específico | Use `type="password"` |
| `<div>` clicável no lugar de `<button>` | Parece mais fácil estilizar uma div | Use `<button>` e estilize ele — CSS resolve a aparência (Módulo 04) |
| `placeholder` no lugar de `label` | Parece redundante ter os dois | `placeholder` some ao digitar; sem `label`, ninguém sabe o que preencher depois disso |

## // Prática guiada

Vamos completar a estrutura da tela de Login, que você começou no Módulo 02.

1. Abra `login.html`.
2. Envolva o título e o parágrafo em um `<header>`.
3. Adicione um `<main>` logo abaixo, contendo o restante da tela.
4. Dentro do `<main>`, adicione um `<form>` com os campos de e-mail e senha, seguindo a estrutura desta seção.
5. Adicione o `<button type="submit">Entrar</button>`.
6. Abra o arquivo no navegador. Clique no texto "Email" — o campo recebe foco? Use Tab para navegar entre os campos — a ordem faz sentido?

## // Pratique sozinho

> **DESAFIO**
> No arquivo `cadastro.html` (criado no Módulo 02), adicione um formulário completo: nome, e-mail, senha, e um botão "Criar conta". Use `<header>` para o topo da página e `<main>` para o formulário. Confirme que cada `label` está corretamente conectado ao seu campo, testando o clique no texto do rótulo.

## // Aplicando no projeto da semana

1. Adicione `<header>` e `<main>` às três telas do seu projeto (Login, Dashboard, Perfil), mesmo que o conteúdo interno ainda seja simples.
2. Garanta que o formulário de Login tenha `label`, `type` e `required` corretos em todos os campos.
3. Se o Dashboard ou Perfil tiverem algum botão de ação (ex: "Sair", "Editar perfil"), confirme que são `<button>`, não `<div>`.
4. Commit: `git commit -m "Adiciona HTML semântico e formulário de Login"`.

## // Checkpoint

> **ANTES DE SEGUIR, PENSE NISTO**
> Por que usar `<button>` é melhor que `<div class="button">` para uma ação, mesmo que os dois possam ficar visualmente idênticos depois do CSS?

Resposta: `<button>` já vem com significado e comportamento nativos do navegador — recebe foco pelo teclado, é ativável com Enter/Espaço, e é anunciado corretamente por leitores de tela. Uma `<div>` não tem nada disso por padrão; para igualar o comportamento, seria preciso adicionar manualmente atributos e JavaScript — trabalho extra para chegar a algo que `<button>` já oferece de graça.

## // Resumo do módulo

- [ ] Sei explicar por que `<div>` genérica é um problema, mesmo funcionando visualmente.
- [ ] Conheço as principais tags semânticas e o que cada uma representa.
- [ ] Sei por que `<button>` é diferente de uma `<div>` clicável.
- [ ] Sei montar um formulário com `label`, `input`, `type`, `required` e `button` corretamente conectados.
- [ ] A tela de Login do meu projeto tem uma estrutura HTML semântica completa.

---

**Próximo módulo:** `04-css.md` — a estrutura está pronta. Hora de fazer a página parecer com o que foi planejado no Figma.

`Material de Estudo // Coffee & Code`
