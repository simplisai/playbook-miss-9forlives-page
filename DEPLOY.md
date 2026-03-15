# Guia de Deploy no Netlify (9forLives Playbook)

Este guia contém as instruções e melhores práticas para publicar o Playbook do Missionário no Netlify, garantindo que a navegação e o redirecionamento funcionem perfeitamente.

## Estrutura Preparada para Deploy

Os seguintes arquivos foram configurados para garantir o funcionamento correto:

1.  **`index.html`**: Configurado para redirecionar automaticamente o acesso da raiz (`/`) para a versão em português (`/playbook-mis-pt.html`).
2.  **`_redirects`**: Arquivo de configuração nativo do Netlify para garantir redirecionamentos do lado do servidor (Server-Side Redirects), o que é mais rápido e confiável que o redirecionamento via HTML/JS.
    *   `/` -> `/playbook-mis-pt.html`
    *   `/pt` -> `/playbook-mis-pt.html` (atalho)
    *   `/en` -> `/playbook-mis-en.html` (atalho)

## Passo a Passo para Deploy

### Opção 1: Netlify Drop (Mais Simples)

1.  Acesse [app.netlify.com/drop](https://app.netlify.com/drop).
2.  Arraste a pasta inteira do projeto (`playbook-miss-9forlives-page`) para a área indicada na tela.
3.  O Netlify fará o upload e publicará o site instantaneamente.
4.  O link temporário será gerado (ex: `https://brave-curie-123456.netlify.app`).

### Opção 2: Via Git (Recomendado para Manutenção)

1.  Suba este repositório para o GitHub, GitLab ou Bitbucket.
2.  No painel do Netlify, clique em **"Add new site"** > **"Import an existing project"**.
3.  Conecte seu provedor Git e selecione o repositório.
4.  **Configurações de Build:**
    *   **Build command:** (Deixe em branco, pois é um site estático HTML puro)
    *   **Publish directory:** (Deixe em branco ou coloque `.` se ele pedir)
5.  Clique em **"Deploy site"**.

## Verificação Pós-Deploy

Após o site estar no ar, teste os seguintes cenários para garantir que tudo está 100%:

1.  **Acesso à Raiz:** Acesse `https://seu-dominio.netlify.app/`.
    *   *Resultado esperado:* Você deve ser redirecionado automaticamente para `/playbook-mis-pt.html`.
2.  **Troca de Idioma:** Clique no botão "EN" no canto superior direito.
    *   *Resultado esperado:* A página deve mudar para a versão em inglês (`/playbook-mis-en.html`).
3.  **Navegação Mobile:** Abra no celular e teste o menu "hambúrguer".
    *   *Resultado esperado:* O menu lateral deve abrir e fechar corretamente.
4.  **Links Diretos:** Teste acessar `https://seu-dominio.netlify.app/en`.
    *   *Resultado esperado:* Deve redirecionar para a versão em inglês.

## Melhores Práticas Aplicadas

*   **Cache Control:** O Netlify gerencia o cache automaticamente para arquivos HTML, garantindo que os usuários sempre vejam a versão mais recente após um novo deploy.
*   **Asset Optimization:** O Netlify otimiza imagens e arquivos estáticos automaticamente (se a opção estiver ativada no painel, o que é padrão).
*   **Clean URLs:** O arquivo `_redirects` garante que a estrutura de URL seja amigável e previne erros 404 na raiz.
