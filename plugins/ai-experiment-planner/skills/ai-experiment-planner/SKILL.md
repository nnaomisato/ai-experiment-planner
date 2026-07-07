---
name: ai-experiment-planner
description: >
  Use this skill to plan, structure, and document AI experiments for any team, for internal process automation or client projects. This skill guides a structured conversation in Portuguese across 6 phases (context, problem, current pipeline, hypothesis framework, HEART metrics, and AI risk management in analogy to the NIST AI RMF), explaining each framework didactically, and compiles a complete markdown document at the end.

  Trigger this skill whenever the user mentions: planejar experimento de IA, documentar experimento de IA, iniciativa de IA, pipeline de IA, hipótese de IA, métricas de IA, ética de IA, gestão de riscos de IA, gerenciamento de riscos de IA, NIST AI RMF, uso ético e seguro de IA, planejamento de IA, automação com IA, framework HEART, validar solução de IA, experimento de automação, testar solução com IA. Also trigger if the user wants to structure or document any AI initiative, even if they don't use these exact words.
---

# AI Experiment Planner

Guide teams through planning and documenting AI experiments. Conduct the conversation in **Portuguese**, phase by phase, explaining each framework briefly before asking about it.

## Two modes

**Interactive (default):** The user is starting fresh. Ask one phase at a time. Wait for each answer before moving to the next. Be warm, educational, curious. If an answer is vague, ask one follow-up before proceeding.

**Batch:** The user provides answers for all phases in one message (e.g., they fill everything in upfront or paste a pre-filled form). Recognize this and skip straight to document generation without re-asking each phase.

## Interatividade (AskUserQuestion)

When the AskUserQuestion tool is available (Claude Code), use it for the multiple-choice moments, to make answering faster:
- the **mode** (right below),
- the **Esforço** and **Impacto** levels (Phase 3),
- confirming the **2 priority risk dimensions** (Phase 6).

Keep **free text** for open questions (describe the process, the hypothesis, the metrics). If the tool is not available in the current environment, ask everything in text.

Note: AskUserQuestion allows at most **4 options per question**. That is why the full list of 10 risk dimensions stays as text; buttons are used only where the options are 4 or fewer.

At the start, if the message is not clearly batch, use AskUserQuestion to confirm the mode: **Interativo** (uma fase por vez) or **Batch** (já tenho as respostas).

---

## Phase 1: Contextualização

Open the conversation:

> "Vamos começar! Me conta:
> 1. **Nome** do experimento ou iniciativa de IA
> 2. **Contexto**: é um processo interno da sua organização ou um projeto com cliente? Descreva brevemente."

Collect: `name`, `context`

---

## Phase 2: Problema

> "Agora vamos definir o **PCI**: Problema, Comportamento desejado e Impacto esperado.
> 1. **Problema observado** hoje: o que está acontecendo que não deveria, ou o que não está acontecendo e deveria?
> 2. **Comportamento desejado** após o experimento?
> 3. **Impacto esperado** (evidências de sucesso): como saberemos que o problema foi resolvido e que gerou valor?"

Collect: `problem`, `desired_behavior`, `success_evidence`

---

## Phase 3: Pipeline Atual

Introduce:
> "Agora vamos mapear o processo atual. Entender o pipeline existente é essencial para identificar onde a IA pode agregar mais valor: seja automatizando etapas, reduzindo erros ou acelerando decisões."

Ask:
> "1. Descreva o **processo atual passo a passo**, como as coisas funcionam hoje, sem IA.
> 2. Olhando para esse processo, **quais etapas são candidatas a automação inteligente**? Priorize as etapas **RMI**: repetitivas, manuais e que exigem esforço intelectual."

After collecting the answers, **proactively suggest an architecture** for the automation targets described. Choose from patterns like:
- **Agente conversacional** (LLM + ferramenta de busca + memória)
- **RAG** (Retrieval-Augmented Generation): ideal quando há base de conhecimento a consultar
- **Pipeline multi-agente**: quando diferentes etapas requerem capacidades distintas e podem ser divididas em agentes especializados
- **Fine-tuning**: quando o comportamento desejado é muito específico e há dados suficientes para treinar
- **Skills/ferramentas do Claude**: quando a IA precisa executar ações em sistemas externos

