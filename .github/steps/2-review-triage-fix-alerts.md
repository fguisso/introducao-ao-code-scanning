<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-2-notes.
-->
## Passo 2: Revisar e Triar Alertas do CodeQL

_Parabéns! Você colocou o CodeQL para funcionar! :tada:_

Neste exercício, vamos revisar os resultados da scan do CodeQL e triagem de um alerta.

**O que é o GitHub Actions**:  
O GitHub Actions é a plataforma de automação e CI/CD integrada ao GitHub. Utilizamos o GitHub Actions para orquestrar e executar scans de segurança com o code scanning. É uma plataforma de integração e entrega contínua (CI/CD) que permite automatizar seu pipeline de build, teste e deploy. Para mais informações, veja "[Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)".

**O que é CWE**:  
Common Weakness Enumeration (CWE) é um sistema de categorização para fraquezas e vulnerabilidades em hardware e software. Pense nele como uma forma de descrever e classificar problemas de segurança no código fonte de uma aplicação. Para mais detalhes, consulte o artigo da Wikipedia "[Common Weakness Enumeration](https://en.wikipedia.org/wiki/Common_Weakness_Enumeration)".

### :keyboard: Atividade 1: Visualizar o status de uma scan CodeQL

Nesta atividade, vamos explorar o GitHub Actions para visualizar o status de uma scan do CodeQL.  
1. No seu novo repositório, acesse a página selecionando **Actions** na barra de navegação superior. Se a execução da action CodeQL ainda estiver em andamento, você verá um spinner amarelo indicando que o scan está em progresso. Geralmente, isso leva cerca de 4 minutos.
2. Selecione a execução clicando em **CodeQL Setup**.

![codeql-setup](/images/codeql-setup.png)

Note que mais informações estão disponíveis dentro da execução das Actions. Sinta-se à vontade para explorar essa seção e visualizar informações como os logs do CodeQL, duração, status e artefatos gerados.

Após a conclusão da scan, um ícone de check verde aparecerá ao lado da execução.

### :keyboard: Atividade 2: Visualizar todos os Alertas do CodeQL

Nesta atividade, vamos visualizar os resultados do CodeQL na página **Security**(Segurança) do seu repositório. Essa página exibe todas as informações relacionadas à segurança.

1. Navegue até a aba **Security** na barra de navegação superior do seu repositório.
2. Selecione **Code scanning** sob o título *"Vulnerability alerts"* na barra lateral esquerda.

Nesta tela, estarão listadas todas as vulnerabilidades identificadas pelo CodeQL no código deste repositório. Explore os diferentes filtros e recursos de busca desta página. Essas capacidades de filtragem são muito úteis quando você está trabalhando com muitas descobertas!

### :keyboard: Atividade 3: Revisar um Alerta

Nesta atividade, vamos explorar a interface do alerta. Vamos revisar o fluxo de dados da vulnerabilidade, identificar qual parte do código o alerta impacta e obter mais informações sobre o alerta.

**Status do alerta:**
Esta seção exibe o status atual do alerta (aberto ou fechado), identifica a branch onde o scan detectou o alerta e mostra o timestamp do alerta.
  
![alert-status](/images/alert-status.png)

**Informações de localização:**
Esta seção descreve qual parte do código está vulnerável.
  
![location-information](/images/location-information.png)

**Caminhos:**  
Ao clicar em "Show paths" (Exibir caminhos), você obterá insights adicionais sobre o fluxo de dados relacionado ao alerta. A janela modal mostra onde a entrada do usuário (chamada de "source") flui pela aplicação até ser processada (chamada de "sink"). Isso ilustra o fluxo de dados em sua aplicação.

**Recomendações:**  
Esta seção fornece uma visão geral rápida da ferramenta (neste caso, o CodeQL), o ID da regra e permite visualizar a consulta CodeQL utilizada para encontrar essa vulnerabilidade. Você pode visualizar a consulta clicando em **View source**. Além disso, este painel inclui recomendações para corrigir a vulnerabilidade. Clique em **Show more** (Mostrar mais) para ver a recomendação completa.

![recommendations](/images/recommendations.png)

**Rastro de auditoria:**  
O rastro de auditoria mostra o histórico do alerta. Ele exibirá o status conforme os usuários marcam um alerta como fechado ou corrigem o alerta no código.

![audit-trail](/images/audit-trail.png)

**Triagem do alerta:**  
Utilize os botões no canto superior direito do alerta para triá-lo como *resolvido, falso positivo ou aceito*. Por enquanto, não faça nada. Em breve, explicaremos esses botões. 😄

