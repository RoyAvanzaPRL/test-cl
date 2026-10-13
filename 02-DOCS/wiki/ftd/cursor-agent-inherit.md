---
author: RoyAvanzaPRL
branch: main
status: in-progress
---
# Modelo de los agentes en Cursor

## Intent
El usuario solo usa Cursor. Los agentes de implementación deben usar el modelo de la conversación, no el Sonnet que RSC escribe por defecto en Cursor.

## Scope
Dentro: `rsc agent-model cursor inherit` en `.rsc.json`.
Fuera: no instalar los subagentes ahora. Siguen aplazados hasta que haya software sustancial. No cambiar el modelo de este chat.

## Checklist
- [x] `agentModels.cursor` es `inherit`. Prueba: `npx @ericrisco/rsc agent-model cursor status` muestra effective inherit.

## Evidence
- `npx @ericrisco/rsc@3.0.22 agent-model cursor inherit` escribió la decisión y re-renderizó 0 archivos: los subagentes aún no están instalados.
- Status: `{"target":"cursor","declared":"inherit","effective":"inherit — the agent uses the session model"}`.

## Next
Cuando el software sustancial instale los subagentes, heredarán el modelo del chat. No queda nada que fijar ahora.
