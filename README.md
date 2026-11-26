# Developer Roadmap Content Repository

This repository stores Markdown topic content used by [roadmap.sh](https://roadmap.sh). It is a content repository, not the deployed roadmap.sh website or application.

## What lives here

- `roadmaps/<roadmap-slug>/content/<topic-slug>@<node-id>.md` — individual roadmap topic content. Preserve the node ID and filename: the synchronization tools use them to associate content with roadmap nodes.
- [`readme.md`](readme.md) — the broader roadmap catalogue and project overview.
- [`contributing.md`](contributing.md) — contribution rules and content-formatting guidance.
- [`scripts/readme.md`](scripts/readme.md) — documentation for the maintainer sync and cleanup scripts.
- `package.json`, `pnpm-lock.yaml`, and `pnpm-workspace.yaml` — JavaScript tooling, scripts, and dependency lockfile.

## Browse and contribute

- [Browse roadmap content](roadmaps/)
- [Read the roadmap catalogue](readme.md)
- [Contribution guidelines](contributing.md)
- [Sync and cleanup script documentation](scripts/readme.md)
- [License](license)

## Local setup

The repository's GitHub Actions workflows use Node.js 24 and pnpm 11. To install the project tooling locally:

```bash
git clone https://github.com/NirmalyaLenka/developer-roadmap.git
cd developer-roadmap
corepack enable
corepack prepare pnpm@11 --activate
pnpm install --frozen-lockfile
```

Installing dependencies does not publish content or synchronize anything with the roadmap database.

## Editing roadmap content

1. Find the relevant topic under `roadmaps/<roadmap-slug>/content/`.
2. Follow the rules in [`contributing.md`](contributing.md), including the required content structure and formatting.
3. Keep the existing filename and node ID unless the maintainers explicitly direct a structural change.
4. Review the diff before submitting a pull request and check the repository's GitHub Actions results.

The root `package.json` defines formatting, synchronization, and cleanup scripts; it does not define a root `build` or `test` script.

## Maintainer scripts and safety

Read [`scripts/readme.md`](scripts/readme.md) before using any maintenance script.

- `sync:content-to-repo` retrieves content from the roadmap database and writes files into the working tree.
- `sync:repo-to-database` submits repository content to the roadmap database. It requires an authorized sync secret and can change remote data.
- `cleanup:orphaned-content` compares local files with database state and can rename or delete content files.
- `format` runs Prettier with `--write .`, which can rewrite files across the repository.

Do not run database synchronization or broad cleanup commands as a first-run test. Use them only with the required authorization, the intended roadmap scope, and a reviewed diff or cleanup report. Keep secrets out of committed files and public logs.

## Verification status

This README documents the repository layout and available scripts. It does not claim that dependencies were installed, a build or test suite was run, database synchronization succeeded, or the website was deployed during this review.

## Maintenance & Audit

- **Audit date:** 11 November 2026
- **Documentation status:** README reviewed and audit record added on this date.
- **Scope:** Documentation entry point only. Source files, dependencies, build status, security posture, and runtime behavior have not been independently validated in this README update.
- **Maintenance note:** Documentation baseline recorded through 11 November 2026. This is not a claim that the project is fully tested, secure, or production-ready.
- **Next review:** Re-check setup instructions, dependency versions, security considerations, and project-specific tests when making functional changes.

## Contact

Maintained up to 25 November 2026.

If you encounter any problems, please contact [carmodbhai@gmail.com](mailto:carmodbhai@gmail.com).
