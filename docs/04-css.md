# Módulo 04 — CSS: Como o Navegador Estiliza a Página

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // O problema

Sua tela de Login já tem estrutura completa (Módulos 02 e 03): título, formulário, campos, botão. Abra ela no navegador agora. Ela se parece com o que você desenhou no Figma na Semana 01?

Quase certamente não. Título e parágrafo em preto, campos sem espaçamento, botão sem cor — o estilo padrão do navegador, genérico, igual em qualquer site sem CSS. HTML deu significado e estrutura; falta a apresentação visual.

## // O que é CSS?

> **CSS — EM PALAVRAS SIMPLES**
> CSS é a linguagem que descreve como cada elemento HTML deve aparecer — cor, tamanho, espaçamento, posição.
>
> Tecnicamente: CSS (Cascading Style Sheets, "folhas de estilo em cascata") é uma linguagem de estilização que seleciona elementos HTML e aplica declarações de aparência a eles. "Cascata" — a parte mais importante do nome — descreve como o navegador decide qual regra vence quando mais de uma poderia se aplicar ao mesmo elemento. Voltamos a isso em breve.

## // Anatomia de uma regra CSS

```css
button {
    background-color: #6f4e37;
    color: white;
}
```

| Parte | Nome | O que é |
|---|---|---|
| `button` | Seletor | Qual(is) elemento(s) essa regra afeta |
| `background-color: #6f4e37;` | Declaração | Uma propriedade + um valor, separados por dois-pontos, terminando em ponto e vírgula |
| `background-color` | Propriedade | O que está sendo alterado |
| `#6f4e37` | Valor | Para que está sendo alterado |
| tudo entre `{ }` | Regra (ou "bloco de declarações") | O conjunto de declarações aplicadas àquele seletor |

Essa regra inteira diz: "todo elemento `<button>` da página deve ter fundo na cor `#6f4e37` e texto branco."

## // Seletores: escolhendo o que estilizar

### > Seletor de elemento

```css
button {
    color: white;
}
```

Afeta **todos** os `<button>` da página, sem exceção.

### > Seletor de classe

```html
<button class="btn-primario">Entrar</button>
```

```css
.btn-primario {
    background-color: #6f4e37;
}
```

O ponto (`.`) antes do nome indica que é uma classe. Diferente do seletor de elemento, uma classe só afeta elementos que a recebem explicitamente — útil quando nem todo botão da página deve ser igual (um botão "Entrar" e um botão "Cancelar" provavelmente não deveriam ter a mesma cor).

### > Seletor de ID (contextualizando)

```css
#form-login {
    max-width: 400px;
}
```

O `#` seleciona pelo atributo `id`. Diferente de classes, um `id` deve ser único na página — só um elemento pode ter aquele `id`. Na prática, classes são usadas com muito mais frequência que IDs para estilização, justamente porque um estilo reutilizável (como um botão) normalmente precisa se aplicar a vários elementos, não a um só.

### > Pseudo-classes (introdução)

```css
button:hover {
    background-color: #5a3e2c;
}
```

`:hover` seleciona o elemento apenas quando o mouse está sobre ele. Existem várias pseudo-classes — vamos ver `:focus` com mais profundidade no Módulo 12 (Acessibilidade), porque ela é essencial para quem navega pelo teclado.

## // Cascade, inheritance e specificity — em nível introdutório

Essas três palavras respondem a mesma pergunta prática: **o que acontece quando duas regras CSS competem pelo mesmo elemento?**

> **CASCADE — EM PALAVRAS SIMPLES**
> Cascata é o mecanismo que o navegador usa para decidir, entre várias regras que poderiam se aplicar a um elemento, qual realmente vale. De forma simplificada, a regra mais específica costuma vencer; entre regras igualmente específicas, a que vem depois no arquivo vence.

Exemplo:

```css
button {
    color: white;
}

.btn-secundario {
    color: black;
}
```

Um `<button class="btn-secundario">` fica com texto preto — porque um seletor de classe é mais específico que um seletor de elemento. Isso é **specificity**: uma forma de medir o "peso" de um seletor. Você não precisa decorar uma tabela de pontuação de specificity esta semana — só entender que classes pesam mais que elementos, e que isso explica por que "minha regra não está funcionando" quase sempre significa "outra regra mais específica está vencendo".

> **INHERITANCE — EM PALAVRAS SIMPLES**
> Alguns estilos (como cor de texto e fonte) passam automaticamente de um elemento pai para seus filhos, a não ser que o filho tenha sua própria regra. Se você define a fonte no `<body>`, todos os elementos dentro dele herdam essa fonte, sem precisar repetir a regra em cada um.

## // Conectando CSS ao HTML

Existem três formas de aplicar CSS. Só uma delas é recomendada para projetos reais:

| Forma | Como | Quando usar |
|---|---|---|
| Inline | `<button style="color: white;">` | Evite — mistura estrutura e apresentação, difícil de manter |
| `<style>` no `<head>` | Bloco de CSS dentro do próprio HTML | Aceitável para testes rápidos, não para o projeto |
| Arquivo externo `.css` | Um arquivo `.css` separado, conectado via `<link>` | **Esta é a forma usada no projeto** |

