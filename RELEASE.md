# A Release Checklist

- Copy over new release folder to `/temp`
- Copy over normal files to web directories
  - `$ npm run copy`
- Create latin subsets and copy to web directories
  - `$ npm run subset`
- Update version strings from `?v=X.XX` across in `_default.scss` and `_variable.scss` files
- Update CSS files
  - `$ npm run generate-css`
- Publish release
  - `$ npm version X.Y.Z` (updates `package.json` + commits the change + makes the git tag)
  - `$ npm publish`
