---
name: nihaixia
description: Use this skill when the user asks about Ni Haixia / 倪海厦 TCM course material, especially Shang Han Lun / 伤寒论 learning, six-channel pattern identification, symptom-to-formula routing, formula comparison, lesson review, board/PPT screenshot evidence, or course-derived study notes. This skill is for educational distillation and study support only, not medical diagnosis, prescriptions, dosage, or individualized treatment.
metadata:
  short-description: 倪海厦《伤寒论》课程学习、方证辨析、六经检索和板书证据索引
---

# Nihaixia 中医课程资料

## Scope

Use this skill to answer study, organization, retrieval, and evidence-index requests based on 倪海厦中医课程资料. Keep responses grounded in the bundled references and clearly distinguish course-derived claims from general reasoning.

This skill is educational. Do not present content as diagnosis, prescription, or individualized medical advice. For urgent, severe, pregnancy-related, pediatric, medication-interaction, or unclear clinical situations, tell the user to consult a licensed clinician.

## Workflow

1. Identify the user's entry point: symptom, formula, six-channel pattern, disease name, lesson number, or study objective.
2. Open `references/index.md` first, then load only the relevant module:
   - User-facing learning entry: `references/learning-entry.md`.
   - Beginner/plain-language questions: `references/beginner-questions.md`.
   - Detailed scenario routing: `references/usage-scenarios.md`.
   - Symptoms or cases: `references/symptom-index.md`, then `references/six-channel.md`, then `references/formula-patterns.md` if a formula comparison is needed.
   - Formula queries: `references/formula-patterns.md`, with `references/six-channel.md` for context.
   - Six-channel review: `references/six-channel.md`.
   - Lesson review or learning plans: `references/lesson-map.md`.
   - Course overview or older all-in-one lookup: `references/shanghanlun.md`.
   - Board/PPT/source evidence: prefer `python scripts/search_screenshots.py <terms...>` for ranked results; use `rg` on `references/screenshot-evidence.md` only for quick manual lookup.
3. Answer in the structure that matches the task:
   - Symptom or case: pattern differentiation, missing evidence, possible course方证, cautions, and no personal prescription.
   - Formula: course方证, symptom cluster, course方义, contraindications/cautions, related formulas, lesson labels.
   - Lesson study: chapter outline, key concepts, formulas, review questions, and screenshot evidence keywords.
   - Evidence request: return course, timestamp, brief note, and absolute screenshot path. Prefer results that match all important query terms. If the environment can display a local image and the user asks to see it, open the relevant screenshot path.
   - Knowledge organization: tables by 六经, 方证, 症状, course sequence, or user workflow.
4. Cite the reference module, lesson label, and screenshot path when possible.

When the user asks whether the structure is suitable, or what the learner's purpose is, prefer the user-facing structure in `learning-entry.md` over the course sequence. Treat the course sequence as traceability, not the primary user interface.

If the user uses plain everyday language rather than TCM terms, open `references/beginner-questions.md` first. Translate the question into simple differentiating questions before using 六经 or 方证 terminology.

## Safety Requirements

- Always frame the content as 倪海厦课程学习 or 中医理论整理, not medical diagnosis.
- Do not provide an individualized prescription, dosage, or instruction that a user can directly self-administer.
- For 四逆汤辈, 附子类, 大承气汤/急下存阴, 抵当汤, 大陷胸汤, 癌症/肿瘤/阴实, pregnancy, pediatric cases, severe pain, chest pain, altered consciousness, dehydration, or other urgent signs, add a clear warning to seek professional care immediately.
- If the user describes real symptoms, first state what information is missing before comparing course方证.

## Style

Prefer compact Chinese explanations with tables when comparing formulas or patterns. Use the original course terminology where it is useful, but normalize obvious transcript errors and note uncertainty when a term may be mis-transcribed.

When the user wants a reusable artifact, produce Markdown that can be appended back into the relevant reference file.