**Informações adicionais:**  
Por fim, o painel à direita contém informações como tags, detalhes sobre CWE e a severidade do alerta.
  
![additional-information.png](/images/additional-information.png)

### :keyboard: Atividade 4: Descartar um Alerta

Agora que você já está familiarizado com o layout do alerta, vamos praticar o processo de encerramento de um alerta.

1. Dentro do mesmo alerta, clique em **Dismiss alert** (Descartar alerta), escolha um motivo para o descarte e adicione uma breve anotação.*Esta anotação é muito importante para seus companheiros ou até mesmo para o time de segurança da sua empresa manterem uma boa comunicação.*
2. Clique em **Dismiss alert**.
3. Neste momento, o alerta mudará seu estado para "Dismissed" (Descartado). Você poderá ver essa alteração no rastro de auditoria na parte inferior do alerta.
4. Volte para **Security** > **Code scanning alerts**. Você verá que agora há apenas 1 alerta listado.
5. Clique em **1 Closed**. Isso o levará à lista de alertas fechados, onde você pode visualizar o alerta que acabou de fechar.

   ![one-closed-alert.png](/images/one-closed-alert.png)

6. (Opcional) Você também pode reabrir o alerta selecionando **Reopen alert** (Reabrir alerta).

## Passo 3: Corrigir Vulnerabilidades de Segurança

Neste passo, vamos trabalhar para corrigir as vulnerabilidades de segurança existentes identificadas pelo CodeQL. Lembre-se, neste ponto, já introduzimos o CodeQL em nosso repositório e o fizemos scannear o código atual. As vulnerabilidades encontradas são problemas do mundo real e precisam ser corrigidas! Vamos resolver essa questão editando o arquivo `/server/routes.py`.

### :keyboard: Atividade 1: Revisar alertas

Primeiro, antes de corrigir esses alertas, precisamos garantir que eles ainda estejam abertos. Também precisaremos coletar informações sobre quais arquivos corrigir e a melhor forma de fazê-lo.

1. Navegue até a página de alertas do code scanning: **Security** > **Code scanning**.
2. Você deverá ver dois alertas listados como "**Open**". Se algum dos alertas estiver listado como "**Closed**", abra a página do alerta e escolha **Reopen alert**.

Agora que ambos os alertas estão abertos, vamos corrigi-los. Se você observar os alertas, ambos apontam para um arquivo específico contendo os problemas: `server/routes.py`. O problema está na construção da consulta SQL para o banco de dados. Essas consultas estão vulneráveis a ataques de injeção de SQL. Devemos reescrever essas instruções SQL de forma mais segura.

Se você expandir a seção **More info** (Mais informações) no final do alerta, encontrará sugestões bem claras para corrigir essa consulta. Vamos implementar essas sugestões na próxima atividade.

### :keyboard: Atividade 2: Editar routes.py

Agora que sabemos onde estão os problemas e como corrigi-los, vamos começar modificando o arquivo `routes.py`. Novamente, recomenda-se realizar esses passos em uma nova janela ou aba do navegador.

1. Clique na aba **Code** do seu repositório.
2. Selecione a pasta `server`.
3. Selecione o arquivo `routes.py`.
4. Clique no botão **Edit** (Editar) à direita.

   ![edit-button.png](/images/edit-button.png)

5. Edite a linha 13, destacando a instrução SQL, e substitua por este texto:  
   `"SELECT * FROM books WHERE name LIKE ?", (f"%{name}%",)`.
6. Edite a linha 19 para substituir a instrução SQL pelo seguinte texto:  
   `"SELECT * FROM books WHERE author LIKE ?", (f"%{author}%",)`.
7. Clique em **Commit changes...** (Confirmar alterações) no canto superior direito. A janela "Propose changes" (Propor alterações) aparecerá. Deixe as configurações padrão e clique novamente em **Commit changes**.
8. O CodeQL iniciará uma nova varredura. Verifique o status dessa varredura navegando até **Actions** e escolhendo a ação **CodeQL**. Assim que o trabalho da varredura for concluído, o Actions exibirá um ícone de check verde ao lado da última execução.
9. Quando a varredura do CodeQL terminar, navegue até **Security** > **Code scanning** para revisar os alertas. Você deverá ver zero alertas abertos e dois alertas fechados 🎉. Sinta-se à vontade para revisar os alertas fechados, especialmente o rastro de auditoria.
10. Aguarde cerca de 20 segundos e, em seguida, atualize esta página (aquela em que você está seguindo as instruções). O [GitHub Actions](https://docs.github.com/en/actions) atualizará automaticamente para o próximo passo.
