# Fuzzy Input Contract Review

Read before the first progress update when input leaves an outcome, proof, constraint, boundary, iteration policy, or stop condition materially uncertain.

Unless the user says otherwise, presume speech-to-text input. Silently resolve obvious homophones, repetitions, missing punctuation, and implausible words against the active goal and evidence. Treat inferred meaning as an assumption; never change authority, outcome, verification, or risk boundaries. If interpretations differ materially on those points, surface the alternatives and ask one narrow question. Keep confirmed corrections in goal state; promote only stable, user-established conventions to reusable guidance.

Input is **fuzzy** when disfluencies, fragments, vague references, missing success criteria, or conflicting directions leave any contract element materially uncertain. Informal wording alone is not uncertainty; infer ordinary implementation details without changing authority, risk, verification, or outcome.

For fuzzy input, show the draft in the first progress update before creating a Goal or taking substantive action. Mark material inferences `Assumption:` and show a **Contract review** with one finding per element:

1. Does the Outcome describe an observable end state rather than an activity?
2. Can the Verification surface produce evidence independent of the agent's opinion?
3. Do Constraints protect the important safety, quality, and compatibility requirements?
4. Do Boundaries name the allowed systems/actions and avoid silently expanding authority?
5. Does the Iteration policy choose a smallest evidence-producing next action and avoid unchanged retries?
6. Does the Blocked stop condition name the evidence, missing input, or authority needed to proceed?

End with `Decision: proceed`, `Decision: proceed with stated assumptions`, or `Decision: clarification required`. This review checks contract usefulness, not eventual outcome correctness.

Safely repair weak findings once with explicit assumptions and review the revision. Ask one narrow question only if a remaining weakness materially affects objective, proof, authority, safety, or external impact; defer Goal creation and substantive action until resolved. For concrete requests, show the compact contract; itemize the review only when an assumption or material tradeoff needs confirmation.
