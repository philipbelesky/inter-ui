# A Release Checklist

- Copy over new release folder to `/temp`
- Copy over normal files to web directories
  - `$ npm run copy`
- Create latin subsets and copy to web directories
  - `$ npm run subset`
- Publish release
  - `$ npm version X.Y.Z` (updates `package.json` + commits the change + makes the git tag)
  - `$ npm publish`
