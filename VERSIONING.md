# Versioning Policy (x.y.z)

- x MAJOR: Core features or system design changes. May include breaking changes.
- y MINOR: Feature branch merges (feat/*).
- z PATCH: Bug fixes (fix/*) or small documentation/config changes.

## Manual release
- Patch: npm run version:patch && npm run release:push
- Minor: npm run version:minor && npm run release:push
- Major: npm run version:major && npm run release:push

## Branch/label conventions
- Feature branches: feat/<topic> → MINOR
- Bug fix branches: fix/<topic> → PATCH
- For MAJOR, add label: major or title contains [major] / mark breaking changes.

## Tags and Releases
- Tags follow vX.Y.Z (e.g., v1.2.3).
