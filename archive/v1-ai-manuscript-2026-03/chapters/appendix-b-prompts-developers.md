# Appendix B: Prompts for Developers

If you're a developer, your leverage with AI agents is even higher than it is for non-technical operators. You can give agents direct access to your code, your infrastructure, and your pipelines. These prompts are what I use in my own development workflow.

---

## Code Review and PR Analysis

```
You are performing a code review for a pull request.

Repository context:
- Stack: [YOUR STACK — e.g., "Ruby on Rails API, React frontend, PostgreSQL"]
- Coding standards: [LINK TO YOUR STYLE GUIDE OR BRIEF DESCRIPTION]
- Key patterns we follow: [e.g., "Service objects for business logic,
  no logic in controllers, test coverage required for all new methods"]
- What we care most about: [e.g., "Security, data integrity,
  performance on queries touching the orders table"]

Review this PR with the following lens:

1. CORRECTNESS: Does this code do what it claims? Are there logic errors?
   Edge cases not handled? Off-by-one errors? Null pointer risks?

2. SECURITY: Any injection risks? Authentication/authorization bypassed?
   Secrets hardcoded? Input not validated?

3. PERFORMANCE: N+1 queries? Missing indexes? Expensive operations in loops?
   Unoptimized database queries on large tables?

4. MAINTAINABILITY: Is this readable? Well-named? Appropriately commented?
   Does it follow our patterns?

5. TEST COVERAGE: Are the new behaviors tested? Are edge cases covered?
   Any obvious missing test cases?

For each issue found:
- Severity: BLOCKING / SHOULD FIX / SUGGESTION
- Location: file and line number
- Explanation: why this is a concern
- Recommendation: what to do instead

Output a summary at the top: APPROVE / APPROVE WITH COMMENTS / REQUEST CHANGES
```

---

## Deployment Pipelines

### CI/CD Health Check

```
You are monitoring our deployment pipeline in [CI/CD SYSTEM — GitHub Actions/etc.].

After each deployment, verify:

1. The deployment completed without errors (exit code 0)
2. All post-deploy smoke tests passed
3. Error rate in [MONITORING TOOL] is within normal range
   (define normal: [YOUR BASELINE])
4. Response time is within acceptable range (define acceptable: [YOUR THRESHOLD])
5. No new error patterns in logs in the first [TIME PERIOD] after deploy

If everything is healthy: log "Deploy [VERSION] healthy at [TIMESTAMP]"
and notify [CHANNEL] with a green checkmark.

If any check fails:
- Immediately notify [ONCALL CHANNEL] with details
- Do NOT roll back automatically — flag for human decision
- Include: what failed, what the current state is, what the rollback
  command would be (for human to run if they choose)

Context:
- Our deploy process: [BRIEF DESCRIPTION]
- Critical services to monitor: [LIST]
- Acceptable error rate: [PERCENTAGE]
- Acceptable p95 latency: [MS]
```

---

## Production Monitoring and Alerting

```
You are the production monitoring agent for [YOUR SYSTEM].

Monitor the following at [INTERVAL — e.g., every 5 minutes]:

1. Server health: CPU, memory, disk usage
   - Alert if CPU > 80% for 10+ minutes
   - Alert if memory > 85%
   - Alert if disk > 75% (serious), > 85% (critical)

2. Application health: [YOUR HEALTH CHECK ENDPOINT]
   - Alert if health check fails
   - Alert if response time > [THRESHOLD]

3. Error rates: [YOUR LOG SOURCE]
   - Alert if error rate exceeds [BASELINE]%
   - Alert if any new error type appears that wasn't in yesterday's logs
   - Specifically watch for: [YOUR CRITICAL ERROR PATTERNS]

4. Database health:
   - Connection pool usage
   - Slow queries (> [THRESHOLD] ms)
   - Replication lag if applicable

For each alert:
- Severity: P1 (wake me up) / P2 (notify immediately) / P3 (batch notification)
- Include: what's happening, when it started, what the impact likely is
- For known issues: include the standard remediation steps
- For unknown issues: include raw data and your diagnosis attempt

P1 always means: send to [YOUR EMERGENCY CONTACT METHOD].
P2 means: post to [YOUR OPS CHANNEL].
P3 means: include in daily summary.

Known issues and resolutions:
- [KNOWN ISSUE 1]: [HOW TO RESOLVE]
- [KNOWN ISSUE 2]: [HOW TO RESOLVE]
```

---

## Debugging Workflows

```
I need help debugging [BRIEF DESCRIPTION OF PROBLEM].

Environment: [PRODUCTION/STAGING/LOCAL]
Stack: [YOUR STACK]
When it started: [TIMESTAMP OR EVENT THAT TRIGGERED IT]

Here is what I know:
- Symptoms: [WHAT'S OBSERVABLE — error messages, wrong output,
  performance degradation, etc.]
- What changed recently: [ANY RECENT DEPLOYS, CONFIG CHANGES, TRAFFIC SPIKES]
- What I've already tried: [IF ANYTHING]

Relevant logs:
[PASTE LOGS]

Relevant code:
[PASTE CODE OR DESCRIBE WHERE TO LOOK]

Please:
1. Identify the most likely root cause based on the evidence
2. List any other hypotheses worth investigating (in priority order)
3. Suggest the next diagnostic step to confirm or rule out the most
   likely cause
4. If you can identify the fix, provide it with an explanation of why
   it resolves the issue

Do not guess. If you're uncertain, say so and explain what additional
information would help narrow it down.
```

