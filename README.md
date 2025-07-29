# Teste Técnico – Desenvolvedor Full Stack

## Descrição do Projeto
Este projeto é um teste técnico para desenvolvedor Full Stack, com foco em back-end Django e análise de dados. A aplicação web desenvolvida tem como objetivo gerenciar vagas e candidatos, permitindo o cadastro de vagas, cadastro e listagem de candidatos, associação de candidatos a vagas, e um dashboard com estatísticas de vagas e candidaturas. O projeto demonstra a aplicação de boas práticas de desenvolvimento com Django e a utilização de bibliotecas como Pandas para análise de dados e geração de relatórios.

## Requisitos

### 1. Modelagem (Banco de Dados com Django ORM)

Foram criados os seguintes modelos:

*   **Vaga**: Representa uma oportunidade de emprego.
    *   Campos: `título` (CharField), `setor` (CharField), `status` (CharField, com opções 'aberta'/'fechada'), `data_abertura` (DateField).

*   **Candidato**: Representa uma pessoa que busca uma vaga.
    *   Campos: `nome` (CharField), `e_mail` (EmailField), `data_nascimento` (DateField), `experiencia` (TextField).

*   **Candidatura**: Representa a associação de um candidato a uma vaga.
    *   Campos: `data` (DateField), `status_candidatura` (CharField, com opções 'pendente'/'aprovada'/'rejeitada').

**Relacionamentos:**

*   Um candidato pode se candidatar a várias vagas (Many-to-Many).
*   Uma vaga pode ter vários candidatos (Many-to-Many).

### 2. Administração e CRUD (via Django Admin ou Views/Forms)

*   **Interface para Gerenciamento**: Implementação de interfaces para criar, editar e excluir vagas e candidatos. Isso pode ser feito através do Django Admin, que oferece uma interface robusta e rápida para gerenciamento de dados, ou através de views e formulários personalizados para maior controle e personalização.

*   **Listagem de Candidaturas**: Uma página dedicada para listar todas as candidaturas existentes, permitindo uma visão geral das associações entre candidatos e vagas.

*   **Associação de Candidatos às Vagas**: Um formulário simples com dropdowns para facilitar a associação de candidatos a vagas específicas, garantindo uma experiência de usuário intuitiva.

### 3. Dashboard com Análise de Dados

Um dashboard foi desenvolvido para apresentar análises básicas de dados, utilizando a biblioteca Pandas para processamento e geração de relatórios. As seguintes métricas são exibidas:

*   **Total de Vagas Abertas/Fechadas**: Contagem das vagas com status 'aberta' e 'fechada'.
*   **Número de Candidatos por Vaga**: Quantidade de candidatos associados a cada vaga.
*   **Média de Idade dos Candidatos**: Cálculo da idade média dos candidatos cadastrados.
*   **Setor com Mais Vagas Abertas**: Identificação do setor que possui o maior número de vagas com status 'aberta'.

Os dados são apresentados em um template HTML simples para fácil visualização. Embora não obrigatório, a integração com bibliotecas como Plotly ou Chart.js para visualização gráfica pode ser considerada para aprimorar a apresentação dos dados.

## Instalação

Para configurar e executar o projeto localmente, siga os passos abaixo:

1.  **Clone o Repositório:**

    ```bash
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_DIRETORIO_DO_PROJETO>
    ```

2.  **Crie e Ative o Ambiente Virtual:**

    É altamente recomendável usar um ambiente virtual para isolar as dependências do projeto.

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # No Linux/macOS
    # venv\Scripts\activate  # No Windows
    ```

3.  **Instale as Dependências:**

    Com o ambiente virtual ativado, instale as bibliotecas Python necessárias usando o `pip`.

    ```bash
    pip install -r requirements.txt
    ```

    *Nota: Certifique-se de que o arquivo `requirements.txt` contenha todas as dependências do projeto (Django, Pandas, etc.). Você pode gerá-lo com `pip freeze > requirements.txt` após instalar as dependências.* 

4.  **Aplique as Migrações:**

    As migrações do Django criarão o esquema do banco de dados (SQLite por padrão).

    ```bash
    python manage.py migrate
    ```

5.  **Crie um Superusuário (Opcional, para acesso ao Django Admin):**

    ```bash
    python manage.py createsuperuser
    ```

    Siga as instruções no terminal para criar um nome de usuário e senha.

## Execução

Para iniciar o servidor de desenvolvimento Django e acessar a aplicação:

1.  **Inicie o Servidor de Desenvolvimento:**

    ```bash
    python manage.py runserver
    ```

    O servidor estará disponível em `http://127.0.0.1:8000/` por padrão.

2.  **Acesse a Aplicação:**

    *   **Página Inicial/Listagem de Vagas:** `http://127.0.0.1:8000/vagas/` (ou a rota configurada para a listagem de vagas).
    *   **Django Admin:** `http://127.0.0.1:8000/admin/` (utilize as credenciais do superusuário criado).
    *   **Dashboard de Análise de Dados:** `http://127.0.0.1:8000/dashboard/` (ou a rota configurada para o dashboard).

## Decisões Técnicas

### Framework Django

O Django foi escolhido como framework web principal devido à sua robustez, segurança e ao seu ORM (Object-Relational Mapper) que facilita a interação com o banco de dados. A estrutura de projeto do Django, com seus aplicativos modulares, contribui para a organização e escalabilidade do código. A utilização do Django Admin para as operações de CRUD (Create, Read, Update, Delete) de vagas e candidatos agiliza o desenvolvimento da interface administrativa, permitindo focar na lógica de negócio e na análise de dados.

### Análise de Dados com Pandas

A biblioteca Pandas foi selecionada para a análise de dados devido à sua eficiência e flexibilidade no tratamento de dados tabulares. Ela permite a manipulação, limpeza e agregação de dados de forma intuitiva, sendo ideal para a geração dos relatórios estatísticos solicitados no dashboard. A integração do Pandas com o Django ORM é feita através da conversão dos QuerySets em DataFrames, facilitando a aplicação das operações de análise.

### Estrutura do Código

A estrutura do projeto segue as convenções do Django, com a separação lógica em aplicativos (`apps`). Cada aplicativo (e.g., `vagas`, `candidatos`, `dashboard`) é responsável por um conjunto específico de funcionalidades, promovendo a modularidade e a manutenibilidade do código. Os modelos (`models.py`), views (`views.py`), URLs (`urls.py`) e templates (`templates/`) são organizados dentro de seus respectivos aplicativos.

## Avaliação

Este teste técnico será avaliado com base nos seguintes critérios:

*   **Estrutura e Organização do Código**: Clareza, modularidade e aderência às boas práticas de organização de projetos Django.
*   **Modelagem Adequada e Uso Correto do ORM**: Design dos modelos de banco de dados e utilização eficiente do Django ORM para relacionamentos e consultas.
*   **Clareza no Uso de Views, Templates e Rotas**: Lógica e organização das views, renderização dos templates e definição das rotas da aplicação.
*   **Aplicação de Boas Práticas com Git**: Histórico de commits claro, mensagens descritivas e uso adequado de branches (se aplicável).
*   **Lógica de Programação e Uso de Bibliotecas como Pandas**: Eficiência e correção da lógica implementada, especialmente na manipulação de dados com Pandas.
*   **Capacidade de Comunicar Dados de Forma Clara (Dashboard)**: Apresentação das estatísticas de forma compreensível e visualmente eficaz no dashboard.
*   **Autonomia e Atenção a Detalhes**: Demonstração de proatividade na resolução de problemas e cuidado com os detalhes na implementação.