### > Por que separar em arquivos

```text
login.html
dashboard.html
perfil.html
styles.css
```

Um arquivo `.css` compartilhado entre as três páginas garante que um botão tenha a mesma aparência em todas elas — mudar a cor uma vez muda nas três telas de uma vez, em vez de editar em três lugares separados.

### > Conectando o arquivo

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

| Parte | O que faz |
|---|---|
| `<link>` | Elemento que conecta recursos externos ao HTML |
| `rel="stylesheet"` | Diz que tipo de recurso é este — uma folha de estilo |
| `href="styles.css"` | Onde o arquivo está, relativo à posição do arquivo HTML |

### > Caminho relativo: o erro mais comum de CSS que "não funciona"

Se `styles.css` está na mesma pasta que `login.html`, `href="styles.css"` funciona. Mas se sua estrutura for:

```text
pages/
  login.html
css/
  styles.css
```

`href="styles.css"` vai falhar — o navegador procura `styles.css` dentro de `pages/`, onde ele não existe. O caminho certo, a partir de `pages/login.html`, seria `href="../css/styles.css"` (o `../` sobe um nível de pasta antes de descer para `css/`).

## // Exemplo guiado: estilizando o botão de Login

```css
button {
    background-color: #6f4e37;
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 8px;
}
```

Cada linha resolve uma parte visível: `background-color` e `color` dão a cor de fundo e do texto; `padding` dá espaço interno (mais sobre isso no Módulo 05); `border: none` remove a borda padrão do navegador; `border-radius` arredonda os cantos.

## // Erros comuns

| Erro | Por que acontece | Como corrigir |
|---|---|---|
| CSS "não funciona" | Caminho do `href` errado, ou arquivo não salvo | Abra o DevTools (Módulo 12 cobre isso melhor) e confira se o CSS foi carregado |
| Esquecer o `;` no final de uma declaração | Fácil de esquecer digitando rápido | Toda declaração termina em ponto e vírgula, mesmo a última do bloco |
| Confundir `.classe` com `#id` | Os símbolos parecem parecidos à primeira vista | `.` para classe (reutilizável), `#` para id (único) |
| Regra não aplica porque outra é mais específica | Não entender cascade/specificity ainda | Seletores de classe vencem seletores de elemento; o último a ser declarado vence em empates |

## // Prática guiada

1. Crie o arquivo `styles.css` na raiz do seu projeto.
2. Conecte ele em `login.html` usando `<link rel="stylesheet" href="styles.css">`.
3. Escreva uma regra para `body` definindo uma `font-family` (por exemplo, `font-family: sans-serif;`).
4. Escreva uma regra para `button`, usando as cores do seu design system da Semana 01.
5. Salve, recarregue o navegador, e confirme visualmente que as mudanças apareceram.

## // Pratique sozinho

> **DESAFIO**
> Adicione uma classe `.link-secundario` para o link "Ainda não tem conta?" do Login, estilizando ele com uma cor diferente da cor primária do seu design system. Depois, sem usar `!important` nem duplicar a regra, faça um teste: adicione uma segunda regra para `a` (todos os links) com outra cor, e observe qual das duas vence — e por quê.

## // Aplicando no projeto da semana

1. Conecte `styles.css` às três páginas (Login, Dashboard, Perfil).
2. Defina estilos base para `body` (fonte, cor de fundo) usando o design system da Semana 01.
3. Estilize os botões e links principais.
4. Commit: `git commit -m "Adiciona CSS inicial e conecta às três telas"`.

## // Checkpoint

> **ANTES DE SEGUIR, PENSE NISTO**
> Você tem duas regras no seu CSS: uma para `button` e outra para `.btn-cancelar`, e ambas definem `background-color` diferente. Um botão com `class="btn-cancelar"` — qual cor de fundo ele vai ter, e por quê?

Resposta: a cor definida em `.btn-cancelar` — porque um seletor de classe é mais específico que um seletor de elemento, então vence a cascata, independente da ordem em que as regras aparecem no arquivo.

## // Resumo do módulo

- [ ] Sei explicar o que é CSS e por que ele existe separado do HTML.
- [ ] Sei a anatomia de uma regra: seletor, propriedade, valor, declaração.
- [ ] Sei a diferença entre seletor de elemento, classe e id.
- [ ] Entendo, em nível introdutório, o que é cascade e por que uma regra pode "perder" para outra.
- [ ] Sei conectar um arquivo CSS externo ao HTML, e sei diagnosticar um caminho relativo errado.
- [ ] As três telas do meu projeto já têm um `styles.css` conectado, com os primeiros estilos aplicados.

---

**Próximo módulo:** `05-box-model-e-unidades.md` — por que seu elemento de 300px raramente ocupa exatamente 300px.

`Material de Estudo // Coffee & Code`
