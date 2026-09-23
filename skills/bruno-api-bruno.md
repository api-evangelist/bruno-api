---
name: bruno
description: Use when building, testing, and collaborating on API collections. Reach for Bruno when you need to send REST, GraphQL, gRPC, or WebSocket requests; write automated tests; manage environments and secrets; run collections via CLI in CI/CD pipelines; or collaborate on API workflows through Git.
metadata:
    mintlify-proj: bruno
    version: "1.0"
---

# Bruno Skill Reference

## Product Summary

Bruno is a Git-friendly, offline-first API client for developers. Store collections as plain-text files (`.bru` or `.yml` format) in your repository, send requests across REST, GraphQL, gRPC, WebSocket, and SOAP protocols, write JavaScript tests and pre/post-request scripts, manage variables across environments, and run collections from the CLI for CI/CD integration. Collections are stored locally—no cloud account required. Primary documentation: https://docs.usebruno.com

**Key files and commands:**
- Collection root: `bruno.json` (`.bru` format) or `opencollection.yml` (YAML format)
- Requests: `request-name.bru` or `request-name.yml`
- Environments: `environments/env-name.bru` or `environments/env-name.yml`
- CLI: `bru run [folder-name] [options]`

## When to Use

Use Bruno when:
- **Building API requests** — Create and organize REST, GraphQL, gRPC, WebSocket, or SOAP requests in a collection
- **Writing tests** — Add assertions or JavaScript test scripts to validate API responses
- **Managing environments** — Switch between local, staging, and production environments with different variables
- **Automating workflows** — Run collections from the command line with data-driven testing (CSV/JSON files)
- **Collaborating via Git** — Store collections in version control and review API changes like code
- **CI/CD integration** — Run collections in Docker, GitHub Actions, Jenkins, or Azure DevOps pipelines
- **Handling secrets** — Store API keys and tokens securely with secret masking and optional secret manager integration
- **Chaining requests** — Pass data from one request to the next using scripts and variables

## Quick Reference

### Collection Structure

| File/Folder | Purpose |
|---|---|
| `bruno.json` or `opencollection.yml` | Collection root metadata |
| `request-name.bru` or `.yml` | Individual request definition |
| `folder-name/` | Organize requests into folders |
| `environments/local.bru` | Environment-specific variables |
| `.env` | Process environment variables (optional) |

### Variable Scopes (Highest to Lowest Precedence)

| Scope | Storage | Use Case |
|---|---|---|
| Runtime | Memory | Set during execution via `bru.setVar()` |
| Request | `request.bru` | Request-specific values |
| Folder | `folder.bru` | Shared across folder requests |
| Environment | `env-name.bru` | Environment-specific (local, prod, etc.) |
| Collection | `opencollection.yml` | Shared across entire collection |
| Global | Local storage | Workspace-level variables |

### Common CLI Commands

```bash
# Run entire collection
bru run

# Run specific folder
bru run folder-name

# Run with environment
bru run --env Local

# Run with CSV data (data-driven testing)
bru run --csv-file-path data.csv

# Run with environment variable override
bru run --env-var API_KEY=abc123

# Run with tag filtering
bru run --tags=smoke,sanity

# Run in parallel
bru run --parallel

# Run with custom reporter
bru run --reporter json --output results.json

# Run with Safe Mode (default v3.0.0+)
bru run

# Run with Developer Mode (external packages, filesystem)
bru run --sandbox=developer
```

### Request Configuration Tabs

| Tab | Purpose |
|---|---|
| **Params** | Query parameters (key-value pairs) |
| **Auth** | Authentication (Bearer, Basic, OAuth2, AWS Sig, etc.) |
| **Headers** | HTTP headers |
| **Body** | Request payload (JSON, form data, multipart, raw) |
| **Pre-request** | JavaScript executed before sending |
| **Tests** | Assertions or test scripts (post-response) |
| **Vars** | Request-level variables |

### Authentication Types

| Type | Use Case |
|---|---|
| **Bearer Token** | JWT, API keys in Authorization header |
| **Basic** | Username + password (Base64 encoded) |
| **OAuth 2.0** | Authorization Code, Client Credentials, Password flow |
| **AWS Signature** | AWS API requests (v4 signing) |
| **Digest** | Legacy HTTP Digest auth |
| **NTLM** | Windows authentication |
| **OAuth 1.0** | Legacy OAuth with signature methods |

### Scripting API Essentials

