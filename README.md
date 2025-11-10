# 🚀 Testes de API Automatizados com Postman e Newman

## 🎯 Sobre o Projeto

Este repositório foi criado como parte do aprendizado do curso **"Dominando Postman (2025): Do Teste Manual a Performance APIs"** do Qualiters Club (Priscila Caimi).

O objetivo principal é demonstrar a capacidade de:
* Realizar **Testes Funcionais** e **Testes de Performance** em APIs REST.
* **Automatizar** a execução de coleções Postman através de linha de comando.
* Implementar um **Pipeline CI/CD** para execução automática dos testes com o Newman.

## 🛠️ Tecnologias e Ferramentas

As seguintes ferramentas foram utilizadas neste projeto:

* **[Postman](https://www.postman.com/):** Criação e gerenciamento das coleções de requisições e scripts de teste (JavaScript).
* **[Newman](https://www.npmjs.com/package/newman):** Executor de linha de comando do Postman para automação.
* **[Newman HTML Extra Reporter](https://www.npmjs.com/package/newman-reporter-htmlextra):** Geração de relatórios HTML detalhados e amigáveis.
* **[GitHub Actions](https://docs.github.com/en/actions):** Implementação de um pipeline de Integração Contínua (CI) para executar os testes a cada *push*.
* **APIs Alvo:** Exemplos práticos utilizando APIs **REST** e **GraphQL**.

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
    * *Substitua o nome do arquivo da sua coleção e environment, se necessário.*
    ```bash
    newman run ./collections/MinhaColecaoDeTestes.json -e ./environments/MeuAmbiente.json -r htmlextra --reporter-htmlextra-export ./reports/report.html
    ```
4.  **Visualize o Relatório:**
    Abra o arquivo `reports/report.html` no seu navegador para ver os resultados detalhados.

## 💻 Automação (Pipeline CI/CD)

Os testes estão integrados a um pipeline de **Integração Contínua (CI)** com o GitHub Actions.

* A cada novo *push* para o branch principal (`main` ou `master`), os testes são executados automaticamente.
* Os **relatórios HTML** gerados pelo Newman são armazenados como **artefatos** da *build* para que possam ser baixados e consultados a qualquer momento.

<details>
  <summary>Visualizar a Configuração do Pipeline</summary>

  O arquivo de configuração do pipeline se encontra em: `.github/workflows/main.yml`
</details>
