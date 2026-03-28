# Mural de Recados Frontend

![Preview do projeto](img/print.png)

## 1. Objetivo do Projeto
Este projeto implementa a interface web de um mural de recados.

O objetivo do sistema e permitir que usuarios:
- visualizem recados cadastrados;
- adicionem novos recados com autor e mensagem;
- excluam recados existentes.

Na pratica, a aplicacao resolve a necessidade de um CRUD simples de mensagens em uma interface unica e direta.

## 2. Arquitetura e Stack
Arquitetura adotada:
- SPA (Single Page Application) com Vue 3 e Vite.

Organizacao principal:
- `src/main.js`: bootstrap da aplicacao (Vue + Pinia + Router).
- `src/App.vue`: tela principal e fluxo de CRUD via `fetch`.
- `src/router/index.js`: roteador configurado, atualmente sem rotas declaradas.
- `src/stores/counter.js`: store inicial do Pinia (ainda nao utilizada no fluxo principal).

Tecnologias identificadas neste repositorio:
- Frontend: Vue 3, Vue Router, Pinia, Vite.
- Backend: nao existe backend neste repositorio; o frontend consome API HTTP externa.
- Banco de dados: nao existe camada de banco neste repositorio.

Integracao de API atual:
- Endpoints chamados pelo frontend: `http://localhost:4000/recados`.
- Operacoes implementadas: listagem, criacao e exclusao de recados.

## 3. Acesso e Execucao do Projeto
Pre-requisitos:
- Node.js na versao `^20.19.0 || >=22.12.0`.
- npm.
- Backend em execucao em `http://localhost:4000` com rota `/recados`.

Passo a passo para rodar localmente:

```sh
npm install
```

```sh
npm run dev
```

Aplicacao em desenvolvimento:
- Abra a URL exibida pelo Vite no terminal (normalmente `http://localhost:5173`).

Build de producao:

```sh
npm run build
```

Preview local da build:

```sh
npm run preview
```

## 4. Alteracoes, Testes e Validacoes
Como contribuir com o projeto:
1. Crie uma branch para sua alteracao.
2. Implemente a mudanca mantendo o padrao do projeto (Vue 3 com Composition API e `script setup`).
3. Rode a aplicacao localmente para validar o fluxo.
4. Abra PR descrevendo o que foi alterado e como validar.

Como rodar testes:
- Atualmente nao existe script de testes automatizados no `package.json`.

Como validar se esta funcionando:
1. Suba o backend local na porta `4000`.
2. Rode o frontend com `npm run dev`.
3. Valide os cenarios principais na interface:
   - listagem de recados ao carregar a pagina;
   - criacao de novo recado;
   - exclusao de recado;
   - atualizacao da lista apos criar/excluir.