```javascript
// Request object (pre-request and test scripts)
req.getUrl()                    // Get request URL
req.setUrl(url)                 // Set request URL
req.getMethod()                 // Get HTTP method
req.setMethod(method)           // Set HTTP method
req.getHeader(name)             // Get header value
req.setHeader(name, value)      // Set header
req.getBody()                   // Get request body
req.setBody(body)               // Set request body
req.setTimeout(ms)              // Set timeout

// Response object (test scripts only)
res.status                      // HTTP status code
res.statusText                  // Status message
res.getBody()                   // Response body (auto-parsed JSON)
res.getHeader(name)             // Get response header
res.getHeaders()                // All response headers
res.getResponseTime()           // Response time in ms

// Variables
bru.getVar(key)                 // Get runtime variable
bru.setVar(key, value)          // Set runtime variable
bru.getEnvVar(key)              // Get environment variable
bru.setEnvVar(key, value)       // Set environment variable
bru.getGlobalEnvVar(key)        // Get global variable
bru.setGlobalEnvVar(key, value) // Set global variable
bru.interpolate(string)         // Interpolate {{variables}} in string

// Testing (Chai assertions)
expect(res.status).to.equal(200)
expect(res.getBody()).to.have.property('id')
expect(res.getBody()).to.have.jsonBody()
expect(res.getBody()).to.have.jsonSchema(schema)
```

### Variable Interpolation

```javascript
// In request fields (URL, headers, body, etc.)
{{variableName}}                // Reference any variable
{{$guid}}                       // Generate UUID
{{$timestamp}}                  // Current Unix timestamp
{{$randomInt}}                  // Random integer
{{$randomEmail}}                // Random email (faker.js)
{{?Prompt text}}                // Prompt user for input

// In scripts
bru.interpolate("{{variableName}}")  // Evaluate variables in string
```

## Decision Guidance

### When to Use `.bru` vs `.yml` Format

| Aspect | `.bru` (Legacy) | `.yml` (OpenCollection) |
|---|---|---|
| **Recommended for** | Existing collections | New collections |
| **Format** | Custom markup language | Standard YAML |
| **Tooling** | Bruno-specific | Works with any YAML tool |
| **Migration** | Supported via CLI | One-way conversion available |
| **Collection root** | `bruno.json` | `opencollection.yml` |

**Action:** Use `.yml` for new collections. Migrate existing `.bru` collections if integrating with external tools.

### When to Use Assertions vs Test Scripts

| Approach | Use When |
|---|---|
| **Assertions** | Simple checks (status code, response field exists, value equals) |
| **Test Scripts** | Complex logic, conditional tests, loops, custom error handling |

**Example:**
```javascript
// Assertion (simple)
test("status is 200", () => {
  expect(res.status).to.equal(200);
});

// Test script (complex)
test("validate user data", () => {
  const body = res.getBody();
  if (body.users && body.users.length > 0) {
    body.users.forEach(user => {
      expect(user).to.have.property('id');
      expect(user.email).to.match(/^[^\s@]+@[^\s@]+\.[^\s@]+$/);
    });
  }
});
```

### When to Use Safe Mode vs Developer Mode

| Mode | Features | Use Case |
|---|---|---|
| **Safe Mode** (default v3.0.0+) | Built-in libraries only (lodash, moment, etc.) | Production CI/CD, shared collections |
| **Developer Mode** | External npm packages, filesystem access | Local development, custom scripts |

**Action:** Use Safe Mode in CI/CD. Pass `--sandbox=developer` locally if you need external packages.

### When to Use Secret Variables vs .env Files

| Approach | Storage | Use Case |
|---|---|---|
| **Secret Variables** | Encrypted locally on machine | Sensitive values (API keys, tokens) |
| **.env File** | Plain text file (not committed) | Non-sensitive config, local development |
| **Secret Manager** | HashiCorp Vault, AWS Secrets, Azure Key Vault | Enterprise secret management |

**Action:** Mark sensitive variables as "secret" in the UI. Use `.env` for local config. Integrate secret managers for team/production workflows.

## Workflow

### 1. Create and Organize a Collection

1. **Create a collection** — Click "New Collection" in Bruno or initialize with `bruno.json`
2. **Create folders** — Organize requests by feature or endpoint (e.g., `/users`, `/posts`)
3. **Create requests** — Add HTTP/GraphQL/gRPC requests to folders
4. **Save to Git** — Commit the collection folder to version control

### 2. Configure Environments and Variables

