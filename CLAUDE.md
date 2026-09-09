# documentos - guia do agente

## Papel no produto

Este repositorio e a fonte versionada de documentacao institucional e tecnica do Projuris Acordos. Ele descreve arquitetura, seguranca, privacidade, integracoes de terceiros, operacao e requisitos de conectividade; nao contem runtime nem publica aplicacao.

## Comece por

- `detalhamento-projuris-acordos.md`: visao da plataforma, isolamento multi-tenant, arquitetura AWS/EKS, observabilidade, backup e microfrontends.
- `servicos-terceiros.md`: catalogo de integracoes externas e implicacoes de protecao de dados.

Valide afirmacoes mutaveis contra os repositorios proprietarios e a evidencia operacional atual antes de reutiliza-las. Mantenha autoria, data e base de evidencia explicitas; relato historico nao e prova do estado presente.

## Verificacao

```bash
git diff --check
```

Nao invente um build para este repositorio. Revise links, nomes de servicos, dominios, periodos de retencao e afirmacoes de seguranca no diff; mudancas que alterem compromisso externo exigem evidencia do proprietario correspondente.

## Limites

- Nao registre credenciais, tokens, dados pessoais ou configuracao secreta.
- Nao transforme documentacao de arquitetura em autorizacao para operar producao.
- Conhecimento comum do harness fica no `sdd-toolkit`; aqui permanecem fatos especificos do Acordos.
