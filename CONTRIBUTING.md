# Como contribuir

**Todo feedback ajuda, mesmo sem código.** Conte o que funcionou, o que confundiu e o que faltou.

## Dar feedback (o jeito mais rápido)

Abra uma issue (um registro público de feedback ou erro):

1. Vá em **Issues > New issue**.
2. Escolha o template: **Feedback** ou **Problema (bug)**.
3. Descreva o que aconteceu e o que você esperava.

## Propor uma melhoria

Você não tem acesso de escrita neste repositório. As mudanças entram por dois passos:

- **Fork:** uma cópia sua do projeto (botão no topo da página).
- **Pull Request (PR):** o pedido para incluir sua mudança, que eu reviso antes de aceitar.

Passo a passo:

1. Faça o fork.
2. Crie uma branch (uma linha de trabalho separada): `git checkout -b minha-melhoria`.
3. Edite o arquivo da skill: `plugins/ai-experiment-planner/skills/ai-experiment-planner/SKILL.md`.
4. Faça commit e envie (push) para a sua branch.
5. Abra o Pull Request para a branch `main`.

Nada muda na skill sem revisão. Ninguém publica direto.

## O que é bem-vindo

- Correções de clareza e de linguagem.
- Novos exemplos ou perguntas que melhorem cada etapa.
- Ajustes nos métodos (HEART, pontos de ética) com uma justificativa.
- Traduções.

## Como escrever

- Português do Brasil, claro e direto.
- Frases curtas. Uma ideia por frase.
- Linguagem inclusiva e neutra de gênero ("pessoa responsável", não "gestor").
- Explique o termo técnico na primeira vez que aparecer.
- Sem o caractere travessão (em-dash). Use ponto, dois-pontos, parênteses ou vírgula.

## Testar antes de enviar

No Claude Code, rode:

```
claude --plugin-dir ./plugins/ai-experiment-planner
```

Dispare a skill e percorra as etapas para confirmar que tudo funciona.
