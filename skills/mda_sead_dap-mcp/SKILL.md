---
name: mda_sead_dap-mcp
description: Skill da REST API do MDA SEAD: Declaração de Aptidão ao PRONAF (DAP) na MCP.AI: 1 endpoint em /api/mda_sead_dap. MDA SEAD: Declaração de Aptidão ao PRONAF (DAP), consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# MDA SEAD: Declaração de Aptidão ao PRONAF (DAP) — REST API skill

Você tem acesso à **MDA SEAD: Declaração de Aptidão ao PRONAF (DAP)** REST API na MCP.AI.

> MDA SEAD: Declaração de Aptidão ao PRONAF (DAP), consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/mda_sead_dap
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/mda_sead_dap/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"birthdate":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/mda_sead_dap/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `mda_sead_dap_consultar`

MDA SEAD: Declaração de Aptidão ao PRONAF (DAP), consulta em fonte oficial. _(POST /api/mda_sead_dap/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | Parâmetro de consulta "cnpj". |
| `cpf` | string | Não | Parâmetro de consulta "cpf". |
| `birthdate` | string | Sim | Parâmetro de consulta "birthdate". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_mda_sead_dap` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
