# MVP Gateway

This repository is a reusable baseline template for creating new repositories with consistent governance, security, and collaboration standards.

## Included Baseline Artifacts

- `CODEOWNERS` for default ownership and review routing
- `SECURITY.md` for vulnerability reporting guidance
- `CONTRIBUTING.md` for contribution workflow expectations
- `.github/ISSUE_TEMPLATE/` for standardized bug and feature intake
- `.github/PULL_REQUEST_TEMPLATE.md` for consistent pull request quality
- `.github/workflows/` placeholder for project-specific GitHub Actions automation
- `.gitignore` for local and generated files

## Ownership

- `@Arid-Nova/developers` owns application and project files by default.
- `@Arid-Nova/admins` owns governance, security, licensing, and `.github/` files.

CODEOWNERS routing becomes enforceable only when repository rulesets or branch
protection require code-owner approval.

## Work Tracking

Keep issues and pull requests in the repository where the work belongs. The
Arid-Nova organization project will provide the cross-repository portfolio
view; items should be linked to that project rather than duplicated.

The future governance repository will provision the organization project,
standard fields and views, and automation to add and reconcile repository
issues and pull requests.

## Existing Repositories

This template establishes defaults for new repositories; it does not
automatically update repositories created before the template. The future
governance repository will onboard existing repositories separately by:

1. Inventorying and classifying repositories.
2. Applying non-destructive repository settings and organization policies.
3. Opening pull requests for shared-file updates instead of overwriting
   project-specific files.
4. Enabling required rulesets after required workflows are available.
5. Supporting documented exemptions and continuously reconciling drift.

## How to Use

1. Create a new repository from this template.
2. Confirm the repository rulesets and required checks applied by the governance automation.
3. Select the project stack and add its project-specific build, test, dependency, and GitHub Actions workflow files.
4. Replace any project-specific links or contact details.
5. Start development with consistent policies already in place.

This baseline is intentionally language-agnostic. Stack-specific workflows,
dependency manifests, Dependabot ecosystems, and devcontainer configuration
should be added by each project rather than assumed by this template.

Every project must use GitHub Actions, but this template intentionally does not
provide a universal CI/CD workflow. Each project owns the workflows and
required checks appropriate for its stack.

## License

See [LICENSE](LICENSE).
