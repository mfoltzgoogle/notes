
# Bikeshed Cheat Sheet

This cheat sheet focuses on markup for the spec prose and IDL, not the spec
metadata and boilerplate.

* [GitHub source](https://github.com/tabatkins/bikeshed)
* [Documentation](https://tabatkins.github.io/bikeshed/)

# Commands

Command   | Function
----------|--------------------------------------
`spec`    | Generate `.html` from `.bs`
`watch`   | Regenrate `.html` when `.bs` changes
`update`  | Update bikeshed autolinking data
`refs`    | Search for references known to BS

# Markup / Markdown

Block-level constructs defined by [CommonMark](https://commonmark.org/)

Definition lists:
```text
: key
:: val
: key 1
: key 2
:: more vals
```

Header IDs:
```text
Header 1 {#header1}
========

### Header 2 ### {#header2}
```

Paragraph shortcuts: `Issue:`, `Advisement:`, `Assertion:`, `Note:`, or `Note, `

## Autolinking

Autolinking:
```text
{{IDL-construct}}
[[#spec-section]]
[[BIBLIOGRAPHY-ENTRY]]
|variable|
```

`<l>` allows autolinks to be embedded inside code blocks like `<pre>`.  `<a>`
attributes can be added to the `<l>`.

## Algorithms

`<p algorithm="to foo a bar">` will scope all `<var>` declarations to that block.

## IDL

Surround IDL with `<xmp>...</xmp>` to avoid the need to quote HTML characters.

## Code

Syntax highlighting is enabled on a code block with `highlight="lang"`.

## Issue tracking

Start block with `Issue(number)` to refer to a GitHub issue in the default
repository.

Start with `Issue(user/repo#number)` to refer to any GitHub issue.

# Definitions

Wrap a `<dfn>` around it.  Common English variants (-s, -ed, -ing) are
automatically linked.  Use `lt=` to define the base variant if needed.  Also you
can add variants separated by `|`.

Use `local-lt=` for variants that are scoped to the current spec.

Definitions have a type inferred from context.  You can manually
override the type as a `<dfn>` attribute.

Definitions can have an optional namespace using the `for=` attribute (esp. for
IDL definitions).

You can control the export behavior for definitions through the `export` and
`noexport` attributes.  Can also be applied to containers.

# Autolinking

## Dfn Autolinks

* `[=foo=]` links to `<dfn>` foo.
* `[$foo$]` links to `<dfn abstract-op>` foo.
* `{{foo}}` links to IDL definition foo.
* `[=foo|when foo is done=]` controls the linking text (if it isn't already a
  variant).

## Spec/section Autolinks

* `[[FOO]]` or `[[!FOO]]` links to a non-normative or normative reference.
* `[[#foo]]` links to a local document section by ID.
* `[[FOO#bar]]` links to a section in another spec.

## Manual Autolinks

`<a>` without an `href` creates a manual autolink.

* `lt=` will change the linking text.
* `for=` will specify the definition type.
* `for` alone will force a `dfn` type.
* `spec=` will reference a spec.

Using `spec=` will allow you to link to unexported definitions from other specs.

# Bibilographic entries

Bikeshed will automatically add references to specs in normative sections to the
References section at the end.  If a referenced spec lacks a bibliographic entry
in SpecRef, it can be added manualy in a `<pre class=biblio>` section.








