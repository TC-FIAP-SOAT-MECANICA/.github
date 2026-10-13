# Tech Challenge FIAP — Pós-Graduação em Software Architecture

### 📄 [Documentação Oficial do Desafio](https://docs.google.com/document/)
### 🎥 Vídeo de Apresentação — [YouTube](https://youtu.be/)

---

## 🏗️ Arquitetura de Microsserviços — Sistema de Gerenciamento de Oficina Mecânica

### 📌 Descrição da Arquitetura

Este projeto foi desenvolvido como parte do Tech Challenge da FIAP, no curso de Pós-Graduação em Software Architecture, com foco na aplicação de conceitos de arquitetura de software em um sistema de gerenciamento de oficina mecânica.

A solução foi concebida com base nos seguintes pilares arquiteturais:

- **Java 21:** linguagem utilizada no desenvolvimento da aplicação.
- **Clean Architecture:** organização das responsabilidades e separação das regras de negócio das tecnologias externas.
- **API First:** definição dos contratos das APIs como parte central do processo de desenvolvimento.

A implementação atual concentra as funcionalidades em um único serviço, estruturado para facilitar a manutenção, a evolução e a futura expansão da solução.

### 🧩 Microsserviços

#### 🔹 `ms-mecanica`

Responsável pelo gerenciamento das principais funcionalidades do sistema:

- Cadastro e gerenciamento de clientes pessoa física (PF) e pessoa jurídica (PJ).
- Cadastro e gerenciamento de veículos, incluindo placa, marca, modelo e ano.
- Controle de estoque de peças e insumos.
- Autenticação e autorização de usuários, incluindo clientes, mecânicos e administradores.
- Consulta detalhada de atendimentos, com organização por prioridade.
- Acompanhamento do progresso e do status dos serviços.
- Demais funcionalidades relacionadas à operação e ao gerenciamento da oficina mecânica.

O serviço foi desenvolvido com **Java 21** e **Spring Boot**, utilizando os recursos do ecossistema Spring para injeção de dependências, persistência de dados e exposição de endpoints REST.

---

## ⚙️ Tecnologias Utilizadas

- **Linguagem e framework:** Java 21 e Spring Boot.
- **Persistência de dados:** Spring Data JPA.
- **Gerenciamento de dependências:** Maven e/ou Gradle, conforme a configuração do projeto.
- **Banco de dados:**
  - MySQL 8.3, executado em container Docker.
  - H2, utilizado para testes e execução em ambiente local, conforme a configuração.
- **Documentação de APIs:** OpenAPI/Swagger, alinhada à abordagem API First.
- **Mapeamento de objetos:** MapStruct, para conversão entre entidades e DTOs.
- **Redução de código repetitivo:** Lombok.
- **Controle de versão:** Git.
- **Conteinerização e ambiente local:** Docker e Docker Compose.
- **Testes:** JUnit 5, Mockito e Postman.

---

## 🧪 Estratégia de Testes

A estratégia de testes contempla a validação das regras de negócio e dos endpoints disponibilizados pela aplicação.

- **Testes unitários:** JUnit 5 e Mockito, para validar comportamentos e regras de negócio de forma isolada.
- **Testes de API:** Postman, para validar requisições, respostas e os contratos dos endpoints REST, por meio de collections manuais ou automatizadas.
- **Testes de persistência:** utilização do H2 e/ou do banco configurado para validar os comportamentos de acesso a dados, conforme a implementação.

---

## 📊 Diagramas da Arquitetura

Os diagramas do projeto serão disponibilizados na pasta `images/` do repositório.

### Diagrama da Arquitetura

![Diagrama da Arquitetura](images/diagrama-arquitetura.svg)

### Outros diagramas

Conforme a evolução do projeto, esta seção poderá incluir diagramas complementares para representar a organização interna da aplicação, os principais fluxos de negócio e as interações entre seus componentes.

---

## 🐳 Execução do Projeto com Docker Compose

### ✅ Pré-requisitos

Antes de executar os scripts de inicialização, instale os seguintes softwares:

| Requisito | Descrição |
|---|---|
| [Docker](https://www.docker.com/) | Necessário para executar os containers e gerenciar o ambiente local. |
| [Java 21+](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) | Necessário para executar a aplicação localmente, caso ela não seja executada em um container. |
| [Postman](https://www.postman.com/downloads/) | Utilizado para testar os endpoints e executar as collections de API. |
| [DBeaver](https://dbeaver.io/download/) | Opcional, para visualizar e consultar os bancos de dados por meio de uma interface gráfica. |
| Git | Necessário para clonar o repositório do projeto. |

> **Observação:** o Docker Compose deve estar disponível no ambiente. O Docker Desktop já inclui esse recurso nas instalações compatíveis. Para executar a aplicação pela IDE ou pelo terminal, utilize um JDK 21 ou superior.

---

## 💻 Como Executar

Os scripts `setup.sh` e `setup.bat` automatizam a preparação do ambiente local.

### 🐧 Linux ou macOS

1. Abra o terminal no diretório que deseja utilizar para o projeto.
2. Conceda permissão de execução ao script:

   ```bash
   chmod +x setup.sh
   ```

3. Execute o script:

   ```bash
   ./setup.sh
   ```

### 🪟 Windows

1. Abra o terminal no diretório que contém o arquivo `setup.bat`.
2. Execute o script:

   ```cmd
   setup.bat
   ```

   Alternativamente, execute o arquivo `setup.bat` diretamente pelo Explorador de Arquivos.

---

## 🛠️ O que os Scripts de Inicialização Fazem?

Os scripts automatizam a preparação do ambiente de desenvolvimento, contemplando as seguintes etapas:

- Clonam o repositório do serviço `ms-mecanica`:

  [https://github.com/TC-FIAP-SOAT-MECANICA/ms-mecanica](https://github.com/TC-FIAP-SOAT-MECANICA/ms-mecanica)

- Criam ou disponibilizam um arquivo `docker-compose.yml` para configuração dos bancos de dados MySQL e PostgreSQL.
- Configuram volumes dedicados para persistência dos dados dos containers.
- Iniciam os containers em segundo plano utilizando:

  ```bash
  docker compose up -d
  ```

> **Importante:** a configuração descrita acima depende da implementação dos scripts. Caso o projeto utilize somente MySQL, ajuste a descrição para refletir os serviços efetivamente configurados no `docker-compose.yml`.

---

## 🔍 Observações

- Os containers dos bancos de dados são iniciados automaticamente pelos scripts, desde que o Docker esteja instalado e em execução.
- O microsserviço `ms-mecanica` deve ser iniciado separadamente pela IDE ou pelo terminal, caso não esteja configurado para execução em container.
- O Postman pode ser utilizado para testar os endpoints REST por meio das collections disponibilizadas no projeto.
- Os dados persistidos nos volumes Docker são mantidos após a interrupção dos containers, desde que os volumes não sejam removidos.
- As configurações de conexão, credenciais e portas dos bancos de dados devem corresponder às definições utilizadas pela aplicação e pelo Docker Compose.

---

## 📁 Estrutura Esperada Após a Execução

Após a execução dos scripts, a estrutura de diretórios deverá ser semelhante à seguinte:

```text
/seu-diretorio/
├── data/
├── images/
│   └── diagrama-arquitetura.svg
├── ms-mecanica/
├── docker-compose.yml
├── setup.sh
├── setup.bat
└── README.md
```