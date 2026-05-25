# Projeto Individual: Currículo Online DS881

Este repositório é um **template** para a atividade prática individual da disciplina DS881. O objetivo é aplicar conceitos de conteinerização, automação de pipeline CI/CD e governança de código em um cenário de projeto real (seu currículo ou portfólio profissional).

## Instruções para Início

Para iniciar o seu trabalho, siga estes passos:

1. Clique no botão verde **"Use this template"** e selecione **"Create a new repository"**.
2. Nomeie o repositório como `ds881-curriculo-GRR99999999`.
3. Certifique-se de que a visibilidade seja **Public**.
4. Configure a proteção da branch `main` imediatamente (instruções na seção 2.2).

---

## 1. Objetivos

Desenvolver e publicar um currículo profissional ou portfólio pessoal utilizando o GitHub Pages. O projeto deve demonstrar o domínio de ferramentas de conteinerização, automação de pipeline CI/CD e governança de código via fluxos de trabalho estruturados, mesmo em um ambiente de desenvolvimento individual.

## 2. Requisitos Técnicos

### 2.1. Tecnologia e Stack

- **Aplicação:** O site deve ser estático. É livre a escolha entre HTML/CSS puro ou o uso de geradores de site estático (SSG) como Astro, Hugo ou Jekyll.
- **Hospedagem:** O deploy final deve ser realizado obrigatoriamente no GitHub Pages.

### 2.2. Conteinerização do Ambiente de Desenvolvimento (Docker)

O repositório deve fornecer a infraestrutura necessária para que o projeto possa ser editado e testado localmente sem a exigência de instalar as linguagens ou dependências base (como Node.js ou Ruby) no sistema operacional do hospedeiro.

- **Dockerfile:** Deve especificar uma imagem base adequada (ex: `node:alpine` ou `ruby:alpine`) e preparar o ambiente com as ferramentas necessárias para executar o gerador de site estático escolhido.
- **Docker Compose (`docker-compose.yml`):** Deve ser configurado para iniciar o servidor de desenvolvimento nativo da ferramenta (ex: `vite dev`, `jekyll serve` ou `hugo server`).
- **Mapeamento de Volumes (Bind Mounts):** A configuração do Compose deve mapear o diretório local do código-fonte para o diretório de trabalho dentro do contêiner. Isso é obrigatório para garantir o funcionamento do _hot reload_ (atualização automática no navegador ao salvar um arquivo).
- **Portas:** O servidor de desenvolvimento dentro do contêiner deve ser mapeado para responder na porta `8080` do localhost da máquina hospedeira.

### 2.3. Workflow de Git e Governança

Apesar de ser um projeto individual, o projeto deve seguir as boas prática do desenvolvimento com git:

- **Proteção de Branch:** A branch `main` deve estar configurada como protegida nas configurações do repositório.
- **Fluxo de Trabalho:** É proibido realizar _push_ direto na `main`. Toda alteração deve ser feita em uma branch secundária (ex: `feat/nome-da-feature`) e integrada via **Pull Request (PR)**.
- **Critérios de Merge:** O merge para a `main` só deve ser permitido se o pipeline de CI estiver com status "verde" (sucesso).
- **Mensagens de Commit:** Devem seguir o padrão _Conventional Commits_ (ex: `feat:`, `fix:`, `ci:`, `docs:`).

### 2.4. CI/CD (GitHub Actions)

Implementação de um workflow automatizado (`.github/workflows/main.yml`) contendo:

1.  **Linter/Static Analysis:** Verificação de sintaxe e padrões de código.
2.  **Build:** Validação de que a aplicação compila corretamente dentro do ambiente de CI.
3.  **Deploy:** Publicação automatizada no GitHub Pages disparada após o merge na branch `main`.

## 3. Documentação

### 3.1. Link Público do Currículo

O currículo está disponível publicamente no GitHub Pages através do seguinte link: **[https://humanaice.github.io/ds881-curriculo-GRR20230998/](https://humanaice.github.io/ds881-curriculo-GRR20230998/)**

### 3.2. Execução do Ambiente Local com Docker

Para configurar e executar o ambiente de desenvolvimento localmente usando Docker, siga os passos abaixo:

1.  **Pré-requisitos:** Certifique-se de ter o Docker e Docker Compose instalados em sua máquina.
2.  **Navegue até o diretório do projeto:**
    ```bash
    cd ds881-curriculo-GRR20230998
    ```
3.  **Inicie o ambiente Docker Compose:**
    ```bash
    docker compose up --build
    ```
    Este comando irá construir a imagem Docker (se necessário) e iniciar o contêiner do servidor de desenvolvimento.
4.  **Acesse o currículo:** Após a inicialização, o site estará acessível no seu navegador através da URL: `http://localhost:8080`.
    Qualquer alteração nos arquivos `.html` ou `.css` será automaticamente refletida no navegador devido ao mapeamento de volumes (hot reload).

### 3.3. Proteção da Branch `main`

A branch `main` está configurada com proteção para garantir a governança do código. As seguintes regras foram aplicadas:

- **Require a pull request before merging:** Todas as alterações devem ser feitas via Pull Request.
- **Require status checks to pass before merging:** O merge só é permitido se o pipeline de CI/CD estiver com status "verde".

Abaixo estão os prints da configuração de proteção da branch `main` no GitHub:

<img width="1717" height="2135" alt="Image" src="https://github.com/user-attachments/assets/8200b204-cb6c-4d22-b175-8a10b9c48389" />

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/1480d4db-c770-460b-950f-52a49abc0f83" />

## 4. Critérios de Avaliação

| Item                                                  | Peso |
| :---------------------------------------------------- | :--- |
| Configuração correta de Docker (Dockerfile e Compose) | 30%  |
| Pipeline de CI/CD funcional (Lint, Build e Deploy)    | 30%  |
| Evidência de uso de Pull Requests e Branch Protection | 20%  |
| Qualidade da documentação e histórico de commits      | 10%  |
| Funcionamento da aplicação no GitHub Pages            | 10%  |

---

## 5. Entrega e Avaliação

A entrega deve ser realizada através do formulário disponibilizado pelo professor, contendo o link do seu repositório público.

---
