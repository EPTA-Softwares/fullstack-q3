# 🚗 Prova Técnica — Sistema de Vistorias (Next.js + Nest.js)

Link do Prótotipo -> https://www.figma.com/design/z296qlHk8uC1O7druJ3Miu/Sem-t%C3%ADtulo?node-id=0-1&t=HIAMYKBXsXLinruY-1

Desafio técnico para vaga de Desenvolvedor(a) Fullstack Júnior / Pleno (ajuste o nível na hora de aplicar).
O objetivo é avaliar domínio em Next.js (front), Nest.js (back), modelagem de dados, autenticação JWT, UX para formulários/relatórios e boas práticas (TypeScript, testes, organização).

**Obs.:** o repositório deve conter um README com instruções de execução, um .env.example, scripts de migração/seed e os entregáveis descritos abaixo.

## 🔎 Escopo (obrigatório)

Implementar uma aplicação com as seguintes telas/fluxos (baseadas nas telas que você já implementou):

### Login

Autenticação com JWT.

### Vistorias

- Listagem com busca, filtros e cards de resumo (Total, Pendentes, Aprovadas, Reprovadas).
- Ações (visualizar, editar, reemitir, exportar).
- Página de criação/edição de vistoria com checklist e observações.

### Veículos

Listagem e CRUD básico de veículos (nome, placa, marca, modelo, ano, proprietário).

### Relatórios

- Filtros por período / vistoriador.
- Cards com métricas (total vistorias, taxa de aprovação, tempo médio).
- Tabela de performance por vistoriador.
- Exportar (CSV/PDF) — diferencial se implementado.

### Vistorias

- `GET /inspections` — lista (filtros: status, vistoriador, date range, search por placa/modelo)
- `GET /inspections/:id` — detalhes
- `POST /inspections` — criar (payload inclui vehicleId, date, vistoriadorId, items: [{ key, status, comment }], observations)
- `PUT /inspections/:id` — atualizar (itens do checklist, observações)
- `PATCH /inspections/:id/status` — alterar status (Pendente → Em andamento → Concluída)
- `DELETE /inspections/:id` — remover (opcional)

### Relatórios (endpoints de suporte)

**GET /reports/overview?from=YYYY-MM-DD&to=YYYY-MM-DD**

Retorna agregados: total, aprovadas, reprovadas, tempo médio.

**GET /reports/by-inspector** — lista com métricas por vistoriador.


## 🧩 Front-end (Next.js) — Páginas / Componentes

### Páginas principais

- `/login` — formulário de login (email, password)
- `/vistorias` — listagem com:
  - Search (placa/modelo)
  - Filtros (status, período)
  - Cards resumo
  - Tabela com paginação e ações (visualizar, editar, exportar)
- `/vistorias/new` e `/vistorias/[id]` — formulário de vistoria (dados veículo no topo, checklist por itens, observações)
- `/veiculos` — listagem; modal/rota para novo/editar veículo
- `/relatorios` — filtros e visualização de cards, gráficos (pode usar chart placeholder)

### UX / UI guidelines

- Formulário de vistoria rápido: itens em formato de lista com botões Aprovado / Reprovado / N/A.
- Indicação de status com badges coloridos (Pendente — amarelo, Concluída — verde, Reprovada — vermelho).
- Responsividade: desktop + tablet (mobile opcional).
- Acessibilidade básica: labels, foco visível, inputs acessíveis.

## 📚 Dados de Seed (exemplo minimal)

- 3 usuários (admin, vistoriador1, vistoriador2)
- 10 veículos com placas, marcas
- 20 vistorias distribuídas (pendente, concluída, reprovada)

## 📦 Entregáveis esperados

Repositório Git (ou monorepo) com:

- backend/ (Nest.js)
- frontend/ (Next.js)
- README.md com instruções de execução
- .env.example
- Scripts de migração/seed
- docker

## 💡 Sugestões de diferenciais que valorizam o candidato

- Implementar refresh tokens e logout seguro.
- Exportar laudo em PDF (gerar arquivo com o resultado da vistoria).
- Implementar filtros avançados e ordenação no backend (SQL/ORM otimizado).
- Implementar microinterações no front (confirmação, toast).
- Implementar E2E com Playwright ou Cypress.
- Containerizar a solução (Docker + docker-compose).
