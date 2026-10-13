---
author: RoyAvanzaPRL
branch: main
status: in-progress
---
# Context7 en RSC

## Intent
RSC detecta Context7 solo si el proyecto tiene `.mcp.json` con `mcpServers.context7`. Cursor ya lo tiene a nivel de usuario. El plan de onboarding lo deja excluido a propósito: el consentimiento del MCP es de esta máquina, no del plan.

## Scope
Dentro: registrar el servidor HTTP oficial en el `.mcp.json` del proyecto y comprobar que el detector de RSC lo ve.
Fuera: no cambiar `policy.context7` ni borrar `.rsc/.no-context7`. El instalador vuelve a crear ese marcador mientras el plan diga `context7: false`. No tocar `~/.cursor/mcp.json`.

## Checklist
- [x] `.mcp.json` del proyecto declara `mcpServers.context7` con `https://mcp.context7.com/mcp`. Prueba: el mismo chequeo que `session-start.mjs` (`hasContext7`) devuelve true.
- [x] El servidor responde. Prueba: una resolución de librería contra Context7 devuelve un id.

## Evidence
- `claude mcp add --scope project --transport http context7 https://mcp.context7.com/mcp` escribió `/home/user/github/test-cl/.mcp.json`.
- Chequeo RSC: `{"hasContext7":true,"type":"http","url":"https://mcp.context7.com/mcp"}`.
- Resolución en vivo: PHP Manual, id `/websites/php_net_manual_en`.
- `claude mcp list` muestra `context7` en HTTP como pendiente de aprobación dentro de Claude Code. En Cursor el servidor ya respondía.

## Next
Si abres Claude Code en este repo, aprueba el servidor una vez (`claude`). En Cursor y para el detector de RSC no queda nada.
