Guia de Padronização de Repositórios
Este documento estabelece as diretrizes para a nomenclatura e organização dos repositórios de software, visando a consistência entre o Backend e o Frontend, além de facilitar a identificação de serviços, APIs e  automações.

1 - Padrão de Nomenclatura

Todos os repositórios devem seguir o padrão CamelCase (palavras compostas unidas sem espaços, com a primeira letra de cada palavra em maiúsculo). A estrutura do nome deve seguir o formato:

[Projeto][Tipo]

Tipos de Repositórios
Utilize os prefixos/sufixos abaixo para identificar a natureza do código:

	Prefixo/Sufixo
	Web, Aplicações de interface (SPA, WebApp, etc.)
	Api, Interfaces de programação (REST, GraphQL)
	Worker, Processamento em segundo plano ou filas
	Service, Serviços de lógica de negócio (Microserviços)
	RPA, Robôs de automação (RPA ou Scripts)
	Lib, Bibliotecas internas e pacotes compartilhados
	Infra, Arquivos de IaC (Terraform, Docker, K8s)


2 - Organização Interna Sugerida

Backend (Ex: .NET / C#)
Seguimos o padrão de Clean Architecture ou N-Tier:

	src/Project.API: Ponto de entrada da aplicação.
	src/Project.Domain: Entidades, interfaces e regras de negócio.
	src/Project.Application: Casos de uso e DTOs.
	src/Project.Infrastructure: Acesso a dados (SQL Server), integrações externas.
	tests/: Testes unitários e de integração.

	Frontend (Ex: Blazor)
	src/components: Componentes reutilizáveis.
	src/pages: Páginas da aplicação.
	src/services: Chamadas para as APIs.
	src/assets: Imagens, estilos globais e fontes.


3 - Melhores Práticas

Git & Fluxo de Trabalho
Branches: Utilizar o padrão GitFlow simplificado:

	main: Código em produção.
	dev: Código em ambiente de desenvolvimento/homologação.
	feature/nome-da-task: Desenvolvimento de novas funcionalidades.
	hotfix/ajuste-urgente: Correções rápidas em produção.

Commits: Mensagens claras e em português. Ex: feat: adiciona endpoint de consulta de técnicos.

Todo repositório deve conter um README.md com:

	Descrição breve: O que o projeto faz.
	Pré-requisitos: Versões do SDK (.NET), Docker, etc.
	Configuração Local: Passos para rodar o projeto (dotnet run, npm install).
	Variáveis de Ambiente: Lista de chaves necessárias (ex: Connection Strings).

Containers:

	Todo projeto deve possuir um Dockerfile na raiz.
	Para projetos que dependem de múltiplos serviços, incluir um docker-compose.yml para facilitar o setup do ambiente de desenvolvimento.
