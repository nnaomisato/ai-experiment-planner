> **Exemplo ilustrativo.** Documento gerado com a skill AI Experiment Planner, para mostrar como fica o output final. Dados fictícios.

# Experimento de IA: Criação de Performance Improvement Plan (PIP) para colaboradores

## 1. Contexto

Processo interno de RH. Apoia as mentorias de desempenho, da criação ao acompanhamento do PIP (plano de melhoria de performance).

---

## 2. Problema

**Problema observado:** o acompanhamento não é estruturado. Falta clareza sobre o foco urgente, prazo e critério de avaliação da evolução. Fica subjetivo e, muitas vezes, sem alinhamento entre quem mentora e quem é mentorado.

**Comportamento desejado:** toda mentoria com um PIP documentado e acompanhado. Sem cobranças desalinhadas e sem demora em decisões de reconhecimento ou evolução.

**Impacto esperado (evidências de sucesso):** melhores decisões baseadas em dados e menos surpresas no meio do processo.

---

## 3. Pipeline Atual + Oportunidades de Automação Inteligente

**Processo atual:**
1. Avaliações são realizadas.
2. Identificam-se os pontos de maior gargalo.
3. Conversa com a pessoa sobre situações, comportamento e impacto gerado.
4. Definem-se competências-chave a trabalhar.
5. Marcam-se encontros periódicos.

**Oportunidades de automação inteligente (etapas RMI: repetitivas, manuais e de esforço intelectual):**
- Gerar o **rascunho inicial do PIP** a partir dos gargalos da avaliação, para revisar na conversa do passo 3.
- (2ª fase) Completar o plano após as competências-chave, com brainstorm de como trabalhá-las, priorização e frequência de acompanhamento das evidências.

**Arquitetura sugerida:**
Alvo: **RAG** (busca em uma base antes de responder) + **template estruturado** + passo **conversacional** de refino. No piloto, versão enxuta: sem integração, usando PIPs anteriores como exemplos no prompt e o template preenchido a partir de um resumo colado.

**Priorização (Esforço x Impacto):**

*Estimativa preliminar. Valide com pessoas de maior experiência e conhecimento para refinar ou usar como referência.*

- **Esforço:** P (após reduções). Cola-se o resumo da avaliação e o modelo preenche o template, sem integração.
- **Impacto:** G. Afeta todas as mentorias e melhora decisões de reconhecimento e cobrança.
- **Leitura:** quick win (Impacto G + Esforço P). Comece por aqui.
- **Opções para reduzir esforço (adotadas):** resumo da avaliação preenche o template; automatizar só o rascunho inicial; rodar com 3 mentorias reais.
- **Acompanhamento:** compare o estimado com o real em intervalos curtos. Antecipe a stakeholders (pessoas interessadas ou impactadas) e ao time possíveis atrasos e reajustes de planejamento.

---

## 4. Framework de Hipótese

| Elemento | Conteúdo |
|---|---|
| **O que sabemos** | Hoje não existe histórico de PIPs. |
| **Hipóteses** | Com PIPs, teremos mais confiança para decidir mais rápido sobre reconhecimento ou cobrança, de forma assertiva. |
| **Aposta de solução** | Automatizar o processo com IA para agilizar a documentação e facilitar o acompanhamento, consultável no futuro. |
| **Critério de sucesso** | Nos prazos definidos, ter mais confiança e evidências para decidir com base em dados, com aprendizado mútuo e motivos claros. |

---

## 5. Métricas (HEART aplicado)

### Métricas de Modelo
- **Aderência** do rascunho às competências e gargalos reais (1 a 5): alvo ≥ 4.
- ⭐ **Aproveitamento do rascunho:** avaliação Likert de quem mentora, com comentário qualitativo, sobre o quanto o rascunho serviu. Alvo ≥ 4. É o sinal de que a IA ajuda de verdade, sem virar retrabalho.
- **Sem alucinação:** zero fatos ou competências inventados que não estão na avaliação.

