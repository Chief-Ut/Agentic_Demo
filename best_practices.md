# Best Practices: Software Development Lifecycle

A living document covering best practices from product initiation to delivery.

---

## 1. Initiation

- **Define the problem before the solution** — understand the "why" before writing a single line of code.
- **Identify stakeholders early** — know who has input, who decides, and who is affected.
- **Write a clear problem statement** — one paragraph that anyone can understand.
- **Set measurable success criteria** — define what "done" and "successful" look like upfront.
- **Assess feasibility** — technical, financial, and time constraints should be understood before committing.
- **Document assumptions and risks** — things you believe to be true but haven't confirmed yet.

---

## 2. Planning

- **Break work into milestones** — each milestone should deliver something tangible and testable.
- **Use a task tracker** — GitHub Issues, Linear, or Jira; keep it updated and visible to the team.
- **Prioritize ruthlessly** — distinguish between must-have, should-have, and nice-to-have (MoSCoW method).
- **Plan for unknowns** — leave buffer time; complexity always reveals itself late.
- **Define the tech stack early** — changing core technologies mid-project is extremely costly.
- **Agree on branching strategy** — e.g., trunk-based development or GitFlow, before the first commit.
- **Set up environments early** — dev, staging, and production should be defined from the start.

---

## 3. Design

- **Design for the user first** — wireframes and user flows before architecture diagrams.
- **Keep architecture simple** — only introduce complexity when simplicity provably fails.
- **Separate concerns** — UI, business logic, and data access should be distinct layers.
- **Design APIs before implementing them** — agree on contracts between components early.
- **Document architectural decisions (ADRs)** — record what was decided, why, and what alternatives were rejected.
- **Plan for failure** — design with error states, retries, and fallbacks in mind from the beginning.
- **Security by design** — authentication, authorization, and data protection are not afterthoughts.

---

## 4. Development

- **Write code for humans first** — clarity beats cleverness; the next reader may be you.
- **Follow the single responsibility principle** — each function, class, and module does one thing well.
- **Keep commits small and focused** — one logical change per commit.
- **Write meaningful commit messages** — describe *why* the change was made, not just *what* changed.
- **Never commit secrets** — use `.env` files, secret managers, and always add secrets to `.gitignore`.
- **Code review everything** — no code goes to main without at least one other set of eyes.
- **Avoid premature optimization** — make it work, make it right, then make it fast.
- **Handle errors explicitly** — never silently swallow exceptions or failures.
- **Use version control consistently** — commit early, commit often, push before end of day.
- **Keep dependencies minimal and updated** — every dependency is a liability; vet them before adding.

---

## 5. Testing

- **Test as you build** — don't defer testing to the end of the project.
- **Write tests at the right level** — unit tests for logic, integration tests for boundaries, E2E for critical flows.
- **Aim for meaningful coverage, not 100%** — test the logic that matters; don't chase vanity metrics.
- **Test edge cases and failure paths** — not just the happy path.
- **Never mock what you can test for real** — mocks that diverge from reality produce false confidence.
- **Automate regression tests** — anything that broke once should have a test to prevent it breaking again.
- **Test in an environment that mirrors production** — staging should be as close to prod as possible.
- **Performance test before launch** — know your system's limits before users discover them.

---

## 6. Code Review

- **Review for correctness first, style second** — does it work correctly before does it look clean.
- **Be specific in feedback** — "this could cause a race condition because X" not "this looks wrong."
- **Approve with intent** — don't rubber-stamp; a review is a shared responsibility.
- **Keep PRs small** — large PRs don't get reviewed properly; aim for under 400 lines of change.
- **Use automated checks** — linters, formatters, and CI should catch style issues before human review.
- **Discuss, don't dictate** — frame suggestions as questions or options, not mandates.

---

## 7. CI/CD & Automation

- **Automate the build pipeline** — every push should trigger lint, test, and build automatically.
- **Fail fast** — if tests fail, block the merge; never let broken code reach main.
- **Deployments should be repeatable and scripted** — no manual steps that exist only in someone's head.
- **Use environment variables for configuration** — never hardcode environment-specific values.
- **Implement rollback capability** — every deployment should be reversible quickly.
- **Deploy frequently in small increments** — big-bang deployments are high-risk; ship small changes often.
- **Tag releases** — every production deployment should map to a tagged commit.

---

## 8. Documentation

- **Document decisions, not just code** — the code shows what; docs explain why.
- **Keep a changelog** — track what changed between versions in plain language.
- **Write a useful README** — setup instructions, how to run, how to test, and how to contribute.
- **Document APIs** — every public interface should have clear input/output documentation.
- **Update docs with the code** — stale documentation is worse than no documentation.
- **Write runbooks for operations** — document how to handle incidents, restarts, and common failures.

---

## 9. Security

- **Validate all input at system boundaries** — never trust user input or external API responses.
- **Use least privilege** — services, users, and tokens should only have the permissions they need.
- **Encrypt sensitive data at rest and in transit** — use HTTPS everywhere; never store plaintext passwords.
- **Rotate secrets regularly** — treat credentials as temporary, not permanent.
- **Audit dependencies for vulnerabilities** — run `npm audit`, `pip check`, or equivalent regularly.
- **Plan for breach** — assume it will happen; know how you will detect, respond, and recover.

---

## 10. Delivery & Launch

- **Define a launch checklist** — go/no-go criteria should be agreed upon before launch day.
- **Launch to a subset of users first** — canary releases or feature flags reduce blast radius.
- **Monitor from day one** — logging, error tracking, and alerting should be live before launch.
- **Have a rollback plan ready** — know exactly how to revert if something goes wrong.
- **Communicate proactively** — notify stakeholders and users of changes, downtime, or issues.
- **Measure against success criteria** — go back to the metrics defined in initiation and track them.

---

## 11. Post-Launch & Iteration

- **Conduct a retrospective** — what went well, what didn't, what to change next time.
- **Treat bugs as priority signals** — a bug in production is feedback about a gap in your process.
- **Monitor performance continuously** — set up dashboards and alerts, not just one-time checks.
- **Gather user feedback early** — real users will surface problems no internal team anticipated.
- **Refactor intentionally** — schedule time for technical debt; don't let it accumulate invisibly.
- **Deprecate cleanly** — remove old features with notice; don't let dead code accumulate.

---

## 12. AI / Agentic Systems (Specific to this Project)

- **Define the agent's scope clearly** — an agent that tries to do everything does nothing well.
- **Log all agent actions** — observability is critical when debugging autonomous behavior.
- **Human-in-the-loop checkpoints** — add approval steps for irreversible or high-impact actions.
- **Fail gracefully** — agents should handle errors without cascading failures.
- **Version control your prompts** — treat prompts like code; track what changes behavior.
- **Evaluate outputs, not just functionality** — correctness in AI systems requires evaluation frameworks.
- **Guard against prompt injection** — treat all external content passed to an LLM as untrusted input.

---

*Last updated: 2026-03-15*