1. **Create environment files** — Add `environments/local.bru`, `environments/prod.bru`, etc.
2. **Define variables** — Add base URL, API keys, tokens as environment variables
3. **Mark secrets** — Check the "secret" checkbox for sensitive values (they won't be exported)
4. **Select active environment** — Choose which environment to use in the UI or CLI

### 3. Build and Test Requests

1. **Create a request** — Set URL, method, headers, body
2. **Add authentication** — Select auth type and configure (Bearer, OAuth2, etc.)
3. **Use variables** — Reference `{{baseUrl}}`, `{{apiKey}}` in URL, headers, body
4. **Write tests** — Add assertions or test scripts to validate responses
5. **Run the request** — Send and inspect response

### 4. Automate with Scripts

1. **Pre-request script** — Generate dynamic data, set headers, modify URL
2. **Post-response script** — Extract values, set variables for next request, validate response
3. **Request chaining** — Use `bru.setVar()` to pass data between requests
4. **Error handling** — Use `req.onFail()` or conditional logic in tests

### 5. Run Collections via CLI

1. **Install Bruno CLI** — `npm install -g @usebruno/cli`
2. **Run collection** — `bru run` (from collection directory)
3. **Use environments** — `bru run --env Production`
4. **Data-driven testing** — `bru run --csv-file-path data.csv`
5. **Generate reports** — `bru run --reporter json --output results.json`
6. **Integrate with CI/CD** — Add `bru run` to GitHub Actions, Jenkins, etc.

### 6. Collaborate via Git

1. **Commit collection** — Push `.bru` or `.yml` files to Git
2. **Review changes** — PRs show human-readable diffs of request changes
3. **Merge conflicts** — Resolve in Git or Bruno's GUI (Pro/Ultimate)
4. **Share collections** — Clone repo and open in Bruno

## Common Gotchas

- **Safe Mode breaking changes (v3.0.0+)** — CLI defaults to Safe Mode; external npm packages fail unless you pass `--sandbox=developer`
- **Variables not interpolating in body** — Use `{{variableName}}` syntax; check variable scope and precedence
- **CSV data not replacing body** — CSV rows are available as variables; you must reference them with `{{columnName}}` in the body. The body is not auto-merged with row data
- **Secrets not masked in exports** — Variables marked as "secret" are not exported when you export a collection; pass them via CLI with `--env-var` instead
- **Request body not sent with GET** — Some APIs reject GET with a body; use query parameters instead
- **OAuth2 token not auto-refreshing** — Enable "Auto-refresh" in OAuth2 settings; ensure refresh URL and credentials are correct
- **Pre-request script modifying body but test sees old body** — Scripts run in order: pre-request → send → test. If you modify the body in pre-request, the test sees the modified version
- **Multipart form data not sending files** — Use "Multipart Form" body type, not "JSON"; click "Add File" to upload
- **Variables with special characters** — Use `bru.interpolate()` in scripts; direct `{{var}}` syntax may fail with certain characters
- **Collection not syncing with Git** — Ensure collection folder is in a Git repo; use CLI commands or Bruno's GUI to push/pull
- **Tests not running in CLI** — Tests only run when you execute `bru run`; they don't run on individual request sends in the UI
- **Timeout errors in CI/CD** — Increase timeout with `req.setTimeout(ms)` in pre-request script or `--timeout` CLI flag
- **Circular variable references** — Avoid setting a variable to a value that references itself (e.g., `{{var}}` → `{{var}}`); this causes infinite loops

## Verification Checklist

Before submitting work with Bruno collections:

- [ ] **Collection structure** — Requests are organized in folders; collection root file exists (`bruno.json` or `opencollection.yml`)
- [ ] **Environments configured** — At least one environment file exists with required variables (base URL, API keys)
- [ ] **Secrets marked** — Sensitive variables (API keys, tokens) are marked as "secret" in the UI
- [ ] **Tests written** — Each request has assertions or test scripts validating the response
- [ ] **Variables used** — Requests reference environment variables (e.g., `{{baseUrl}}`) instead of hardcoded URLs
- [ ] **Authentication configured** — Requests use the correct auth type (Bearer, OAuth2, etc.) with variables for tokens
- [ ] **Scripts tested locally** — Pre-request and post-response scripts run without errors
- [ ] **Request chaining works** — If using `bru.setVar()` to pass data, verify the next request receives the value
- [ ] **CLI runs successfully** — `bru run` executes without errors; tests pass
- [ ] **Git-ready** — Collection is committed to Git; `.env` and secret files are in `.gitignore`
- [ ] **Documentation** — Add descriptions to requests, variables, and complex scripts for team clarity
- [ ] **No hardcoded secrets** — No API keys, tokens, or passwords in request bodies, headers, or URLs

## Resources

**Comprehensive navigation:** https://docs.usebruno.com/llms.txt

**Critical documentation pages:**
- [Getting Started](https://docs.usebruno.com/introduction/getting-started) — Overview and quick-start guides
- [JavaScript API Reference](https://docs.usebruno.com/testing/script/javascript-reference) — Complete scripting API (`req`, `res`, `bru` objects)
- [Bruno CLI](https://docs.usebruno.com/bru-cli/overview) — Command-line execution and CI/CD integration

---

> For additional documentation and navigation, see: https://docs.usebruno.com/llms.txt