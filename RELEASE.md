# A Release Checklist

- Delete existing files in `/web`
- Copy over contents of the `/web` folder from the release zip to `/temp`
- Copy over normal-setted font files to `web` directories:
  - `$ npm run build-supersets`
- Create latin subsets and copy them to `*-latin` directories:
  - `$ npm run build-subsets`
- Update version strings from `?v=X.XX` across in `_default.scss` and `_variable.scss` files
- Publish release
  - `$ npm version X.Y.Z` (updates `package.json` + commits the change + makes the git tag)
  - `$ npm publish`

## Build Dependencies

- Standard npm stuff
- `fonttools` and `brotli` for glyphhanger, see <https://github.com/zachleat/glyphhanger#prerequisite-pyftsubset>