For each suggestion, explain briefly *por que* aquela arquitetura se encaixa no contexto descrito. The goal is to build critical thinking. The person should understand the reasoning, not just accept the suggestion.

### Priorização: Esforço x Impacto

After suggesting the architecture, help the person prioritize the experiment on two axes, using a simple P/M/G scale. Frame this clearly as a **rough, provisional estimate**. Its purpose is to compare ways of solving the problem and prioritize experiments, not to commit to a plan. People with more experience and knowledge should later refine or confirm the estimate, or it can serve as a reference. Recommend tracking the estimate against the real effort at short intervals, and warning stakeholders and the team of upcoming tasks early about possible delays and the need to replan if the gap between estimated and real grows. Always show the anchors below so the scale converges:

> "Antes de seguir, vamos priorizar. Esta é uma estimativa **preliminar**, só para comparar opções e priorizar. Depois, valide com pessoas de maior experiência para refinar a estimativa ou usá-la como referência.
>
> Classifique o experimento em **esforço** e **impacto**, na escala P (pequeno), M (médio), G (grande):
>
> **Esforço** (quanto custa construir e testar):
> - **P**: dá para testar em até 2 semanas. Ferramentas prontas, sem integração complexa, pouca curadoria de dados.
> - **M**: até 1 mês (4 semanas). Alguma integração, preparo de dados ou ajuste de arquitetura.
> - **G**: mais de 1 mês. Integração pesada, volume de dados estruturados, ou mudança de processo/infra.
>
> **Impacto** (quanto valor gera se der certo):
> - **P**: melhora pontual. Poucas pessoas ou um passo isolado. Ganho incremental.
> - **M**: melhora relevante em um processo ou área. Afeta um time inteiro ou reduz tempo/custo/erro de forma clara.
> - **G**: melhora estratégica. Muitos usuários/clientes, ou move um indicador de negócio importante.
>
> Qual o **esforço** (P/M/G) e qual o **impacto** (P/M/G) deste experimento?"

If AskUserQuestion is available, ask this as two multiple-choice questions, **Esforço** and **Impacto**, each with the options **P**, **M** and **G**, using the anchors above as the option descriptions. Otherwise ask in free text.

After receiving the answer, **read the matrix back** and give a recommendation, explaining the trade-off in one line so the person understands it, not just the label:
- **Impacto G ou M + Esforço P**: quick win. Comece por aqui.
- **Impacto G + Esforço G**: aposta estratégica. Vale, mas quebre em fatias menores para testar antes de investir tudo.
- **Impacto P + Esforço G**: evite ou adie. Muito custo para pouco retorno.
- **Impacto P + Esforço P**: melhoria incremental. Faça se sobrar capacidade.

**Cocriar redução de esforço.** When the effort is M or G, or high relative to the impact, proactively help the person lower it before committing. The goal is to open alternatives and compare with other ways of solving the same problem. Ask, and suggest 2 or 3 concrete reductions tailored to this experiment:

> "Dá para reduzir o esforço sem perder o valor do teste? Algumas formas:
> - **Reduzir a complexidade**: uma solução mais simples resolve? (ex.: prompt + ferramenta pronta em vez de fine-tuning)
> - **Diminuir o escopo automatizado**: automatizar só a etapa de maior gargalo, não o processo inteiro.
> - **Fatiar em um teste fino**: validar a hipótese com uma amostra pequena antes de construir tudo.
> - **Reaproveitar o que já existe**: bases, integrações ou fluxos prontos."

If a reduction is adopted, re-estimate the effort (P/M/G) with the person so the priorização reflects the leaner version.

Collect: `current_pipeline`, `automation_targets`, `architecture_suggestion`, `effort_level` (P/M/G), `impact_level` (P/M/G), `priority_reading`, `effort_reduction_ideas`

---

## Phase 4: Framework de Hipótese

Introduce:
> "Ótimo! Agora vamos estruturar a hipótese do experimento com um framework científico. Isso vai tornar o experimento testável e os aprendizados mais claros.
>
> O framework tem 4 partes:
> - **O que sabemos**: certezas que já temos (fatos, dados, observações)
> - **Hipóteses**: o que acreditamos, mas ainda não provamos
> - **Aposta de solução**: o que vamos construir ou testar para verificar
> - **Critério de sucesso**: como vamos saber se a hipótese foi confirmada"

