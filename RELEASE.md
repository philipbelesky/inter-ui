# A Release Checklist

- Copy over new font files
- Bump version numbers in `inter-ui.css` and `inter-ui-hinted.css`
- `$ npm version X.Y.Z` (updates `package.json` + commits the change + makes the git tag)
- `$ npm publish`