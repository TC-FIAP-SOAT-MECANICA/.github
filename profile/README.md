# 🏗️ Tech Challenge FIAP — Software Architecture

### 📄 [Documentação Oficial do Tech Challenge](https://docs.google.com/document/d/1RPeK3JgDrr0Tr1RDDOBvYhXcyjjhGP35yhkQcw4bi7o)
### 🎥 [Vídeo de Apresentação](https://youtu.be/xeHCxDUHEUg)
### 🏛️ [Acessar documentação no Miro](https://miro.com/app/board/uXjVEVg990w=/?share_link_id=821131686431).

# Sistema de Gestão para Oficina Mecânica

Aplicação desenvolvida como parte do Tech Challenge da Pós-Graduação em Software Architecture da FIAP, com o objetivo de centralizar e otimizar o gerenciamento de oficinas mecânicas.

## 📌 Problema e Objetivo

Oficinas mecânicas podem enfrentar dificuldades na gestão de atendimentos e execução de serviços, especialmente quando utilizam processos manuais e planilhas. Isso pode ocasionar perda do histórico de clientes e veículos, falhas no controle de peças e insumos, dificuldade no acompanhamento das ordens de serviço e falta de visibilidade sobre os prazos e tempos de execução.

O projeto propõe um sistema integrado para centralizar o gerenciamento de clientes, veículos, serviços, estoque e ordens de serviço, desde a entrada do veículo até sua entrega.

A solução permite acompanhar o andamento dos serviços, consultar o histórico dos atendimentos, elaborar e aprovar orçamentos e controlar as movimentações de estoque.

## ⚙️ Funcionalidades

- **Autenticação e usuários:** login, geração de tokens JWT e controle de acesso por perfil.
- **Clientes:** cadastro, consulta, atualização e gerenciamento.
- **Mecânicos:** cadastro, consulta, atualização e gerenciamento.
- **Veículos:** cadastro e gerenciamento de veículos vinculados aos clientes.
- **Serviços:** gerenciamento do catálogo de serviços da oficina.
- **Peças e estoque:** cadastro de peças, controle de quantidades e movimentações.
- **Ordens de Serviço:** abertura, diagnóstico, orçamento, aprovação, execução, finalização e entrega.
- **Acompanhamento:** consulta das ordens de serviço, histórico e aprovação de orçamentos pelos clientes.

### Perfis de acesso

| Perfil | Responsabilidade |
|---|---|
| `ADMIN` | Gerenciamento administrativo da oficina. |
| `MECANICO` | Diagnóstico, execução dos serviços e gerenciamento operacional. |
| `CLIENTE` | Consulta de veículos e ordens de serviço, além da aprovação de orçamentos. |

### Fluxo da Ordem de Serviço

`RECEBIDA → EM_DIAGNOSTICO → AGUARDANDO_APROVACAO → EM_EXECUCAO → FINALIZADA → ENTREGUE`

## 🏛️ Arquitetura

A aplicação utiliza **arquitetura monolítica**, desenvolvida em Java 21 com Spring Boot.

Principais abordagens adotadas:

- **DDD (Domain-Driven Design):** modelagem orientada ao domínio e às regras de negócio.
- **Event Storming:** identificação dos eventos, comandos e fluxos de negócio.
- **Clean Architecture:** separação de responsabilidades e baixo acoplamento.
- **API First:** definição dos contratos da API utilizando OpenAPI.
- **C4 Model:** documentação arquitetural nos quatro níveis.

A aplicação é organizada em camadas, utilizando Controllers, Use Cases, Gateways e componentes de infraestrutura.

