<!-- Copyright (c) 2026 Pedro Vinicius. Todos os direitos reservados. Next Teams. -->

# » NEXT TEAMS

**Projetos de equipe organizados em cima do GitHub.** Cada pessoa altera só as
pastas liberadas para ela, e o Claude explica em português o que cada pull
request faz.

> 🚧 **Em desenvolvimento.** Fase atual: protótipo das telas (Etapa P), antes do Marco 1.

---

## O problema

Em projetos de grupo, cada integrante cria pastas e código do seu jeito, um não
entende a lógica do outro e alguém acaba bagunçando a parte dos colegas.
Configurar CODEOWNERS, proteção de branch e rulesets no GitHub é difícil para
quem está começando.

## A solução

O Next Teams é uma camada por cima do GitHub (ele **não substitui** o GitHub):

1. O **Admin** cria um projeto novo pelo painel ou conecta um que já existe.
2. O Next Teams monta a estrutura no GitHub e define quem pode alterar cada pasta.
3. Cada **Desenvolvedor** abre o projeto no VS Code com um clique, numa branch da tarefa.
4. Todo trabalho chega à `main` por pull request, que o Next Teams checa (✅ / ❌)
   e o Claude resume em 4 blocos.

**Para quem:** equipes de estudantes e pequenas equipes de desenvolvimento,
como projetos de disciplina, TCC e hackathon.

## Papéis

| Papel | O que faz |
|---|---|
| **Admin** | Cria ou conecta o projeto, convida pessoas, define pastas, aprova PRs e pedidos |
| **Desenvolvedor** | Programa nas pastas liberadas, envia PRs, pede acesso a outras pastas |
| **Analista** | Acompanha o painel de análise da equipe (sem ranking) |

Todos leem todo o código. O controle é só sobre quem pode **alterar**.

## Stack

| Camada | Tecnologia |
|---|---|
| Backend e GitHub App | ASP.NET Core (.NET 8+) |
| Painel web | Blazor |
| Integração GitHub | Octokit.NET |
| Banco de dados | MySQL + EF Core (Pomelo) |
| IA | SDK oficial da Anthropic para C# |
| Login | OAuth do GitHub |
| Hospedagem | Azure App Service + Azure Database for MySQL |

## Estrutura da solução (planejada)

```
src/
├── Next.Web      # Painel Blazor + endpoint de webhook
├── Next.Core     # Regra de permissão (sem depender do GitHub nem do banco)
├── Next.GitHub   # Repositórios, branches, checks, convites
├── Next.IA       # Fila de resumos de PR com o Claude
└── Next.Data     # EF Core + MySQL
tests/
└── Next.Core.Tests
```

## Roteiro

- [ ] **Etapa P:** protótipo das telas
- [ ] **Marco 1 (Demo):** login e instalação, novo projeto, conectar projeto existente,
      permissões e convites, checagem do PR, resumo do Claude
- [ ] **Marco 2 (Versão 1):** abrir no VS Code + branch, pedido de acesso, saída e troca
      de membro, envio direto na `main`, painel do Analista, privacidade, teste com o PCEDUC
- [ ] **Versão 2:** extensão do VS Code, e-mail de convite automático, explicação de pasta,
      mais modelos de projeto

## Autor

Pedro Vinicius: [@PedroVini09](https://github.com/PedroVini09)

## Licença

Projeto proprietário. Veja o arquivo [LICENSE](LICENSE).
