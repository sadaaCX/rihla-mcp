---
name: journey-measurement-design
description: Design customer journeys, touchpoints and measurement plans, and create or edit journey drafts in Sadaa. Use for deciding what to measure at each customer interaction.
---

# Journey Measurement Design

Map the customer's goals and interactions to evidence that helps an operating team improve the experience.

## Design

Use the user's service, audience and journey boundaries. Organize around customer goals before, during and after the experience where relevant, rather than copying the organization's departments. For every proposed touchpoint identify the customer goal, likely friction to investigate, measurement purpose and suitable collection timing. Label assumed friction as a hypothesis.

Use Sadaa terms: touchpoints, sub touchpoints, measurements and measurement tools. Select metrics that inform a concrete decision; avoid repeating NPS at every interaction. Present a compact map or table with stages, interactions, measures and intended decisions. Reuse existing surveys or journey elements when appropriate without duplicating them.

## Tool workflow

Find existing journeys with `list_journeys` and read `get_journey` before editing. Read `list_measurement_definitions` and `list_measurement_tool_catalog` before choosing definition IDs or tool configurations. Follow pagination when needed; use returned contracts and supported nature values rather than invented identifiers.

When draft creation is requested, use `create_journey`, then create touchpoints, sub touchpoints and measurements in dependency order. Refresh the journey revision after each mutation when needed; do not reuse a stale revision across a batch. Retain returned child IDs. Configure measurement tools only from the catalog's supported contracts.

Before linking an existing survey, inspect its fields and the targeted measurements; use `link_survey_to_measurement_tool` with compatible field mappings and current survey/journey revisions. Do not claim linking is possible if field compatibility cannot be established. Read `list_measurement_tools` for preparation status and update tokens. A queued tool is not a completed survey. Retry a failed preparation only when requested or justified within the authorized task, using current revision/update token; do not poll or retry indefinitely.

Use `update_measurement_tool_survey` for wording changes to a journey-managed instrument while preserving its structure. Publishing a journey can also publish eligible managed surveys: explain this scope before executing a requested publication when it is not already clear from the request.

Return the actual `rihla_url` as a clickable link and summarize what was saved or remains pending. Journeys are viewed and edited in Rihla; do not promise an embedded journey preview.

## Saving in Sadaa

A request to create or edit authorizes the relevant draft work; a request for advice or review alone does not. Discover current tool schemas before writing. Use returned entity IDs, current revisions and a unique idempotency key per logical operation; reuse the key and identical payload only for a retry of that operation. On a revision conflict, stop the affected write and explain that another edit occurred; do not silently retry against a newer revision. Preserve unrelated fields, choices and relationships. Responses are read-only.

Save drafts without publishing. Publish only if the user requests publication. Report only outcomes confirmed by tools, and identify partial completion if a multi-step operation fails. Do not blindly repeat successful creates. Do not send messages, assign tasks or change customer records merely because a recommendation mentions doing so.