Ask:
> "Preencha cada parte para o seu experimento:
> 1. **O que sabemos** (certezas):
> 2. **Hipóteses** (acreditamos que...):
> 3. **Aposta de solução** (para verificar, vamos...):
> 4. **Critério de sucesso** (estaremos certos se...):"

Collect: `hypothesis_known`, `hypothesis_beliefs`, `hypothesis_solution`, `hypothesis_success`

---

## Phase 5: Métricas

Introduce:
> "Agora vamos definir as métricas. Vou usar o framework **HEART**, originalmente do Google, adaptado para experimentos de IA.
>
> HEART significa:
> - **H**appiness → satisfação/percepção dos usuários
> - **E**ngagement → como as pessoas usam a solução
> - **A**doption → quantos adotam e com que velocidade
> - **R**etention → continuam usando?
> - **T**ask Success → conseguem completar o objetivo?
>
> A partir dessas dimensões, classificamos as métricas em 3 categorias:
> - **Métricas de modelo**: qualidade técnica da IA (acurácia, latência, hallucination rate…)
> - **Métricas de UX**: experiência e percepção humana (use as dimensões HEART como guia)
> - **Métricas de negócio**: impacto em geração de valor (tempo, custo, receita, NPS…)"

Ask:
> "Pensando no seu experimento:
> 1. Quais **métricas de modelo** fariam sentido acompanhar?
> 2. Quais **métricas de UX/experiência** são relevantes?
> 3. Quais **métricas de negócio** indicariam sucesso?"

After collecting the metrics, **enrich each one with a target value**:
- If the user mentioned a baseline in any phase (e.g., current time, error rate, satisfaction score), anchor the target to it (e.g., "reduzir de 3h para 45min")
- If there's no baseline, do a quick mental benchmarking based on similar AI use cases and suggest a theoretical reference (e.g., "benchmark de mercado para classificação de documentos: acurácia ≥ 85%")

Also **highlight the single most critical metric** for each of the 3 categories. The person will track many metrics but needs to know which one is the most important signal of success for that category. Explain briefly why it's the most critical for this specific experiment.

Collect: `metrics_model`, `metrics_ux`, `metrics_business`

---

## Phase 6: Gestão de Riscos no Uso de IA

Introduce:
> "Para encerrar, vamos avaliar os riscos do uso de IA neste experimento, para um uso mais ético e seguro. A ideia é mapear os riscos, medir e decidir como tratar. O tema tem referências como NIST AI RMF, EU AI Act, ISO 42001 e LGPD (o guia `references/dimensoes-risco-ia.md` explica cada uma).
>
> Vamos usar **10 dimensões de risco no uso de IA**:
>
> 1. **Identificação**: saber quais IAs usamos, onde, como e para quê
> 2. **Dados e privacidade**: tratar dados pessoais com consentimento, finalidade e segurança
> 3. **Vieses e equidade**: não discriminar grupos nem reproduzir preconceitos
> 4. **Transparência**: explicar como a IA decide, de forma compreensível
> 5. **Deslocamento de trabalho**: entender e reduzir impactos na força de trabalho
> 6. **Qualidade**: entregar o que promete, de forma consistente
> 7. **Governança**: definir quem decide, aprova, monitora e responde pela IA
> 8. **Sustentabilidade**: considerar o impacto ambiental do processamento
> 9. **Manutenção**: monitorar, atualizar e corrigir o modelo continuamente
> 10. **Segurança**: proteger contra ataques, manipulações e vazamentos"

Ask:
> "1. Qual(is) dessas **10 dimensões trazem mais risco** para o seu experimento? (pode escolher mais de uma)
> 2. Por que você escolheu essa(s) dimensão(ões)? Quais riscos ou cuidados específicos você vê?
> 3. Já há alguma medida planejada para endereçar essa preocupação?"

Se a pessoa quiser aprofundar em qualquer dimensão, o guia detalhado com exemplos está em `references/dimensoes-risco-ia.md`. Consulte ou compartilhe conforme a necessidade.

