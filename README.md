# dependabot-agent-fixture-npm

**Test fixture. Not for use. Deliberately vulnerable.**

npm-workspace counterpart of [dependabot-agent-fixture](https://github.com/michaelpipkin/dependabot-agent-fixture), proving [dependabot-agent](https://github.com/michaelpipkin/dependabot-agent)'s multi-line advisory handling on **npm**.

Two workspace members pin different majors of `js-yaml`, each vulnerable to a different line of [`GHSA-mh29-5h37-fv8m`](https://github.com/advisories/GHSA-mh29-5h37-fv8m) (and `GHSA-h67p-54hq-rp68`):

| package | js-yaml | patched at |
| --- | --- | --- |
| `packages/consumer-old` | `3.14.1` | `3.15.0` |
| `packages/consumer-new` | `4.1.0` | `4.2.0` |

The agent writes per-line version-selector overrides (`js-yaml@3`, `js-yaml@4`) into the root `package.json` `overrides` block, keeping each consumer on its own line. The pinned versions are vulnerable on purpose — do not "fix" them.
