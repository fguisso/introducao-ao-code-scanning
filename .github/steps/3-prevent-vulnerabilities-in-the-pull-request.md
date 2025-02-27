<!--
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-4-notes.
-->

## Passo 4: Prevenir Vulnerabilidades no Pull Request

_Bom trabalho! Você concluiu o Passo 3: Corrigir Vulnerabilidades de Segurança!_

Muito bem! Você chegou até aqui. Estamos quase terminando! O último passo é testar a integração do pull request com o CodeQL. Nesta etapa, vamos reintroduzir uma vulnerabilidade no arquivo `routes.py` para disparar um alerta de vulnerabilidade de injeção de SQL. Trata-se do mesmo problema que vimos inicialmente.

Nosso objetivo é compreender a experiência dos desenvolvedores ao encontrar uma nova vulnerabilidade.

Neste passo, nós iremos:
- Editar o arquivo `routes.py`.
- Alterar a instrução SQL para torná-la insegura.
- Confirmar essas alterações e mesclar o código inseguro na branch principal.
- Experimentar o alerta dentro de um pull request.

Vamos começar 👍

**O que é pull request**:  
Pull requests são propostas de alterações em um repositório submetidas por um usuário e aceitas ou rejeitadas pelos colaboradores do repositório. Isso permite que várias pessoas trabalhem no mesmo código ao mesmo tempo. Para mais informações, confira o curso GitHub Skills "[Introduction to GitHub](https://github.com/skills/introduction-to-github)" ou a seção "[About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)" na documentação do GitHub.

**O que é branch**:  
Uma branch é uma versão paralela do seu repositório. Por padrão, seu repositório possui uma branch chamada `main`, que é considerada a branch principal. Criar branches adicionais permite que você copie a branch principal do seu repositório e realize alterações de forma segura, sem comprometer o projeto principal. Para mais informações, veja "[About branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#)" na documentação do GitHub.

### :keyboard: Atividade 1: Editar `routes.py` e criar um novo pull request

Nesta primeira atividade, vamos introduzir a mesma instrução SQL insegura que vimos anteriormente no arquivo `routes.py`. Assim que atualizarmos o arquivo, faremos o commit das alterações em uma nova branch e criaremos um pull request.

1. Clique na aba **Code** do seu repositório.
2. Selecione a pasta `server`.
3. Selecione o arquivo `routes.py`.
4. Clique no botão **Edit** (Editar) à direita.

   ![edit-button.png](/images/edit-button.png)

5. Edite a linha 16, destacando a instrução SQL, e substitua por este texto:  
   `"SELECT * FROM books WHERE name LIKE '%" + name + "%'"`.
6. Clique em **Commit changes...** no canto superior direito. A janela "Propose changes" (Propor alterações) aparecerá.
7. Desta vez, selecione o botão de opção ao lado de **Create a new branch**. Você pode criar um novo nome para essa branch ou deixar a sugestão padrão.
8. Clique em **Propose changes**. Isso abrirá um novo pull request.
9. Na janela "Open a pull request" (Abrir um pull request), clique em **Create pull request**.

### :keyboard: Atividade 2: Revisar o pull request

Neste ponto, editamos o arquivo `routes.py` para adicionar nosso código vulnerável, fizemos o commit das alterações em nossa nova branch e criamos um pull request para mesclar a nova branch na branch `main`. Esses são os mesmos passos que um desenvolvedor tomaria para introduzir novos códigos em um repositório.

Agora, vamos dar uma olhada no pull request para ver como é a experiência:

1. Na atividade anterior, criamos o pull request. Após a criação, você foi levado diretamente para a página do pull request. No final da página, você verá uma verificação chamada "Code scanning/CodeQL". Essa é a ação do CodeQL analisando o código introduzido no pull request.

   ![pr-panel](/images/pr-panel.png)

2. Assim que a verificação for concluída, você verá um novo comentário no pull request do CodeQL indicando uma nova vulnerabilidade de segurança: uma consulta SQL construída a partir de dados controlados pelo usuário. Essa é nossa vulnerabilidade de injeção de SQL.

   <img width="1180" alt="image" src="https://github.com/leftrightleft/enable-code-scanning/assets/4910518/378bd766-ef61-4619-ab3c-bf2c8d9618d7">

3. Revise os caminhos do fluxo de dados clicando em **Show paths** (Exibir caminhos).
4. Se desejar, adicione um comentário e marque um de seus amigos usando o handle do GitHub (por exemplo, `@username`). Isso notificará a pessoa de que você comentou no problema e precisa da ajuda dela para resolver o problema. 😄

Se isto fosse uma situação real, o desenvolvedor corrigiria a instrução SQL em sua branch. Uma vez corrigida, a vulnerabilidade seria automaticamente encerrada.

Se você quiser saber mais sobre integrações de pull request para code scanning, consulte "[Triaging code scanning alerts in pull requests](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/triaging-code-scanning-alerts-in-pull-requests)".

5. Aguarde cerca de 20 segundos e, em seguida, atualize esta página (aquela em que você está seguindo as instruções). O [GitHub Actions](https://docs.github.com/en/actions) atualizará automaticamente para o próximo passo.