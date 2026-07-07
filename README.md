# AI Experiment Planner

**Planeje experimentos de IA do problema à documentação, sem virar burocracia.**

Isto é uma skill: uma extensão que ensina o Claude a conduzir uma tarefa específica. Esta skill guia você por 6 etapas, em português, e entrega no fim um documento pronto para compartilhar.

**Por que importa:** boa ideia de IA sem método vira retrabalho. A skill dá o método e já pensa em ética e em escala desde o começo.

## Instale em 2 comandos

Rode no Claude Code (o assistente de IA da Anthropic que funciona no seu terminal ou editor de código):

```
/plugin marketplace add nnaomisato/ai-experiment-planner
/plugin install ai-experiment-planner@ai-experiment-planner
```

O primeiro comando aponta para o marketplace (a "loja" de onde o Claude baixa a skill). O segundo instala. Depois, escreva algo como "quero planejar um experimento de IA".

## As 6 etapas

A conversa acontece uma etapa por vez. A skill explica cada método antes de perguntar.

1. **Contexto:** nome e origem do experimento.
2. **Problema:** o que resolver e como saber que deu certo.
3. **Processo atual:** o passo a passo de hoje. A skill sugere um desenho de solução e ajuda a priorizar por Esforço x Impacto (escala P, M, G).
4. **Hipótese:** o que você sabe, o que acredita e o que vai testar.
5. **Métricas:** o que medir. Usa o HEART, um método do Google para medir experiência (satisfação, uso, adoção, retenção e sucesso na tarefa).
6. **Ética:** 10 dimensões de atenção, com as 2 prioridades e um plano para reduzir riscos. Vem com um [guia de consulta](plugins/ai-experiment-planner/skills/ai-experiment-planner/references/dimensoes-eticas.md) detalhado de cada dimensão.

**No fim:** a skill monta um documento completo, com uma seção de próximos passos (quebrar em tarefas por marcos e distribuir entre responsáveis). Você pode salvar como arquivo `.md` (texto simples, fácil de colar em qualquer lugar).

## Mantenha atualizada

Quando a skill evoluir, rode:

```
/plugin marketplace update ai-experiment-planner
```

## Gostou? Deixe uma estrela

Clique em **Star**, no topo da página. É assim que eu sei quantas pessoas se interessaram.

## Feedback e contribuição

- **Tem uma ideia ou achou um erro?** Abra uma [issue](../../issues/new/choose), um registro público de feedback ou problema. Já tem templates prontos.
- **Quer melhorar a skill?** Envie sua proposta por fork e Pull Request. O passo a passo está no [CONTRIBUTING](CONTRIBUTING.md).

## Licença

MIT. Use, adapte e compartilhe, mantendo o crédito. Detalhes em [LICENSE](LICENSE).