### Métricas de UX
- ⭐ **Clareza percebida** por quem é mentorado (entende foco, prazo e avaliação, 1 a 5): alvo ≥ 4. É o centro do problema: acabar com a subjetividade.
- **Alinhamento:** PIPs com o campo de acordo mútuo preenchido e confirmado pelas duas partes: alvo ≥ 90%.
- **Esforço de montar o PIP:** de horas para menos de 15 min.

### Métricas de Negócio
- ⭐ **Cobertura:** mentorias com PIP documentado e acompanhado: alvo 100% (hoje 0). Adoção real prova o valor.
- **Tempo de decisão** para reconhecimento ou cobrança após o prazo: estabelecer a linha de base e reduzir.
- **Surpresas no processo** (cobranças desalinhadas): tender a zero.

---

## 6. Gestão de Riscos no Uso de IA

### Dimensões prioritárias

**1ª prioridade: Dados e privacidade**
*(Prioridade porque: impacto alto e reversibilidade baixa. Um vazamento de dado de desempenho não se desfaz. O esforço de mitigar é moderado.)*

Dados de desempenho de pessoas entram no modelo e ficam num documento de piloto. Importa porque são dados sensíveis, sob a LGPD (Lei Geral de Proteção de Dados), e um acesso amplo expõe a pessoa avaliada.

- **Mitigação:** usar só o necessário no resumo, restringir o acesso ao documento às pessoas envolvidas, definir prazo de descarte e não usar os dados para treinar o modelo. Funciona porque limita a exposição ao mínimo.

**2ª prioridade: Qualidade**
*(Prioridade porque: impacto alto no objetivo, mas reversível. Dá para revisar o rascunho antes de usar. Esforço de mitigar baixo.)*

Um rascunho genérico ou impreciso gera cobrança desalinhada, exatamente o problema que o experimento quer resolver. Importa porque um PIP errado prejudica a pessoa e a confiança no processo.

- **Mitigação:** manter uma pessoa no controle (quem mentora revisa e edita antes de usar), acompanhar o aproveitamento pela Likert e exigir zero alucinação. Funciona porque o rascunho é ponto de partida, nunca decisão final.

### Agenda de Maturidade
As demais 8 dimensões devem ser revisitadas conforme o experimento evolui e ganha escala:

- **Identificação:** registrar qual modelo e versão gera os rascunhos e para quê, num inventário simples, conforme mais mentorias usam.
- **Vieses e equidade:** a avaliação de origem pode ter viés. Ao escalar, medir se o rascunho favorece ou prejudica algum perfil.
- **Transparência:** deixar claro para quem é mentorado como e por que o PIP foi montado.
- **Deslocamento de trabalho:** reforçar que a IA apoia quem mentora, não substitui o julgamento humano, e comunicar isso ao time.
- **Governança:** definir quem aprova o uso e responde por um PIP mal gerado.
- **Sustentabilidade:** usar o menor modelo que resolve e evitar reprocessar, conforme o volume de PIPs cresce.
- **Manutenção:** versionar o template e o prompt e revisar quando a qualidade cair.
- **Segurança:** proteger o acesso aos dados de desempenho e ao modelo, com controle de acesso.

---

## 7. Próximos Passos

Depois de validar este plano, transforme-o em execução:

- **Quebre em tarefas** agrupadas por marcos ou entregas de valor.
- **Defina quem assume cada entrega.** Uma pessoa responsável por grupo.
- **Considere um SDD** (Spec-Driven Development, desenvolvimento guiado por especificação): parte de uma especificação clara, gera as tarefas e mantém plano e execução alinhados. Exemplo aberto: GitHub Spec Kit.

**Marcos sugeridos para este experimento:**
1. Template do PIP definido, com campos de foco, prazo, competências e evidências.
2. Rascunho gerado a partir do resumo da avaliação, testado em 3 mentorias reais.
3. Coleta leve de aproveitamento (Likert) e ajuste do prompt para a próxima leva.

---
*Documento gerado em: 07/07/2026*
*Ferramenta: AI Experiment Planner*
