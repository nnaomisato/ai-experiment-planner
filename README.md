# AI Experiment Planner

Skill do Claude Code para planejar experimentos de IA éticos e escaláveis, do problema à documentação.

Ela conduz você por 6 fases, em português, e entrega um documento pronto para compartilhar.

## O que a skill faz

Conversa guiada, uma fase por vez, explicando cada framework antes de perguntar:

1. **Contexto**: nome e origem do experimento.
2. **Problema**: o que resolver e como medir sucesso.
3. **Pipeline atual**: mapeia o processo de hoje e sugere uma arquitetura de IA.
4. **Hipótese**: o que sabemos, o que acreditamos, o que vamos testar.
5. **Métricas**: framework HEART aplicado a modelo, UX e negócio.
6. **Ética**: 10 esferas de consideração, com as 2 prioridades e um plano de mitigação.

No fim, gera um documento markdown completo. Você pode salvar como `.md`.

## Instalação

No Claude Code, rode os 2 comandos:

```
/plugin marketplace add nnaomisato/ai-experiment-planner
/plugin install ai-experiment-planner@ai-experiment-planner
```

Pronto. Para começar, escreva algo como "quero planejar um experimento de IA".

## Atualizar

Quando a skill evoluir, rode:

```
/plugin marketplace update ai-experiment-planner
```

## Gostou? Deixe uma estrela

Se a skill foi útil, clique em **Star** no topo desta página. É o sinal que uso para saber quantas pessoas se interessaram.

## Feedback e contribuição

- **Feedback ou dúvida:** abra uma [issue](../../issues/new/choose).
- **Ideia de melhoria:** proponha por fork e Pull Request. Veja o [CONTRIBUTING](CONTRIBUTING.md).

## Licença

MIT. Use, adapte e compartilhe, mantendo o aviso de crédito. Veja [LICENSE](LICENSE).
