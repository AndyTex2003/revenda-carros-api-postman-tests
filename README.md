# Automação de Testes de API REST — Revenda de Carros

Projeto de automação de testes de API REST desenvolvido com Postman e JavaScript, utilizando Newman para execução automatizada e HTMExtra para geração de relatórios HTML.

## Sobre o projeto

Este projeto surgiu a partir de uma API de revenda de carros desenvolvida anteriormente como parte de um projeto de portfólio.

Com a API já implementada, o objetivo foi reutilizá-la para construir uma suíte de testes automatizados, aplicando conceitos e boas práticas de Quality Assurance (QA).

Os testes foram organizados por módulos, contemplando cenários positivos, negativos e validações de regras de negócio, com foco na confiabilidade, organização e repetibilidade das execuções.

## Tecnologias utilizadas

| Tecnologia | Finalidade |
|------------|------------|
| Postman | Criação, organização e execução dos testes de API |
| JavaScript | Implementação de assertions e scripts de automação |
| Newman | Execução automatizada das collections pelo terminal |
| Node.js e npm | Gerenciamento das dependências e execução dos scripts |
| HTMExtra | Geração de relatórios HTML das execuções |
| Git e GitHub | Versionamento, organização de branches e Pull Requests |

## Cobertura dos testes

A suíte de testes automatizados está organizada em cinco módulos, permitindo validar diferentes funcionalidades da API de Revenda de Carros.

| Módulo | Cobertura |
|--------|-----------|
| Health | Verificação da disponibilidade e funcionamento da API |
| Autenticação | Login, validação de tokens e controle de acesso |
| Veículos | Operações de cadastro, consulta, atualização e exclusão |
| Clientes | Operações de cadastro, consulta, atualização e exclusão |
| Vendas | Validação dos fluxos e regras de negócio relacionados às vendas |

### Tipos de cenários

A automação contempla:

- **Cenários positivos:** validação de operações realizadas com dados válidos.
- **Cenários negativos:** verificação do comportamento da API diante de dados inválidos ou requisições não autorizadas.
- **Validação de status HTTP:** conferência dos códigos de resposta esperados.
- **Validação de respostas:** assertions sobre os dados retornados pela API.
- **Controle de massa de dados:** utilização de variáveis e requisições de preparação e limpeza para apoiar a execução dos testes.


## Estrutura do projeto

```text
revenda-carros-api-postman-tests/
├── collections/
│   └── revenda-carros-api.postman_collection.json
├── environments/
│   └── local.postman_environment.json
├── reports/
│   └── newman-report.html
├── .gitignore
├── README.md
├── package.json
└── package-lock.json
```

### Descrição dos arquivos e diretórios

- **collections/**: contém a collection do Postman com os testes automatizados da API.
- **environments/**: armazena as variáveis do ambiente local utilizadas durante os testes.
- **reports/**: contém o relatório HTML gerado após a execução com Newman.
- **package.json**: define as dependências e os scripts npm para execução dos testes.
- **package-lock.json**: registra as versões das dependências instaladas.
- **.gitignore**: impede o versionamento de arquivos locais, dependências instaladas e relatórios gerados.

> **Importante:** os arquivos locais de ambiente e os relatórios HTML não são versionados no GitHub. O ambiente deve ser configurado antes da execução dos testes.


## Pré-requisitos

Para executar os testes automatizados, é necessário:

- **Node.js e npm** instalados no computador.
- **API Revenda de Carros** configurada e em execução localmente.
- **Ambiente local do Postman** configurado com as variáveis necessárias para os testes.

A API utilizada neste projeto está disponível em:

https://github.com/AndyTex2003/revenda-carros-api

Por padrão, os testes utilizam a API em:

`http://localhost:3000`

> **Atenção:** a API deve estar em execução antes de iniciar os testes. O arquivo `environments/local.postman_environment.json` deve ser configurado localmente e não deve conter credenciais ou tokens publicados no repositório.


## Instalação e execução dos testes

### 1. Clonar o repositório

```bash
git clone https://github.com/AndyTex2003/revenda-carros-api-postman-tests.git
```

Acesse o diretório do projeto:

```bash
cd revenda-carros-api-postman-tests
```

### 2. Instalar as dependências

```bash
npm ci
```

Esse comando instala as dependências registradas no `package-lock.json`, incluindo Newman e HTMExtra.

### 3. Configurar o ambiente

Crie e configure localmente o arquivo:

`environments/local.postman_environment.json`

O arquivo deve conter as variáveis necessárias à execução da collection, incluindo a URL base da API e os dados de autenticação utilizados nos testes.

Por segurança, não publique credenciais ou tokens no repositório.

### 4. Executar os testes

Com a API em execução, utilize:

```bash
npm test
```

Esse comando executa a collection do Postman utilizando o Newman e apresenta os resultados diretamente no terminal.

### 5. Executar os testes com relatório HTML

Para executar os testes e gerar o relatório HTML:

```bash
npm run test:report
```

O relatório será gerado em:

`reports/newman-report.html`

Abra esse arquivo no navegador para visualizar os resultados da execução.


## Resultados da execução

A suíte de testes foi executada localmente utilizando Newman, com os seguintes resultados:

| Métrica | Resultado |
|---------|-----------|
| Requisições executadas | 60 |
| Assertions executadas | 228 |
| Assertions com falha | 0 |
| Testes ignorados | 0 |

**Resultado:** todos os testes foram aprovados na última execução validada.

### Relatório HTML

O projeto utiliza o reporter HTMExtra para gerar um relatório HTML com informações detalhadas sobre a execução dos testes.

O relatório permite consultar:

- Resumo geral da execução.
- Quantidade de requisições e assertions.
- Testes aprovados e reprovados.
- Tempo de execução e tempos de resposta.
- Detalhes das requisições executadas.

Para gerar um novo relatório, execute:

```bash
npm run test:report
```

O arquivo será salvo em `reports/newman-report.html`.

> **Observação:** os resultados apresentados correspondem à última execução local validada. Eles podem variar conforme o estado da API, os dados utilizados e as alterações realizadas nos testes.
