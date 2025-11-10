# 🚀 Dominando testes de API com Postman e Newman: Execução, Performance e Geração de relatorios.

## 🎯 Sobre o Projeto

Este repositório foi criado como parte do resultado direto da conclusão do curso "[Dominando Postman: Do Teste Manual a Performance APIs](https://www.udemy.com/course/dominando-postman-2023-testando-e-automatizado-apis)" na Udemy, ministrado pela Priscila Caimi no Qualiters Club.

O objetivo principal é consolidar e demonstrar proficiência no ciclo completo de testes de API:
* **Testes Abrangentes:** Criação e execução de **Testes Funcionais**, **Automatizados** e de **Performance** em APIs REST e GraphQL.
* **Automação:** Utilização do **Newman** para execução de coleções Postman via linha de comando.
* **Relatórios:** Geração de relatórios de testes profissionais utilizando o `newman-reporter-htmlextra`.
* **Integração Contínua (CI/CD):** Implementação de um **Pipeline** com GitHub Actions para execução automática dos testes e persistência dos relatórios.

## ⚙️ Estrutura do Repositório

O projeto está organizado para facilitar a navegação e execução:

```text
.
├── .github/workflows/
│   └── main.yml        # Configuração do pipeline CI/CD (GitHub Actions).
├── collections/
│   └── ServeRest.postman_collection.json # Arquivos .json exportados do Postman com as requisições e testes.
├── environments/
│   └── serveRest_env.postman_environment.json # Arquivos .json com variáveis de ambiente (URLs, tokens, etc.).
├── reports/
│   └── report.html     # Diretório para salvar os relatórios de execução local.
└── README.md
```

## 🛠️ Tecnologias e Ferramentas

As seguintes ferramentas foram utilizadas neste projeto:

* **[Postman](https://www.postman.com/):** Criação e organização das coleções de requisições, variáveis de ambiente e scripts de teste (com JavaScript).
* **[Node.js](https://nodejs.org/pt)** Ambiente de execução e gerenciamento de dependências para Newman.
* **[Newman](https://www.npmjs.com/package/newman):** Executor de linha de comando para as coleções do Postman, incluindo a geração de relatorios.
* **[Newman HTML Extra Reporter](https://www.npmjs.com/package/newman-reporter-htmlextra):** Geração de relatórios HTML detalhados e amigáveis.
* **[GitHub Actions](https://docs.github.com/en/actions):** Implementação de um pipeline de Integração Contínua (CI) para executar os testes a cada *push*.
* **APIs de exemplo:** Utilização de APIs públicas e/ou simuladas para a prática de testes em APIs REST e GraphQL.

## ⚙️ Como Executar os Testes Localmente

Siga os passos para rodar a coleção de testes em sua máquina:

### Pré-requisitos
* [Node.js](https://nodejs.org/) (Necessário para instalar o Newman)
* [Postman](https://www.postman.com/downloads/) (Opcional, para visualização e edição das coleções)

### Instalação e Execução
1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/SEU_USUARIO/testes-api-postman-newman.git](https://github.com/SEU_USUARIO/testes-api-postman-newman.git)
    cd testes-api-postman-newman
    ```
2.  **Instale o Newman e o htmlextra (Globalmente ou no projeto):**
    ```bash
    npm install -g newman newman-reporter-htmlextra
    ```
3.  **Execute a coleção de testes:**
    ```bash
    newman run collections/ServeRest.postman_collection.json -e environments/serveRest_env.postman_environment.json -r htmlextra --reporter-htmlextra-export ./reports/report.html
    ```
4.  **Visualize o Relatório:**
    Abra o arquivo `reports/report.html` no seu navegador para ver os resultados detalhados.

## ☁️ Automação (Pipeline CI/CD)

Os testes estão integrados a um pipeline de **Integração Contínua (CI)** com o GitHub Actions.

* A cada novo *push* para o branch principal (`main`), os testes são executados automaticamente.
* Os **relatórios HTML** gerados pelo Newman são armazenados como **artefatos** da *build* para que possam ser baixados e consultados a qualquer momento.

- O pipeline foi configurado para executar os testes automaticamente:
  - O workflow é acionado a cada push para o branch principal.
  - O Node.js é configurado, e o Newman é instalado.
  - A coleção é executada, e o relatório HTML é gerado.
  - O relatório HTML é armazenado como um artefato de build do GitHub Actions, permitindo a consulta dos resultados sem a necessidade de rodar o Newman localmente.
