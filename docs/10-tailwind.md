# Módulo 10 — Tailwind CSS

`SEM 02 // Interface Web — Parte 1: Layout`

---

## // Antes de começar

Este módulo só faz sentido depois dos Módulos 04 a 08. Se `display: flex`, `padding` ou `grid-template-columns` ainda não estão claros como CSS puro, volte lá antes de continuar — Tailwind não ensina CSS, ele abrevia a escrita de CSS que você já entende.

## // O problema

Em uma interface com vários componentes, é comum escrever bastante CSS repetitivo:

```css
.card {
    display: flex;
    padding: 1rem;
    border-radius: 0.75rem;
}

.card-secundario {
    display: flex;
    padding: 1rem;
    border-radius: 0.5rem;
}
```

Cada novo componente pede um novo nome de classe, e boa parte das declarações se repete de um para o outro. Tailwind propõe um jeito diferente de resolver isso.

## // O que é Tailwind

> **TAILWIND — EM PALAVRAS SIMPLES**
> Tailwind é uma biblioteca de CSS que, em vez de te dar classes prontas por componente (como `.card` ou `.botao-primario`), te dá classes pequenas, uma para cada propriedade CSS — e você combina várias delas direto no HTML para montar o estilo.

Essa ideia tem nome: **utility-first**. Em vez de nomear e definir um componente inteiro, você aplica *utilities* (classes utilitárias) até alcançar o resultado.

## // Comparando lado a lado

**CSS tradicional:**

```css
.card {
    display: flex;
    padding: 1rem;
    border-radius: 0.75rem;
}
```
```html
<div class="card">...</div>
```

**Tailwind:**

```html
<div class="flex p-4 rounded-xl">...</div>
```

Traduzindo cada classe:

| Classe Tailwind | CSS equivalente |
|---|---|
| `flex` | `display: flex;` |
| `p-4` | `padding: 1rem;` |
| `rounded-xl` | `border-radius: 0.75rem;` |

> **NÃO DEIXE ISSO VIRAR MÁGICA**
> A classe `flex` não é uma palavra especial que "faz o layout funcionar" — é literalmente `display: flex` escrito de um jeito mais curto. Toda classe Tailwind representa uma ou mais declarações CSS reais. Se você não sabe qual CSS uma classe representa, você não sabe o que ela está fazendo — só está copiando algo que parece funcionar.

## // Utility classes que você já reconhece

Como você já estudou CSS puro nos módulos anteriores, a maioria das classes Tailwind vai parecer familiar assim que você souber o padrão:

| Categoria | Exemplos | Equivale a |
|---|---|---|
| Spacing (escala) | `p-4`, `m-2`, `gap-6` | `padding`, `margin`, `gap`, em uma escala consistente |
| Colors | `bg-amber-700`, `text-white` | `background-color`, `color`, usando a paleta do Tailwind |
| Flex | `flex`, `justify-between`, `items-center` | `display: flex`, `justify-content`, `align-items` |
| Grid | `grid`, `grid-cols-3`, `gap-4` | `display: grid`, `grid-template-columns`, `gap` |
| Width | `w-full`, `w-64` | `width: 100%`, `width: 16rem` |
| Responsividade | `md:grid-cols-2` | a mesma regra, só ativa a partir do breakpoint `md` |
| Hover | `hover:bg-amber-800` | a regra só se aplica no `:hover` |
| Focus | `focus:outline-none` | a regra só se aplica no `:focus` |

Repare: `justify-between` é `justify-content: space-between`, um conceito que você já viu inteiro no Módulo 06. Tailwind não inventa layout novo — ele abrevia o CSS que já existe.

## // A escala de spacing

```html
<div class="p-1">...</div>  <!-- 0.25rem -->
<div class="p-2">...</div>  <!-- 0.5rem -->
<div class="p-4">...</div>  <!-- 1rem -->
<div class="p-8">...</div>  <!-- 2rem -->
```

Os números não são pixels nem uma unidade livre — são posições em uma escala pré-definida, pensada para manter espaçamentos consistentes entre si (o mesmo princípio de consistência do seu design system da Semana 01, só que aplicado através de uma escala já pronta).

