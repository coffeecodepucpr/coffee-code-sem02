# Desafios — Semana 02

Desafios opcionais, organizados pelos módulos da semana. Nenhum é obrigatório para a entrega básica — veja `entregavel.md` para o que é obrigatório. Use estes desafios se terminou os módulos principais e quer se aprofundar, ou se quer deixar o entregável mais robusto.

---

## // HTML e Formulários (Módulos 02–03)

**Se você está começando**
- Adicione validação nativa extra ao formulário de Login: `minlength` na senha, e uma mensagem de erro customizada usando o atributo `title`.
- Adicione um `<fieldset>` com `<legend>` agrupando os campos do formulário de cadastro, se você criou um.

**Se você já tem experiência**
- Pesquise sobre o atributo `autocomplete` em campos de formulário (por exemplo, `autocomplete="email"`) e aplique nos campos relevantes do Login — isso melhora o preenchimento automático do navegador.
- Adicione um segundo tipo de input relevante ao seu projeto (`type="tel"`, `type="date"`) em algum formulário do Perfil, com o `pattern` correspondente.

---

## // CSS e Box Model (Módulos 04–05)

**Se você está começando**
- Crie uma segunda variação de botão (`.botao-secundario`) com cores diferentes da principal, mas reaproveitando `--spacing` e `--radius` do seu design system.

**Se você já tem experiência**
- Pesquise sobre a propriedade `clamp()` em CSS e use ela para um tamanho de fonte que se ajusta suavemente entre um mínimo e um máximo, sem precisar de uma media query específica para isso.

---

## // Flexbox e Grid (Módulos 06–07)

**Se você está começando**
- Adicione um estado vazio para o Dashboard: o que aparece na área de cards se não houver nenhum grupo? Estilize esse estado (mesmo que simples) usando Flexbox para centralizar uma mensagem.

**Se você já tem experiência**
- No grid do Dashboard, use `grid-template-areas` (em vez de só `grid-template-columns`) para nomear explicitamente as regiões do layout, e pesquise a documentação oficial do MDN sobre essa propriedade antes de aplicar.
- Combine `minmax()` com `auto-fit` no grid de cards, testando o comportamento sem nenhuma media query — compare com a versão que usa breakpoints fixos.

---

## // Responsividade (Módulo 08)

**Se você está começando**
- Teste suas três telas em pelo menos duas larguras que você ainda não tinha testado (por exemplo, 900px e 1440px), e ajuste qualquer ponto de quebra que fizer sentido.

**Se você já tem experiência**
- Pesquise sobre `clamp()` combinado com `vw` para espaçamentos verdadeiramente fluidos (que mudam continuamente, não só em saltos de breakpoint), e aplique em um espaçamento do seu Dashboard.

---

## // Tailwind (Módulo 10)

**Se você está começando**
- Reconstrua a tela de Login inteira usando só Tailwind (via CLI standalone), comparando o resultado final com a versão em CSS puro.

**Se você já tem experiência**
- Configure cores customizadas do seu design system dentro de um bloco `@theme` no seu CSS de entrada do Tailwind v4, e use essas cores customizadas (não as cores padrão do Tailwind) nos componentes reconstruídos.

---

## // Design System em Código (Módulo 11)

**Se você está começando**
- Adicione ao menos duas variáveis de espaçamento que ainda não existem no seu `:root` (por exemplo, `--spacing-2xl`), documentando a decisão em `/docs/design-system.md`.

**Se você já tem experiência**
- Pesquise sobre `@property` (registro tipado de custom properties em CSS) e avalie se faria sentido aplicar em alguma variável do seu projeto — não é obrigatório usar, só entender o que resolve.

---

## // Acessibilidade (Módulo 12)

**Se você está começando**
- Rode uma checagem de contraste em todas as combinações de texto/fundo do seu design system, não só na principal, documentando os resultados.

**Se você já tem experiência**
- Instale uma extensão de auditoria de acessibilidade no seu navegador (pesquise "Lighthouse accessibility audit" ou similar) e rode ela nas suas três telas, corrigindo pelo menos dois pontos que ela apontar.

---

## // Componentização e Temas (Módulo 13)

**Se você está começando**
- Documente, em `/docs/design-system.md`, a lista completa de componentes reutilizáveis do seu projeto e onde cada um aparece.

**Se você já tem experiência**
- Adicione um botão de troca de tema manual, usando JavaScript básico (`document.documentElement.setAttribute('data-theme', ...)`) para alternar o atributo `data-theme` ao clicar — mesmo sabendo que JavaScript não é foco desta semana, este é um bom primeiro contato guiado por curiosidade, não por obrigação.

---

## // Desafio geral (todos)

Peça para alguém de fora do seu grupo (ou você mesmo, revisando depois de um intervalo) navegar pelas suas três telas usando só o teclado, em pelo menos duas larguras de tela diferentes, sem nenhuma explicação sua. Essa pessoa consegue: entender o que cada tela faz? Preencher o formulário de Login? Navegar entre as telas? Se a resposta for sim para tudo, seu entregável está em um bom nível. Se não, volte ao módulo correspondente.
