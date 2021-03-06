# get-repo-package-json

Fetch a GitHub repository's package.json file using the GitHub API

## Installation

```sh
npm install get-repo-package-json --save
```

## Usage

The basics:

```js
const getPackage = require('get-repo-package-json')

getPackage('segmentio/nightmare', function (err, pkg) {
  if (err) throw err
  // pkg is a JSON object
})
```

To fetch a specific commit/branch/tag, use a long-form URL:

```js
getPackage('https://github.com/monkey/business/tree/experiment', function (err, pkg) {
  if (err) throw err
  // pkg is a JSON object
})
```

Or specify a `ref` option:

```js
getPackage('monkey/business', {ref: '0e783153885ed78f71d138085a77644ff8e59aa1'}, function (err, pkg) {
  if (err) throw err
  // pkg is a JSON object
})
```

To see more supported repository string formats, see the
[github-url-to-object](https://zeke.github.io/github-url-to-object/) demo.

## API

This package exports a single function:

### `getPackage(repository, [options], callback)`

- `repository` (string) - Any string supported by
[github-url-to-object](https://zeke.github.io/github-url-to-object/).
- `options` (optional object)
  - `access_token` - GitHub API key. Can also be set as a `GITHUB_ACCESS_TOKEN` environment variable.
  - `ref` - The name of the commit/branch/tag. Defaults to nothing, so the GitHub API will return the repo's default branch.
- `callback(err, pkg)` (function) - node-style error-first callback

## Tests

```sh
npm install
npm test
```

## Dependencies

- [github-url-to-object](https://github.com/zeke/github-url-to-object): Extract user, repo, and other interesting properties from GitHub URLs
- [got](https://github.com/sindresorhus/got): Simplified HTTP requests

## Dev Dependencies

- [chai](https://github.com/chaijs/chai): BDD/TDD assertion library for node.js and the browser. Test framework agnostic.
- [mocha](https://github.com/mochajs/mocha): simple, flexible, fun test framework
- [nock](https://github.com/node-nock/nock): HTTP Server mocking for Node.js
- [require-dir](https://github.com/aseemk/requireDir): Helper to require() directories.
- [standard](https://github.com/feross/standard): JavaScript Standard Style


## License

MIT

_Generated by [package-json-to-readme](https://github.com/zeke/package-json-to-readme)_