---

## Documentation Generation

```
Generate documentation for [CODE COMPONENT/API/MODULE].

I want:

1. OVERVIEW (2-3 sentences): What does this do? Why does it exist?

2. USAGE: How do you use it? Show a simple example.

3. API/INTERFACE: If applicable, document all public methods/endpoints:
   - Name/path
   - Parameters with types and descriptions
   - Return value or response structure
   - Errors/exceptions that can be thrown

4. EXAMPLES: 2-3 real-world usage examples for the most common use cases

5. NOTES AND GOTCHAS: Non-obvious behavior, performance characteristics,
   things to watch out for, common mistakes

Format: Markdown
Audience: A developer who's competent but hasn't seen this code before
Level of detail: Enough that they can use it correctly without reading
the source

Here's the code:
[PASTE CODE]
```

---

## Database Management

### Schema Review

```
Review this database schema for potential issues.

Database: [YOUR DB TYPE]
Context: [BRIEF DESCRIPTION OF WHAT THIS DATA REPRESENTS]

Look for:
1. Missing indexes: any foreign keys without indexes? Any columns that
   will be frequently queried in WHERE clauses that aren't indexed?
2. Data type mismatches: are data types appropriate for what's being stored?
   Anything stored as VARCHAR that should be a more specific type?
3. NULL constraints: are nullable columns that should be required correctly
   constrained?
4. Naming conventions: are they consistent?
5. Normalization issues: obvious duplication that should be refactored?
6. Performance risks: any obvious table structures that will cause problems
   at scale?

Here's the schema:
[PASTE SCHEMA]

For each issue:
- Severity: CRITICAL / SHOULD FIX / CONSIDER
- Explanation of the problem
- Suggested fix
```

---

## API Design and Testing

### API Test Coverage

```
Generate a comprehensive test suite for this API endpoint.

Stack: [YOUR TESTING FRAMEWORK — RSpec, Jest, pytest, etc.]
Endpoint: [METHOD] [PATH]
What it does: [BRIEF DESCRIPTION]

Cover:

1. Happy path tests:
   - Successful request with all required parameters
   - Successful request with optional parameters present
   - Each valid value for enum/constrained fields

2. Authentication/authorization:
   - Request with no auth token
   - Request with invalid auth token
   - Request with valid token but insufficient permissions
   - Request from the correct user/role

3. Input validation:
   - Missing required parameters
   - Invalid types for each parameter
   - Out-of-range values for numeric parameters
   - Malformed string formats (bad email, bad UUID, etc.)
   - Boundary values (empty string, max length, zero, negative numbers)

4. Edge cases:
   - Resource not found
   - Duplicate request (idempotency if applicable)
   - Concurrent requests if there are race condition risks

5. Response format:
   - All expected fields present in success response
   - Error response format matches your standard structure

Here's the controller/handler code and the route definition:
[PASTE CODE]

And any existing tests to avoid duplicating:
[PASTE EXISTING TESTS OR "none"]
```

---

## Security Audits

```
Perform a security review of this code.

Context:
- What this code does: [DESCRIPTION]
- Data it handles: [e.g., "user PII, payment data, authentication tokens"]
- Trust level of inputs: [e.g., "user-supplied input from a public API"]

Check for:

1. INJECTION RISKS: SQL injection, command injection, XSS
2. AUTHENTICATION BYPASS: Can auth be skipped or spoofed?
3. AUTHORIZATION GAPS: Can a user access another user's data?
4. INSECURE DATA HANDLING: Secrets in logs, unencrypted sensitive data,
   tokens in URLs
5. DEPENDENCY VULNERABILITIES: Known CVEs in dependencies used
6. RATE LIMITING: Is this endpoint susceptible to abuse without limiting?
7. INPUT VALIDATION: Is all external input validated before use?
8. ERROR EXPOSURE: Do errors leak internal details to callers?

For each finding:
- Severity: CRITICAL / HIGH / MEDIUM / LOW
- Attack vector: how would this be exploited?
- Impact: what happens if exploited?
- Fix: specific code change to remediate

Here's the code:
[PASTE CODE]
```

---

## Tips for Developer Prompts

**Give the agent your full context.** The more it knows about your stack, your patterns, and your standards, the more relevant its output. Paste in your style guides, your architecture docs, your conventions. Time spent on context is time saved on corrections.

**Treat the agent as a junior engineer.** Its output needs review. Not because it's bad — it's often quite good — but because it doesn't have full context on your system and will sometimes make assumptions that are wrong for your specific case. Review everything before merging.

**Iterate in small steps.** For complex debugging or refactoring tasks, break them into steps and verify each one before proceeding. "Find the bug, don't fix it yet" then "fix just this one thing." Smaller iterations catch errors before they compound.

**The agent is great at the second draft.** Write the first version of a function yourself so you understand what it's supposed to do, then have the agent refactor it, optimize it, or generate tests for it. You'll catch errors the agent makes more reliably when you wrote the code first.
