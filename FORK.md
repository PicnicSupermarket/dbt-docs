# dbt-docs fork

This repository holds a fork of
[dbt-docs](https://github.com/dbt-labs/dbt-docs) (referred as
`upstream`). Its main purpose is to serve as a staging area for some
features we're developing.

We intend to follow upstream development, and diverge from it as
little as possible. Therefore:
- Every PR in this repository must be accompanied by a PR upstream,
  and/or an issue upstream where the feature is discussed with
  upstream developers.
- If a feature developed in this repository ends up being developed
  upstream with an alternative implementation, the upstream implementation
  will be kept (to the extent it doesn't break anything or conflict
  with other features).
  
This repository holds 2 important branches:
- `main`: a copy of upstream `main`.
- `fork`: the default branch, in which PRs are merged. It is regulary
  merged with `main`.
  
## How to report a bug

Please be mindful that if a bug is not related to the specific
features developed in this repository, but rather upstream, it should
be opened in [dbt-docs](https://github.com/dbt-labs/dbt-docs).

Feel free to open an issue in this repository to discuss a bug you
encountered related to the specific features added in this fork, or
for any question or suggestion.

## How to contribute

Contributions are certainly welcome! Keep in mind however that
contributions should ideally be submitted upstream, as to keep this
fork from diverging.

New features must be accompanied by a new entry in the Changelog
below, referencing the PR or issue opened upstream, to make it easy to
keep track of the differences between upstream and this fork.

Fixes related to features developed in this fork need an update in the
Changelog entry related to the feature they are fixing.

PRs must be created against the `fork` branch.

To help keep things trackable, the following branch naming conventions
are used:
- New feature: `[username]/feature-[feature-name]`
- Bug fix: `[username]/fix-[fix-name]`

## Changelog

- Add support for rendering additional metadata
    - Upstream issue: https://github.com/dbt-labs/dbt-docs/issues/424
    - Fork PR: https://github.com/PicnicSupermarket/dbt-docs/pull/1

  To enable users in adding any metadata to dbt docs in a structured way. The key `meta.meta_docs` is treated
  differently and rendered in a structured way on the webpage. The structure of `meta` and `meta_docs` should be
  as follows:

  ```
      meta:
        meta_stuff: meta_stuff
        meta_docs:
          - - foo: bar
            - baz: qux
          - - fiz: buz
            - bla: bla
  ```

  `meta_docs` enables users to add rows under the row that contains `meta`. It has to be a list of lists, where
  each inner list contains dictionaries with one key-val pair. The
  index of the outer list defines the position of the row, the index of the inner list(s) defines the position inside
  the row.

- Add support for mermaid.js graphs
  - Upstream PR: https://github.com/dbt-labs/dbt-docs/pull/375
  - Upstream issue: https://github.com/dbt-labs/dbt-docs/issues/338
  - Fork PR: https://github.com/PicnicSupermarket/dbt-docs/pull/3

  [mermaid.js](https://mermaid.js.org/) is a Javascript library to
  render diagrams and flowcharts built from plain text.

  By using the syntax ```` ```mermaid```` in any markdown file, dbt
  entities can enhance their catalog page with any mermaid.js diagram.

## Changelog entry example

```
- Add support for foo.
  - Upstream PR: https://github.com/dbt-labs/dbt-docs/pull/x
  - Upstream issue: https://github.com/dbt-labs/dbt-docs/issues/x
  - Fork PR: https://github.com/PicnicSupermarket/dbt-docs/pull/x
  - Fork bugfix: https://github.com/PicnicSupermarket/dbt-docs/pull/y
  - Fork bugfix: https://github.com/PicnicSupermarket/dbt-docs/pull/z

  Description of the feature, and how to use it.
```