## // Responsividade em Tailwind

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
```

Isso diz: 1 coluna por padrão (mobile-first, igual ao Módulo 08), 2 colunas a partir do breakpoint `md`, 3 a partir do `lg`. Os prefixos `md:` e `lg:` são convenções do próprio Tailwind para representar breakpoints — por padrão, `md` equivale a `768px` e `lg` a `1024px`, os mesmos valores que você já usou manualmente no Módulo 08.

## // Dark mode, quando pertinente

```html
<div class="bg-white dark:bg-gray-900 text-black dark:text-white">
```

O prefixo `dark:` aplica a regra quando o modo escuro está ativo. Vamos aprofundar tema claro/escuro no Módulo 13 — por enquanto, só reconheça o padrão.

## // Instalando o Tailwind — o que este guia usa, e por quê

> **VERSÃO E DATA DA CONSULTA**
> Este módulo foi escrito consultando a documentação oficial do Tailwind CSS (tailwindcss.com/docs) em 21 de setembro de 2026. A versão estável atual é o **Tailwind CSS v4** (build 4.3.x). A v4 mudou a forma de instalar em relação a versões antigas: não existe mais `tailwind.config.js` obrigatório, e o antigo `@tailwind base; @tailwind components; @tailwind utilities;` foi substituído por um único `@import "tailwindcss";`. Se você encontrar um tutorial mais antigo usando esses comandos, ele está desatualizado — siga o que está aqui.

### > Para testar rapidamente (Play CDN)

```html
<head>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
```

Uma linha, sem instalar nada, sem terminal. O navegador baixa o Tailwind e gera o CSS necessário em tempo real, direto no navegador. **Use isso só para testar e aprender** — não é a forma recomendada para o projeto final, porque o processamento acontece no navegador de quem visita a página, a cada carregamento, sem otimização.

### > Para o projeto real (CLI standalone, sem precisar de Node.js)

Esta é a forma recomendada para o entregável da semana, porque gera um arquivo `.css` real e compilado — sem depender de Node.js instalado, o que a maioria de quem está começando ainda não tem configurado:

1. Baixe o executável correspondente ao seu sistema operacional, direto da página de releases oficial do Tailwind no GitHub (`github.com/tailwindlabs/tailwindcss/releases`).
2. Dê permissão de execução ao arquivo baixado (no Mac/Linux: `chmod +x tailwindcss`).
3. Crie um arquivo `input.css` com o conteúdo:
   ```css
   @import "tailwindcss";
   ```
4. Rode o comando que compila esse arquivo para um CSS final, observando mudanças:
   ```bash
   ./tailwindcss -i input.css -o styles.css --watch
   ```
5. Conecte `styles.css` (o arquivo gerado) ao seu HTML, exatamente como você já faz desde o Módulo 04.

> **SE VOCÊ JÁ TEM NODE.JS INSTALADO**
> Existe também o caminho via npm: `npm install tailwindcss @tailwindcss/cli`, e depois `npx @tailwindcss/cli -i input.css -o styles.css --watch`. É equivalente ao standalone — escolha o que for mais conveniente para o seu ambiente.

## // Tailwind não substitui CSS

Reforçando o ponto mais importante deste módulo: Tailwind é construído em cima dos conceitos que você já estudou, não no lugar deles. Olhe para este trecho:

```html
<div class="flex items-center justify-between gap-4">
```

O objetivo é que você consiga ler isso e pensar: *Flexbox, alinhamento vertical centralizado, distribuição com espaço entre os itens, espaçamento de 1rem entre eles* — não "essas são classes que fazem funcionar". Se você só decorar nomes de classes sem saber o CSS por trás, qualquer situação que fuja do óbvio (um bug, uma necessidade não coberta por uma utility pronta) vai te deixar travado.

## // Bom exemplo × mau exemplo

**Mau exemplo** — copiar classes sem entender:

> "Vi esse conjunto de classes em um template e colei, não sei o que cada uma faz, mas ficou parecido."

**Bom exemplo** — aplicar sabendo o que cada classe representa:

> "Usei `flex` porque preciso alinhar esses itens em linha, `justify-between` porque quero o logo de um lado e os links do outro, e `gap-4` para o espaçamento — a mesma decisão que tomaria escrevendo CSS puro, só mais rápido de escrever."

## // Erros comuns

| Erro | Por que acontece | Como corrigir |
|---|---|---|
| Tailwind "não aplica nenhuma classe" | Script do Play CDN não carregou, ou CSS compilado não foi conectado | Confira se o `<script>` está no `<head>` (Play CDN) ou se o `styles.css` gerado está com `<link>` correto |
| Misturar CDN e CLI no mesmo projeto | Confusão sobre qual caminho seguir | Escolha um: CDN só para teste, CLI para o projeto real |
| Usar `tailwind.config.js` de um tutorial antigo | Tutorial baseado em Tailwind v3 ou anterior | Na v4, configuração customizada vai direto no CSS, dentro de um bloco `@theme` |
| Aplicar dezenas de classes sem entender nenhuma | Copiar de outro projeto sem verificar | Traduza mentalmente cada classe para o CSS equivalente antes de usar |

## // Prática guiada

1. Adicione o Play CDN (`<script src="https://cdn.tailwindcss.com"></script>`) a uma página de teste separada, fora do seu projeto principal.
2. Recrie a navbar do Módulo 06 usando só classes Tailwind: `flex`, `justify-between`, `items-center`, `p-4`.
3. Compare visualmente com a versão em CSS puro que você já tinha — o resultado deveria ser idêntico.
4. Para cada classe usada, diga em voz alta o CSS equivalente, sem consultar a tabela desta seção.

## // Pratique sozinho

> **DESAFIO**
> Reescreva o grid de cards do Dashboard (Módulo 07) usando `grid`, `grid-cols-1`, `md:grid-cols-2`, `lg:grid-cols-3` e `gap-4`. Teste redimensionando a janela do navegador, e confirme que o comportamento responsivo é equivalente ao que você já tinha construído manualmente com media queries.

## // Aplicando no projeto da semana

1. Decida: seu projeto vai usar Tailwind via CLI standalone, ou continuar em CSS puro? (Os dois são válidos — o importante é que a escolha seja consciente, não copiada sem entender.)
2. Se optar por Tailwind, instale a CLI standalone e gere seu `styles.css` a partir de `@import "tailwindcss";`.
3. Reconstrua pelo menos um componente do seu projeto (por exemplo, o botão principal) usando utility classes, mantendo as mesmas cores e espaçamentos do seu design system.
4. Commit: `git commit -m "Adiciona Tailwind CSS e reconstrói componente com utility classes"`.

## // Checkpoint

> **ANTES DE SEGUIR, PENSE NISTO**
> Por que a classe Tailwind `class="flex items-center gap-4"` não elimina a necessidade de entender Flexbox?

Resposta: porque essa classe é apenas uma forma abreviada de escrever `display: flex; align-items: center; gap: 1rem;`. Sem entender o que Flexbox faz — container, items, eixos — não dá para prever o resultado, ajustar quando algo sair diferente do esperado, ou decidir quais outras utility classes combinar para resolver um problema de layout que não tenha uma solução pronta.

## // Resumo do módulo

- [ ] Sei explicar o conceito de utility-first, com um exemplo comparando CSS puro e Tailwind.
- [ ] Sei traduzir classes comuns do Tailwind (`flex`, `p-4`, `grid-cols-3`, `md:`, `hover:`) para o CSS que elas representam.
- [ ] Sei a diferença entre usar o Play CDN (teste) e instalar a CLI standalone (projeto real), e por quê.
- [ ] Sei por que Tailwind não substitui o conhecimento de CSS.
- [ ] Já reconstruí pelo menos um componente do meu projeto usando Tailwind.

---

**Próximo módulo:** `11-design-system-no-codigo.md` — suas cores e espaçamentos já existem no Figma. Hora de transformar isso em tokens reais no código.

`Material de Estudo // Coffee & Code`