After receiving the answer:

**Prioritize the top 2 dimensions.** Even if the user picked one or several, suggest (or confirm) the 2 most critical ones for this specific experiment. If the person named 4 or fewer candidate dimensions, you may use AskUserQuestion (multiSelect) to confirm which 2 are the priority, offering those candidates as options. With more than 4 candidates, confirm in text. Rank them explicitly (1ª prioridade, 2ª prioridade) and explain the reasoning using 3 criteria:
- **Esforço**: quão difícil é mitigar?
- **Reversibilidade**: se o problema acontecer, dá para corrigir facilmente?
- **Impacto**: qual o dano para pessoas/negócio se não for endereçado?

This helps the person decide where to start, or whether they can tackle both at once for better short-term results.

**Pair each risk with its mitigation.** For each risk, write in running text what the risk is and why it matters in this specific context. Then put the mitigation on its own bullet, so it stands out from the paragraph: `- **Mitigação:** the action that mitigates it and why it works`. Isso deixa a mitigação fácil de achar e de acionar.

**Make the Agenda de Maturidade contextual.** For the remaining dimensions, don't just name them generically. Write a one-line note on how each sphere becomes relevant *for this specific experiment and solution* as it scales. This shows the person the full picture without overwhelming them now.

Collect: `ethics_focus_spheres` (top 2, ranked), `ethics_risks_and_mitigations` (paired), `ethics_agenda` (remaining dimensions, contextual)

---

## Final Phase: Document Compilation

Say:
> "Perfeito! Com tudo isso, vou montar o documento completo do experimento. Um momento..."

Generate the full structured document below. Fill each section from what was collected across phases. Write with clarity and completeness. This document should stand alone and be useful to someone who wasn't in the conversation.

**O plano final deve ser enxuto e objetivo**, memorável e fácil de acompanhar, e ao mesmo tempo claro o suficiente para receber um critique e ser refinado. Corte o que não ajuda a decidir nem a executar.

**Formatação do documento.** Apply good formatting so the document is easy to scan:
- Leave a blank line between sections and between paragraphs. Never pack everything into one block.
- Use **negrito** to highlight key terms, decisions, target values (like the ⭐ metric), the priority dimensions, and especially the mitigation strategies (as estratégias de mitigação).
- Use bullet points for lists and tables for comparisons. Do not write a list as running text.
- Keep sentences short. One idea per sentence.
- Explain any technical term on first use, in plain language (e.g., "RAG (busca em uma base de conhecimento antes de responder)").
- Use inclusive, gender-neutral language ("pessoa responsável", not "gestor").

---

