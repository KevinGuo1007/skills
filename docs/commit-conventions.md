# Commit Conventions

Use [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/).
The language, length, types, and scopes below are repository conventions.

## Format and language

```text
<type>[(scope)][!]: <subject>

[optional body]

[optional footers]
```

- Write the subject, body, and descriptive footer text in English. Preserve
  exact identifiers, paths, issue references, and proper names when needed.
- Use a lowercase type and an optional lowercase, hyphenated scope. Separate the
  prefix and subject with a colon and one space.
- Write an imperative subject describing the resulting change, such as `add`,
  `fix`, or `clarify`. Keep the full title at most 72 characters, with no trailing
  period. Avoid vague subjects such as `update files` or `misc changes`.
- Separate the title, body, and footers with blank lines. A small change may use
  only a title. Add a body when the intent, behavior, or scope needs explanation;
  wrap prose around 72 characters, leaving long identifiers and URLs intact.

## Choose the type by effect

| Type | Use for |
| --- | --- |
| `feat` | A new skill or a new capability in an existing skill |
| `fix` | Correcting instructions, resources, or metadata that cause wrong behavior |
| `docs` | Explanatory or contributor documentation without changing skill behavior |
| `refactor` | Reorganizing content or helpers while preserving behavior |
| `test` | Adding or changing validation code or behavioral test cases |
| `build` | Plugin packaging or distribution configuration |
| `ci` | Automated validation or delivery workflows |
| `chore` | Repository maintenance that does not fit the types above |

A `SKILL.md` edit can be `feat` or `fix`: Markdown instructions are the product,
so the file extension does not determine the type. For a cohesive change with
supporting docs or metadata, choose the type of its primary outcome. Use `feat`
for an initial commit that delivers a usable skill collection, rather than
classifying everything as setup work.

## Scope and breaking changes

- Prefer the skill name for one-skill changes, for example
  `fix(feature-development-loop): preserve retry counts across sessions`.
- Use `repo` for collection-wide setup or shared project instructions, and
  `plugin` for packaging. Omit the scope when it would be misleading or redundant.
- Mark an incompatible consumer-facing change with `!` before the colon and
  explain the impact and migration in a `BREAKING CHANGE:` footer. This can
  include a removed invocation name, resource contract, or required behavior.
- Include issue references only when they exist. Add attribution or sign-off
  trailers only when supported by actual contribution or an explicit requirement;
  do not invent trailers or add automatic tool signatures.

## Match the actual commit

- Before drafting, inspect `git status --short`, staged and unstaged diffs, and
  relevant untracked files. Without a previous commit, inspect the new files
  directly rather than assuming `HEAD` exists.
- The message used for an actual commit describes the staged patch. If nothing
  is staged and the user asks for a draft for the current work, describe the
  intended changes and make that scope clear. Drafting does not require staging
  files.
- Keep one coherent outcome per commit. Supporting templates, documentation,
  indexes, and metadata may accompany the skill they deliver; separate unrelated
  work. Before an authorized commit, stage specific intended paths and review
  the resulting staged diff so unrelated user changes are excluded.
- Mention validation only when it was actually performed, with its real scope
  and limitations. A temporary experiment is not a committed test suite.
- A request to write a commit message asks for a draft. Run `git commit`, amend,
  or push only when the user's instruction authorizes that action. Preserve
  existing author and signing configuration.