**Diagramas e modelagem:** [Acessar documentação no Miro](https://miro.com/app/board/uXjVEVg990w=/?share_link_id=821131686431).

## 💻 Tecnologias Utilizadas

| Categoria | Tecnologia |
|---|---|
| Linguagem | Java 21 |
| Framework | Spring Boot |
| Segurança | Spring Security e JWT |
| Persistência | Spring Data JPA |
| Banco de dados | PostgreSQL 16 |
| Testes locais | H2 |
| Contratos e documentação | OpenAPI / Swagger |
| Build | Maven |
| Testes automatizados | JUnit 5, Mockito e MockMvc |
| Testes de API | Postman |
| Conteinerização | Docker e Docker Compose |
| Versionamento | Git e GitHub |

### Banco de Dados

O PostgreSQL foi escolhido por oferecer confiabilidade, integridade referencial, suporte a transações e flexibilidade para consultas SQL, atendendo às necessidades de persistência e relacionamento entre clientes, veículos, peças e ordens de serviço.

## 🧪 Testes

A aplicação contempla testes unitários, de integração e testes funcionais de API.

São disponibilizadas duas collections Postman:

**1. Testes funcionais**

[oficina-mecanica.postman_collection.json](https://github.com/TC-FIAP-SOAT-MECANICA/collections/blob/main/oficina-mecanica.postman_collection.json)

Contempla os principais recursos da API, incluindo cenários de sucesso, erro, autenticação e permissões.

**2. Fluxo completo da Ordem de Serviço**

[oficina-mecanica-fluxo-os.postman_collection.json](https://github.com/TC-FIAP-SOAT-MECANICA/collections/blob/main/oficina-mecanica-fluxo-os.postman_collection.json)

Simula o ciclo completo de uma OS, desde os cadastros iniciais até a entrega do veículo, incluindo diagnóstico, orçamento, aprovação do cliente e movimentação do estoque.

[**Acessar repositório das Collections**](https://github.com/TC-FIAP-SOAT-MECANICA/collections)

## 🐳 Execução com Docker

A configuração do ambiente está centralizada em um repositório independente, responsável pela orquestração da API e do PostgreSQL.

**Repositório:** [TC-FIAP-SOAT-MECANICA/docker](https://github.com/TC-FIAP-SOAT-MECANICA/docker)

### Pré-requisitos

- Git.
- Docker Desktop.
- Docker Compose.

### Linux, macOS, Git Bash ou WSL

Baixe o script:

```bash
curl -fsSL https://raw.githubusercontent.com/TC-FIAP-SOAT-MECANICA/docker/main/setup.sh -o setup.sh
```

Conceda permissão de execução:

```bash
chmod +x setup.sh
```

Execute:

```bash
./setup.sh
```

### Windows (Prompt de Comando ou PowerShell)

Baixe o script:

```powershell
curl.exe -fsSL https://raw.githubusercontent.com/TC-FIAP-SOAT-MECANICA/docker/main/setup.bat -o setup.bat
```

Execute:

```bat
setup.bat
```

Os scripts automatizam a clonagem dos repositórios, configuração do ambiente, construção da imagem da API e inicialização dos containers.

Para informações sobre portas, credenciais, variáveis de ambiente e comandos Docker, consulte o [README do repositório Docker](https://github.com/TC-FIAP-SOAT-MECANICA/docker).

## 📚 Documentação da API

O contrato OpenAPI está disponível no repositório:

[**oficina-mecanica-contract.yaml**](https://github.com/TC-FIAP-SOAT-MECANICA/ms-mecanica/blob/main/oficina-mecanica-contract.yaml)

Após iniciar a aplicação, a documentação e o estado da API podem ser consultados nos seguintes endpoints:

| Recurso | Endpoint padrão |
|---|---|
| API | `http://localhost:8080/api/v1` |
| Contrato OpenAPI | `/api/v1/oficina-mecanica-contract.yaml` |
| Health Check | `/api/v1/actuator/health` |

A porta externa pode ser personalizada por meio da variável `API_PORT` no ambiente Docker.

## 🔗 Repositórios

| Repositório | Descrição |
|---|---|
| [Organização FIAP](https://github.com/TC-FIAP-SOAT-MECANICA) | Organização do projeto. |
| [ms-mecanica](https://github.com/TC-FIAP-SOAT-MECANICA/ms-mecanica) | Código-fonte da aplicação. |
| [docker](https://github.com/TC-FIAP-SOAT-MECANICA/docker) | Configuração e orquestração do ambiente. |
| [collections](https://github.com/TC-FIAP-SOAT-MECANICA/collections) | Collections de testes Postman. |

---

**FIAP — Pós-Graduação em Software Architecture**