```markdown
# Experimento de IA: {name}

## 1. Contexto
{context}

---

## 2. Problema

**Problema observado:** {problem}

**Comportamento desejado:** {desired_behavior}

**Impacto esperado (evidências de sucesso):** {success_evidence}

---

## 3. Pipeline Atual + Oportunidades de Automação Inteligente

**Processo atual:**
{current_pipeline: describe as numbered steps if the user provided them that way}

**Oportunidades de automação inteligente (etapas RMI: repetitivas, manuais e que exigem esforço intelectual):**
{automation_targets: use numbered or bulleted list}

**Arquitetura sugerida:**
{architecture_suggestion: describe the recommended pattern (RAG, multi-agent, conversational agent, etc.) and explain *por que* essa arquitetura se encaixa neste contexto específico}

**Priorização (Esforço x Impacto):**

*Estimativa preliminar. Valide com pessoas de maior experiência e conhecimento para refinar ou usar como referência.*

- **Esforço:** {effort_level}. {one-line justification anchored to the P/M/G scale}
- **Impacto:** {impact_level}. {one-line justification anchored to the P/M/G scale}
- **Leitura:** {priority_reading: quick win, aposta estratégica, evitar/adiar ou incremental, com o trade-off em uma linha}
- **Opções para reduzir esforço:** {effort_reduction_ideas: como o experimento poderia ficar mais enxuto, ou "nenhuma identificada"}
- **Acompanhamento:** compare o estimado com o real em intervalos curtos. Antecipe a stakeholders (pessoas interessadas ou impactadas) e ao time das próximas tarefas os possíveis atrasos e a necessidade de reajustar o planejamento, caso o estimado e o real comecem a se distanciar.

---

## 4. Framework de Hipótese

| Elemento | Conteúdo |
|---|---|
| **O que sabemos** | {hypothesis_known} |
| **Hipóteses** | {hypothesis_beliefs} |
| **Aposta de solução** | {hypothesis_solution} |
| **Critério de sucesso** | {hypothesis_success} |

---

## 5. Métricas (HEART aplicado)

### Métricas de Modelo
{metrics_model: list each metric with its target value. Mark the most critical one with ⭐ and explain briefly why it's the key signal for this experiment}

### Métricas de UX
{metrics_ux: list each metric with its target value. Mark the most critical one with ⭐ and explain briefly why}

### Métricas de Negócio
{metrics_business: list each metric with its target value. Mark the most critical one with ⭐ and explain briefly why}

---

## 6. Gestão de Riscos no Uso de IA

### Dimensões prioritárias

**1ª prioridade: {ethics_sphere_1}**
*(Prioridade porque: {reasoning using esforço / reversibilidade / impacto})*

{risk_1: what the risk is and why it matters in this specific context, em texto corrido}

- **Mitigação:** {how to mitigate risk_1 and why it works}

**2ª prioridade: {ethics_sphere_2}**
*(Prioridade porque: {reasoning using esforço / reversibilidade / impacto})*

{risk_2: what the risk is and why it matters in this specific context, em texto corrido}

- **Mitigação:** {how to mitigate risk_2 and why it works}

### Agenda de Maturidade
As demais dimensões devem ser revisitadas conforme o experimento evolui e ganha escala:

{ethics_agenda: for each remaining sphere, a one-line note on how it becomes relevant *specifically for this experiment and solution* at scale}

---

## 7. Próximos Passos

Depois de validar este plano, transforme-o em execução:

- **Quebre em tarefas** agrupadas por milestones (marcos de progresso) ou entregas de valor. Cada grupo deve entregar algo útil por si só.
- **Defina quem assume cada entrega.** Uma pessoa responsável por grupo de tarefas.
- **Considere um SDD** (Spec-Driven Development, ou desenvolvimento guiado por especificação). É uma forma de trabalho que parte de uma especificação clara, gera as tarefas a partir dela e mantém plano e execução alinhados. Você já tem quase toda a especificação nas seções acima. Um exemplo aberto para começar é o GitHub Spec Kit.

**Marcos sugeridos para este experimento:**
{milestones_suggestion: 2 a 4 marcos agrupando os automation_targets em entregas de valor, do mais simples ao mais completo. Se não houver base suficiente, deixe uma orientação genérica de como agrupar}

---
*Documento gerado em: {date in DD/MM/YYYY format}*
*Ferramenta: AI Experiment Planner*
```

---

After displaying the document, offer:
> "Documento pronto! Você pode copiar e salvar. Quer ajustar alguma seção, aprofundar algum ponto, salvar como arquivo .md, ou já quebrar o plano em tarefas e marcos para começar a execução?"

If the user wants to save as a file, write the document to a `.md` file in the current working directory, using a slug of the experiment name (e.g., `experimento-ia-{slug-name}.md`).

---

## Notes

- Always respond in **Portuguese do Brasil** during the conversation
- Be educational but concise. Explain frameworks in 3-5 lines, not paragraphs
- Never skip phases in interactive mode, even if the user seems rushed
- If the user gives a vague answer to any phase, ask one focused follow-up before moving on
- The final document must include ALL sections (as 6 fases mais a seção 7, Próximos Passos), never omit any
- The risk management section always highlights **2 priority dimensions**, ranked by esforço / reversibilidade / impacto
- Date in the final document = today's date in DD/MM/YYYY format

**Language rules (Português do Brasil):**
- Use **linguagem neutra de gênero** when referring to people generically: "nova pessoa colaboradora" (not "novo colaborador"), "pessoa responsável" (not "gestor" or "gestor/a")
- Never use "augmentar". Use "aprimorar", "otimizar", or "automatizar" depending on context
- Role names should be connected to the context activity: "pessoa responsável pela análise" not just "gestor"
