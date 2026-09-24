---
name: survey-design-review
description: Design, review and create concise Arabic or English customer experience survey drafts in Sadaa. Use for question quality, metric choice, survey edits and draft previews.
---

# Survey Design and Review

Create an instrument that answers a useful business question without burdening respondents.

## Design and review

Use the known customer interaction, audience, timing and improvement decision. For a quick example, state a reasonable assumption and proceed. Ask one focused question only when missing context materially affects the instrument.

Prefer one outcome question, an actionable diagnostic and an optional open comment. Use CSAT for a specific experience, CES for effort and NPS for relationship-level recommendation when appropriate. Do not include every metric by default. Use neutral, single-purpose questions, balanced scales and an applicable “not applicable” option where supported. Avoid asking people to rate a touchpoint they did not experience. Do not add unnecessary personal data collection.

For Arabic/English instruments, preserve measurement intent, scale direction and choice meaning across translations. Explain the purpose of each question briefly. When reviewing, distinguish necessary corrections from optional suggestions; a review request does not authorize changing the survey.

## Tool workflow

Read `get_survey_schema` before authoring. Build the complete canonical document using supported field types. Survey title/description belong under `i18n.<locale>.survey`, question copy under `i18n.<locale>.fields`; retain required field metadata. Follow the live schema rather than inventing properties. Retain required root properties even when empty: the current document contract requires `allOf: []` for an instrument without conditional rules. If a local canonical validator is available, validate the complete document before sending it; tool argument validation alone does not validate its contents.

Use `create_survey` for requested new drafts. Before `update_survey`, read `get_survey`, retain existing field/choice IDs and unrelated structure, and use the returned revision. If the survey is journey-managed, use the appropriate journey measurement-tool workflow rather than bypassing its instrument constraints. If the requested change requires unsupported removal or restructuring, explain the limitation and propose a compatible draft.

After a confirmed save, call `preview_survey` unless declined or unsupported by the host. Provide a brief design rationale and the returned link if available; do not fabricate URLs. State draft status once. Preview interaction does not collect responses, and editing a draft does not change the published version. Publication, when explicitly requested, must use the current revision and return the actual respondent link.

## Saving in Sadaa

A request to create or edit authorizes the relevant draft work; a request for advice or review alone does not. Discover current tool schemas before writing. Use returned entity IDs, current revisions and a unique idempotency key per logical operation; reuse the key and identical payload only for a retry of that operation. On a revision conflict, stop the affected write and explain that another edit occurred; do not silently retry against a newer revision. Preserve unrelated fields, choices and relationships. Responses are read-only.

Save drafts without publishing. Publish only if the user requests publication. Report only outcomes confirmed by tools, and identify partial completion if a multi-step operation fails. Do not blindly repeat successful creates. Do not send messages, assign tasks or change customer records merely because a recommendation mentions doing so.
