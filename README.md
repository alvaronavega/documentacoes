# Domine o Git com Elegância: Estratégias para Branches, Commits Semânticos e Dicas Essenciais

## Sumário
- [Domine o Git com Elegância: Estratégias para Branches, Commits Semânticos e Dicas Essenciais](#domine-o-git-com-elegância-estratégias-para-branches-commits-semânticos-e-dicas-essenciais)
  - [Sumário](#sumário)
  - [Introdução](#introdução)
  - [Branches](#branches)
    - [Tipos Principais de Branches](#tipos-principais-de-branches)
    - [Boas Práticas para Branches](#boas-práticas-para-branches)
    - [Workflow de Branches](#workflow-de-branches)
    - [Resolução de Conflitos](#resolução-de-conflitos)
    - [Proteções Recomendadas](#proteções-recomendadas)
  - [Commits](#commits)
    - [Commits Semânticos](#commits-semânticos)
    - [Estrutura do Commit](#estrutura-do-commit)
    - [Tipos de Commits](#tipos-de-commits)
    - [Padrões de Emojis para Commits](#padrões-de-emojis-para-commits)
    - [Exemplos de Uso](#exemplos-de-uso)
  - [Comandos Essenciais do Git 📜](#comandos-essenciais-do-git-)
    - [Configuração Inicial do Repositório](#configuração-inicial-do-repositório)
  - [Glossário 📖](#glossário-)

## Introdução

O Git é uma ferramenta essencial para controle de versão que permite aos desenvolvedores gerenciar seu código de forma eficaz. Este guia explora as melhores práticas para branches e commits no Git, combinando insights de desenvolvedores líderes na área.

## Branches

### Tipos Principais de Branches

| Tipo | Descrição | Origem | Exemplo |
|------|-----------|--------|---------|
| **main** (ou master) | Branch principal do projeto. Contém código em estado de produção. | -- | `main` |
| **develop** | Branch de desenvolvimento. Contém código em estado de pré-produção. | main | `develop` |
| **feature/** | Para desenvolvimento de novas funcionalidades. | develop | `feature/login-system` |
| **hotfix/** | Para correções urgentes em produção. | main | `hotfix/fix-login-bug` |
| **release/** | Preparação para nova versão de produção. | develop | `release/v1.0.0` |
| **bugfix/** | Para correção de bugs em desenvolvimento. | develop | `bugfix/header-alignment` |

### Boas Práticas para Branches

| Prática | Descrição | Exemplo | Comando Git |
|---------|-----------|---------|-------------|
| **Nomes Descritivos** | Use nomes claros e concisos | ✅ `feature/user-auth`<br>❌ `feature/f1` | `git checkout -b feature/user-auth` |
| **Kebab Case** | Use hífen para separar palavras | ✅ `feature/email-login`<br>❌ `feature/email_login` | `git checkout -b feature/email-login` |
| **Referência à Issue** | Inclua o número da issue quando relevante | `feature/123-user-profile` | `git checkout -b feature/123-user-profile` |
| **Prefixos Padrão** | Use prefixos consistentes | `feature/`, `hotfix/`, `bugfix/` | `git checkout -b [prefixo]/[nome]` |
| **Atualizações Frequentes** | Mantenha a branch sincronizada com develop | -- | `git merge develop` |
| **Limpeza Pós-Merge** | Remova branches após merge concluído | -- | `git branch -d feature/concluida` |

### Workflow de Branches

| Etapa | Ação | Comando |
|-------|------|---------|
| 1. Criar feature | Crie uma nova branch a partir da develop | `git checkout develop`<br>`git checkout -b feature/nova-func` |
| 2. Desenvolver | Faça commits na sua feature branch | `git add .`<br>`git commit -m "✨ feat: Nova função"` |
| 3. Atualizar | Mantenha sua branch atualizada com develop | `git merge develop` |
| 4. Finalizar | Merge da feature em develop | `git checkout develop`<br>`git merge feature/nova-func` |

### Resolução de Conflitos

| Situação | Ação Recomendada | Comando |
|----------|------------------|---------|
| Conflito no merge | Resolver localmente antes do push | `git merge develop`<br>Resolver conflitos<br>`git add .`<br>`git commit -m "🔀 merge: Resolve conflitos"` |
| Conflito no rebase | Resolver um commit por vez | `git rebase develop`<br>Resolver conflitos<br>`git add .`<br>`git rebase --continue` |

### Proteções Recomendadas

| Branch | Proteção | Motivo |
|--------|----------|--------|
| main | Require pull request | Evita mudanças diretas em produção |
| develop | Require code review | Mantém qualidade do código |
| all | Require status checks | Garante que testes passem |

## Commits

### Commits Semânticos
De acordo com a documentação do **[Conventional Commits](https://www.conventionalcommits.org/pt-br)**, commits semânticos são uma convenção que define regras para criar um histórico de commit explícito, facilitando a criação de ferramentas automatizadas e a compreensão das alterações por toda a equipe.

### Estrutura do Commit

1. **Tipo:** Identifica a natureza da mudança (feat, fix, docs, etc.)
2. **Escopo:** (opcional) Indica a seção do código afetada
3. **Descrição:** Resumo conciso da mudança
4. **Corpo:** (opcional) Descrição detalhada
5. **Rodapé:** (opcional) Metadados como revisor e referências

Exemplo:
```
feat(login): adiciona autenticação com Google

Implementa OAuth2 para login com Google
- Adiciona dependências necessárias
- Configura rotas de autenticação
- Atualiza UI com novo botão

Reviewed-by: João Silva
Refs #123
```

### Tipos de Commits
1. `feat` - Novo recurso
2. `fix` - Correção de bug
3. `docs` - Documentação
4. `style` - Formatação de código
5. `refactor` - Refatoração de código
6. `test` - Testes
7. `chore` - Tarefas de build, admin, etc.
8. `perf` - Melhorias de performance
9. `ci` - Mudanças na integração contínua
10. `build` - Modificações em arquivos de build
11. `raw` - Mudanças em dados/configs
12. `cleanup` - Limpeza de código
13. `remove` - Remoção de arquivos/recursos

### Padrões de Emojis para Commits

| Tipo de Commit | Emoji | Palavra-chave |
|----------------|-------|---------------|
| Acessibilidade | ♿ `:wheelchair:` | |
| Adicionando um teste | ✅ `:white_check_mark:` | `test` |
| Adicionando uma dependência | ➕ `:heavy_plus_sign:` | `build` |
| Alterações de revisão de código | 👌 `:ok_hand:` | `style` |
| Animações e transições | 💫 `:dizzy:` | |
| Bugfix | 🐛 `:bug:` | `fix` |
| Comentários | 💡 `:bulb:` | `docs` |
| Commit inicial | 🎉 `:tada:` | `init` |
| Configuração | 🔧 `:wrench:` | `chore` |
| Deploy | 🚀 `:rocket:` | |
| Documentação | 📚 `:books:` | `docs` |
| Em progresso | 🚧 `:construction:` | |
| Estilização de interface | 💄 `:lipstick:` | `feat` |
| Infraestrutura | 🧱 `:bricks:` | `ci` |
| Lista de ideias (tasks) | 🔜 `:soon:` | |
| Mover/Renomear | 🚚 `:truck:` | `chore` |
| Novo recurso | ✨ `:sparkles:` | `feat` |
| Package.json em JS | 📦 `:package:` | `build` |
| Performance | ⚡ `:zap:` | `perf` |
| Refatoração | ♻️ `:recycle:` | `refactor` |
| Removendo um arquivo | 🗑️ `:wastebasket:` | `remove` |
| Removendo uma dependência | ➖ `:heavy_minus_sign:` | `build` |
| Responsividade | 📱 `:iphone:` | |
| Revertendo mudanças | 💥 `:boom:` | `fix` |
| Segurança | 🔒️ `:lock:` | |
| SEO | 🔍️ `:mag:` | |
| Tag de versão | 🔖 `:bookmark:` | |
| Teste de aprovação | ✔️ `:heavy_check_mark:` | `test` |
| Testes | 🧪 `:test_tube:` | `test` |
| Texto | 📝 `:pencil:` | |
| Tipagem | 🏷️ `:label:` | |
| Tratamento de erros | 🥅 `:goal_net:` | |
| Limpeza de código | 🧹 `:broom:` | `cleanup` |
| Dados | 🗃️ `:card_file_box:` | `raw` |

### Exemplos de Uso

```
git commit -m "🎉 init: Commit inicial"
git commit -m "✨ feat: Sistema de login"
git commit -m "🐛 fix: Corrige loop infinito"
git commit -m "📚 docs: Atualiza README"
git commit -m "♻️ refactor: Simplifica função"
```

## Comandos Essenciais do Git 📜

| Comando | Descrição |
|---------|-----------|
| `git clone url-do-repositorio` | Clona um repositório remoto |
| `git init` | Inicializa um novo repositório Git |
| `git add .` | Adiciona todos os arquivos para stage |
| `git commit -m "mensagem"` | Registra alterações com mensagem |
| `git branch -M main` | Renomeia a branch atual para main |
| `git remote add origin url` | Adiciona um repositório remoto |
| `git push -u origin main` | Envia commits e configura upstream |
| `git fetch` | Busca atualizações sem integrar |
| `git pull origin main` | Atualiza branch local com remota |
| `git push --force-with-lease` | Force push seguro |
| `git revert commit-id` | Reverte um commit específico |
| `git reset --hard commit-id` | Redefine para commit específico |
| `git commit --amend` | Altera último commit |
| `git cherry-pick commit-hash` | Aplica commit específico |

### Configuração Inicial do Repositório
```bash
git init
git remote add origin git@github.com:usuario/projeto.git
git branch -M main
git push -u origin main
```

## Glossário 📖

- `fork` - Cópia de um repositório para sua conta
- `issues` - Ferramenta para gerenciar tarefas/bugs
- `pull request` - Solicitação para integrar alterações
- `gist` - Compartilhamento de trechos de código

---

*Créditos:*  
🕹 Feito &nbsp;por Alvaro Navega &nbsp;

[![Github](https://img.shields.io/badge/-Github-595D60?style=flat-square&logo=Github&logoColor=white&link=https://github.com/nayaraquino/)](https://github.com/alvaronavega)
[![Linkedin](https://img.shields.io/badge/-LinkedIn-595D60?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/nayaraquino//)](https://www.linkedin.com/in/alvaronavega/)

*Insights dos artigos:*

*Padrões de commits do [artigo de Iuri Silva](https://github.com/iuricode/padroes-de-commits/blob/main/README.md)*  
*Entendendo as Nomenclaturas de Commits no Git do [artigo de Augusto Simionato](https://medium.com/@augustosimionato/entendendo-as-nomenclaturas-de-commits-no-git-301a95a72806)*
