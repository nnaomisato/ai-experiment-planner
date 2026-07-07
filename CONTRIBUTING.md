# Como contribuir

Obrigada pelo interesse em melhorar a AI Experiment Planner. Toda contribuição ajuda.

## Dar feedback

A forma mais rápida é abrir uma issue:

1. Vá em **Issues > New issue**.
2. Escolha o template: **Feedback** ou **Problema (bug)**.
3. Descreva o que aconteceu e o que você esperava.

Feedback vale muito, mesmo sem código. Conte o que funcionou, o que confundiu e o que faltou.

## Propor uma melhoria (Pull Request)

Você não tem acesso de escrita neste repositório. Contribuições entram por fork e Pull Request:

1. **Fork** deste repositório (botão no topo da página).
2. Crie uma branch no seu fork: `git checkout -b minha-melhoria`.
3. Edite o arquivo da skill: `plugins/ai-experiment-planner/skills/ai-experiment-planner/SKILL.md`.
4. Faça commit e push na sua branch.
5. Abra um **Pull Request** para a branch `main` deste repositório.

Toda alteração passa por revisão antes do merge. Ninguém altera a skill sem aprovação.

## O que é bem-vindo

- Correções de clareza e linguagem.
- Novos exemplos ou perguntas que melhorem cada fase.
- Ajustes nos frameworks (HEART, esferas éticas) com justificativa.
- Traduções.

## Padrões de escrita

- Português do Brasil claro e direto.
- Frases curtas. Uma ideia por frase.
- Linguagem neutra de gênero para papéis genéricos ("pessoa responsável", não "gestor").
- Sem o caractere travessão (em-dash). Use ponto, dois-pontos, parênteses ou vírgula.

## Validar a skill localmente

Antes de abrir o PR, teste no Claude Code:

```
claude --plugin-dir ./plugins/ai-experiment-planner
```

Dispare a skill e rode as 6 fases para confirmar que tudo funciona.
