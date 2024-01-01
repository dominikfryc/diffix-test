# Contribute

All contributions are extremely valuable to the project! There are many ways to contribute:

- **Improve documentation**: Fix incomplete or missing docs, bad wording, examples or explanations.
- **Give feedback**: Propose new components or features via GitHub Issues.
- **Share the project**: Share link to the docs or GitHub with everyone who might be interested.
- **Give a code review**: Help identify problems with the source code or make it more performant.
- **Contribute to the codebase**: Find an existing issue that you are interested in and work on it!

## Contributing workflow

1. Decide on what you want to contribute.
2. If you would like to implement a new feature, discuss it with the maintainer before jumping into coding.
3. Please make sure to follow commit rules and coding conventions.
4. Run tests and submit a PR once all tests have passed.
5. Get a code review and fix all issues noticed by the maintainer.
6. Your PR is merged. You successfully contributed to the project!

## Commit rules

Please make sure to follow the [Conventional Commits](https://www.conventionalcommits.org/) rules when writing commit messages. This will help us to automate the release flow and generate changelog notes. Commits should follow this mandatory format:

```
<type>(<optional scope>): <subject>
```

Example:

```
feat(button): add loading state
```

Type should be one of the following:

- **build**: Changes that affect the build system or external dependencies.
- **ci**: Changes to our CI configuration files and scripts.
- **docs**: Documentation only changes.
- **feat**: A new feature.
- **fix**: A bug fix.
- **perf**: A code change that improves performance.
- **refactor**: A code change that neither fixes a bug nor adds a feature.
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- **test**: Adding missing tests or correcting existing tests.
- **revert**: Reverts a previous commit.

Scope is optional and should be used when the change affects only a specific component or a part of the project.

The subject contains a short description of the change. Use the imperative, present tense: "change" not "changed" nor "changes", don't capitalize the first letter and don't write dot (.) at the end.

Learn more in [Angular Commit Message Guidelines](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines).

## Coding conventions

The project uses [Prettier](https://prettier.io/) and [ESLint](https://eslint.org/) to enforce coding conventions. Follow the set up rules to make sure that the code is easy to read and consistent with the existing codebase. Please make sure to run `pnpm lint` and `pnpm format` before submitting a PR.

There are some rules for developing new components:

- Web components:
  - Should be prefixed with `dfx-` to avoid collisions with other components.
  - Should document all attributes, events, slots, CSS properties and CSS parts with [TSDoc](https://tsdoc.org/).
  - Custom events should be prefixed with `dfx-` to avoid collisions with other events.
- Custom CSS properties in components:
  - Should be prefixed with `--dfx-component-name`.
  - Should use design tokens instead of hardcoded values.
  - Should set default values in case the design tokens are not available.
- Components should be documented with [Storybook](https://storybook.js.org/).
  - Add a story for each attribute of the component to demonstrate how it works and how it should be used.
  - Add a story to showcase slots usage if the component has any.
- Components should be tested with [Web Test Runner](https://modern-web.dev/docs/test-runner/overview/). Please make sure to add tests at least for the following cases:
  - Test if the component (custom element) is defined.
  - Test if the component renders correctly with default values.
  - Test if the component renders correctly with custom attributes.
  - Test if the component fires defined events correctly.
  - Test if the component passes the accessibility audit.

## Get started locally

- Fork the [repository](https://github.com/dominikfryc/diffix-test), then clone or download your fork.
- Install dependencies with [pnpm](https://pnpm.io/).
- Generate a new component with `pnpm generate component-name`.
- Run the Storybook with `pnpm start`.
- Lint the project with `pnpm lint`.
- Format the project with `pnpm format`.
- Build the project with `pnpm build`.
- Run tests with `pnpm test`.

## Release flow

The project uses [semantic-release](https://semantic-release.gitbook.io/semantic-release/) to automate the release flow. Every commit triggers a release flow based on the branch:

- **main**: Released in `latest` npm channel. Every push to `main` branch makes a stable release.
- **next**: Released in `next` npm channel. Every push to `next` branch makes a preview release.

Semantic release follows semantic versioning rules. When there is a commit that is marked as breaking change in commit message, that push creates a major release in current channel. Backward incompatible changes should have breaking change commits. We'll try to avoid making breaking changes as much as possible. When there are some commits that have feat prefix in the message, that push creates a minor release. And finally, when there are some commits that have fix prefix in the message and not any feat commits, that push creates a patch release.

With every release, new version is published in NPM. Semantic release also automatically creates a GitHub Release with autogenerated changelog including all commits since the last release. We are not pushing changes to `main` and `next` branches directly. `main` branch will only be updated by a PR from `next` branch that contains features/fixes that we are ready to release as stable release. And all of the changes for the current version will be done in PRs targeting `next` branch. PRs are not making any releases.