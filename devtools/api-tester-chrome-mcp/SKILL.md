---
name: api-tester
description: Test HTTP APIs by executing JavaScript fetch() calls in Chrome DevTools. Use when user asks to test API, call API, check endpoint, verify HTTP response, or validate REST calls.
---

# API Tester

Execute HTTP requests via Chrome DevTools using `evaluate_script` from the `user-chrome-devtools` MCP server.

## Prerequisites

1. A Chrome tab must be open and selected (visible in Cursor MCP connection)
2. If no page is open, use `navigate_page` to open `about:blank` first

## How to Execute API Calls

Use `CallMcpTool` with server `user-chrome-devtools` and tool `evaluate_script`:

```json
{
  "server": "user-chrome-devtools",
  "toolName": "evaluate_script",
  "arguments": {
    "function": "async () => { const res = await fetch('URL', OPTIONS); return { status: res.status, body: await res.json() }; }"
  }
}
```

## Request Patterns

### GET Request

```json
{
  "server": "user-chrome-devtools",
  "toolName": "evaluate_script",
  "arguments": {
    "function": "async () => { const res = await fetch('https://api.example.com/endpoint', { method: 'GET', headers: { 'Authorization': 'Bearer TOKEN' } }); return { status: res.status, headers: Object.fromEntries(res.headers.entries()), body: await res.json() }; }"
  }
}
```

### POST Request (JSON)

```json
{
  "server": "user-chrome-devtools",
  "toolName": "evaluate_script",
  "arguments": {
    "function": "async () => { const res = await fetch('https://api.example.com/endpoint', { method: 'POST', headers: { 'Content-Type': 'application/json', 'Authorization': 'Bearer TOKEN' }, body: JSON.stringify({ key: 'value' }) }); return { status: res.status, body: await res.json() }; }"
  }
}
```

### POST with Form Data

```json
{
  "server": "user-chrome-devtools",
  "toolName": "evaluate_script",
  "arguments": {
    "function": "async () => { const res = await fetch('https://api.example.com/endpoint', { method: 'POST', headers: { 'Authorization': 'Bearer TOKEN' }, body: new URLSearchParams({ key: 'value' }) }); return { status: res.status, body: await res.text() }; }"
  }
}
```

## Workflow

1. **Parse user request**: Extract URL, method, headers, body from user's API test request
2. **Check page state**: Ensure Chrome tab exists, use `navigate_page` to `about:blank` if needed
3. **Build fetch call**: Construct JavaScript fetch() with appropriate options
4. **Execute**: Call `evaluate_script` with the fetch function
5. **Format response**: Display status, headers, body in readable format
6. **Analyze**: Comment on success/failure, suggest fixes if needed

## Response Format

Present results as:

```
✅ Status: 200 OK
Headers: { ... }
Body: { ... }
```

Or for errors:

```
❌ Status: 401 Unauthorized
Error: Invalid token
```

## Error Handling

If `evaluate_script` fails:
- Check if Chrome tab is open and selected
- Suggest user open a new tab if needed
- Offer to try `navigate_page` to open about:blank first

## Notes

- Responses must be JSON-serializable
- Large responses truncated for readability
- Use `filePath` parameter to save large responses to disk if needed

## Important: Authentication & Authorization

Most real-world APIs require authentication (API keys, Bearer tokens, JWT) or authorization headers. This skill executes requests **without credentials by default**.

### When Testing Fails Due to Missing Credentials

1. **Identify the error**: Analyze the response to determine the error type:
   - `401 Unauthorized` - Missing or invalid authentication
   - `403 Forbidden` - Valid credentials but insufficient permissions
   - `400 Bad Request` - Invalid request format or missing required headers
   - `422 Unprocessable Entity` - Validation errors
   - Network/CORS errors - Missing `Access-Control-Allow-Origin` header

2. **Report to user**: When an error occurs:
   - State the HTTP status code and error type
   - Quote relevant error messages from the response body
   - Suggest possible causes (e.g., "Missing Authorization header", "Invalid token format")
   - Ask the user for clarification to proceed

3. **Example error response format**:

```
❌ Status: 401 Unauthorized
Error Type: Authentication Error
Message: "Invalid or expired token"

Possible Causes:
- Missing Authorization header
- Incorrect token format (expected: Bearer <token>)
- Token has expired
- Token is invalid/revoked

Next Steps:
Please provide the API key/token or authorization header, and I'll re-test the request.
```

4. **If credentials are provided by user**:
   - Add the appropriate headers (e.g., `Authorization: Bearer <token>`, `X-API-Key: <key>`)
   - Re-execute the request
   - If still failing, analyze the new error and continue troubleshooting together
