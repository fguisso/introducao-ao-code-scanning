<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses the MIT license.
-->

# Habilitando o Code Scanning para deixar seu código seguro

_Assegurar a segurança do código fonte das aplicações é um passo essencial no desenvolvimento de software moderno. Neste curso você ira aprender como usar o Github Code Scanning para identificar, resolver e previnir padrões inseguros de código._

</header>

<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
  TBD-step-1-notes.
-->

## Olá, mundo!

_Bem-vindo(a) ao "Introdução ao CodeQL"! :wave:_

Neste curso, vamos explorar como usar o code scanning do GitHub, impulsionado pelo [CodeQL](https://codeql.github.com/), para detectar práticas de programação que podem deixar brechas na segurança. Durante nosso percurso, vamos ativar o code scanning no seu repositório para identificar, corrigir e evitar que novas vulnerabilidades apareçam.

O code scanning é parte da suíte de recursos do [GitHub Advanced Security (GHAS)](https://docs.github.com/en/get-started/learning-about-github/about-github-advanced-security). E a melhor parte: todos os recursos do Advanced Security são 100% gratuitos para repositórios públicos e open source!

- **Para quem é este curso**: Desenvolvedores, engenheiros de segurança e mantenedores de projetos open source.
- **O que você vai aprender**: Mostraremos como ativar o code scanning e identificar vulnerabilidades de injeção de SQL com o CodeQL.
- **O que você vai construir**: Uma pipeline de desenvolvimento segura, que identifica e previne novas vulnerabilidades antes que elas entrem em ação na produção.
- **Pré-requisitos**: Você precisa ter uma noção básica dos conceitos do GitHub, como pull requests, GitHub Actions e gerenciamento de código fonte. Também é bom já estar familiarizado com o que é Static Application Security Testing (SAST). Mas relaxe, vamos descomplicar tudo para você! 🙂
- **Duração**: São apenas quatro passos, e o curso leva menos de 30 minutos para ser concluído.

## Como começar este curso

<!-- For start course, run in JavaScript:
'https://github.com/new?' + new URLSearchParams({
  template_owner: 'TBD-organization',
  template_name: 'TBD-course-name',
  owner: '@me',
  name: 'TBD-organization-TBD-course-name',
  description: 'My clone repository',
  visibility: 'public',
}).toString()
-->

[![Começar o curso](https://user-images.githubusercontent.com/1221423/235727646-4a590299-ffe5-480d-8cd5-8194ea184546.svg)](https://github.com/new?template_owner=fguisso&template_name=introducao-ao-code-scanning&owner=%40me&name=introducao-ao-code-scanning&description=Introdu%C3%A7%C3%A3o%20guiada%20ao%20Code%20Scanning&visibility=public)

1. Clique com o botão direito em **Começar o curso** e abra o link em uma nova aba.
2. Na nova aba, a maioria dos campos já estará preenchida para você.
   - Para o "owner", escolha sua conta pessoal ou a organização onde deseja hospedar o repositório. *Ao utilizar uma organização, algumas regras do Github Advanced Security podem estar habilitadas por padrão. Prefira utilizar sua conta pessoal*
   - Recomendamos criar um repositório público, pois os privados consomem minutos do GitHub Actions, conforme explicado [aqui](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).
   - Role a página até o fim e clique no botão **Create repository**.
3. Depois que o repositório for criado, espere cerca de 20 segundos, atualize esta página e siga as instruções detalhadas no README do seu novo repositório.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---
Precisa de ajuda?:
- [Manda para gente!](https://github.com/fguisso/introducao-ao-code-scanning/discussions)
- [Github Skills: Post in our discussion board](https://github.com/orgs/skills/discussions/categories/introduction-to-codeql) &bull; 

&copy; 2023 GitHub • [Código de Conduta](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) • [Licença MIT](https://gh.io/mit)

</footer>