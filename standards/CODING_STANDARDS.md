# Coding Standards

These standards apply to all repositories in the Aryv Labs organisation unless a repository states otherwise. They describe how we write, review and release code, and they apply to maintainers and external contributors alike.

## 1. Principles

- **Clarity over cleverness.** Code is read far more often than it is written.
- **Reproducibility.** Anyone should be able to run a project end to end from a clean checkout.
- **Evidence.** Claims about performance or quality are supported by measurements.
- **Maintainability.** We publish only what we are prepared to maintain.

## 2. Commit messages

We follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

```
<type>: <short imperative summary>

<optional body explaining what changed and why>
```

- **Types:** `feat`, `fix`, `docs`, `refactor`, `test`, `perf`, `build`, `ci`, `chore`.
- Subject line in the imperative mood, no more than 72 characters, no trailing full stop.
- Use the body to explain motivation and context when the change is not self-evident.
- One logical change per commit. Messages such as "update", "fix stuff" or "final" are not acceptable.

Examples:
- `feat: add configurable reranker model`
- `fix: handle empty pages during PDF ingestion`
- `docs: clarify embedding setup in README`

## 3. Branches and pull requests

- `main` is always in a working, releasable state.
- Work happens on short-lived branches named by purpose, for example `feat/streaming-responses` or `fix/pdf-ingestion`.
- Every change to `main` goes through a pull request.
- A pull request should have a clear title and description, link any related issue, and stay focused on one concern.
- Pull requests are merged only when checks pass and the change has been reviewed.
- We prefer squash merges, with the pull request title used as the commit message.

## 4. Code style

**General**
- Follow the established conventions of the language and the existing style of the repository.
- Use descriptive names. Avoid abbreviations that are not widely understood.
- Keep functions small and single-purpose.
- Remove dead code and commented-out blocks rather than leaving them in place.

**Python**
- Follow [PEP 8](https://peps.python.org/pep-0008/).
- Format and lint with an automated tool (Ruff is our default) and configure it in the repository so results are consistent.
- Use type hints for public functions and interfaces.
- Write docstrings for public modules, classes and functions.
- Target a documented minimum Python version and state it in the README.

## 5. Testing

- New behaviour and bug fixes include tests where practical.
- Tests must be runnable with a single documented command.
- Tests should be deterministic. Set random seeds where randomness affects results.
- Do not call paid or rate-limited external services from tests by default. Use fakes or recorded responses, or mark such tests clearly as optional.

## 6. Dependencies and environments

- Declare all dependencies in the repository (for example, `requirements.txt` or `pyproject.toml`).
- Pin versions, or version ranges, deliberately. Separate runtime and training or development dependencies.
- Add a dependency only when it is justified. State the licence of any new dependency and confirm it is compatible with the repository licence.
- Keep installation instructions in the README current.

## 7. Configuration and secrets

- Secrets, API keys and tokens are never committed. Use environment variables and document each one required.
- Provide an example configuration file in place of real values.
- Keep `.gitignore` current so that credentials, local data, model outputs and caches are excluded.
- Any suspected exposure of a secret is treated as compromised: rotate it immediately.

## 8. Documentation

Every repository includes, at minimum:

- A README covering purpose, installation, a minimal working example, configuration, and known limitations.
- A licence file.
- Contribution guidance, or a reference to the organisation-wide guidance.
- A statement of the expected response time for issues.

Documentation is updated in the same pull request as the code it describes.

## 9. Evaluation and reproducibility

For projects that make claims about quality, accuracy or performance:

- State the dataset, method and metrics used.
- Provide the means to reproduce reported results.
- Report limitations and what the results do not show.
- Document the provenance and licence of any data and models used.

## 10. Security and licensing

- Report suspected vulnerabilities privately to the maintainers rather than in public issues.
- Respect the licences of all third-party code, data and models.
- Do not include proprietary, confidential or client-derived material in any public repository.
- Code is released under the MIT Licence unless a repository states otherwise.

## 11. Releases and versioning

- Use [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`.
- Tag each release and keep a changelog of notable changes.
- A release must satisfy the documentation and reproducibility requirements above.
- Repositories that can no longer be maintained are archived with a note in the README.

## 12. Review checklist

Before approving a pull request, reviewers confirm that:

- [ ] The change does what its description states, and no more.
- [ ] Commit messages follow Section 2.
- [ ] Tests and checks pass, and new behaviour is covered where practical.
- [ ] No secrets, credentials or confidential material are included.
- [ ] Documentation is updated.
- [ ] Dependencies and their licences are acceptable.
