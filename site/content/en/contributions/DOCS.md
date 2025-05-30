---
title: "Working on Envoy Gateway Docs"
description: "This section tells the development of
 Envoy Gateway Documents."
---

The documentation for the Envoy Gateway lives in the `site/content/en` directory.
Any individual document can be written using [Markdown].

## Documentation Structure

We supported the versioned Docs now, the directory name under docs represents
the version of docs. The root of the latest site is in `site/content/en/latest`.
This is probably where to start if you're trying to understand how things fit together.

Note that the new contents should be added to `site/content/en/latest` and will be cut off at
the next release. The contents under `site/content/en/v0.5.0` are auto-generated,
and usually do not need to make changes to them, unless if you find the current release pages have
some incorrect contents. If so, you should send a PR to update contents both of `site/content/en/latest`
and `site/content/en/v0.5.0`.

You can access the website which represents the current release in default,
and you can access the website which contains the latest version changes in
[Here][latest-website] or at the footer of the pages.

## Documentation Workflow

If you are creating procedural or conceptual documentation, please use our provided templates. You can generate these templates by running the following commands in the site directory:

### New Task Documentation

To create a new task document, use the following command:

```bash
hugo new --kind task content/en/latest/tasks/your-category/your-new-task.md
```

Replace `your-category`, `your-new-task` with the appropriate names.

### New Conceptual Documentation

To create a new conceptual document, use the following command:

```bash
hugo new --kind concept content/en/latest/concepts/your-new-concept.md
```

Replace `your-new-concept` with the appropriate name for your documentation. 

{{% alert title="Note" color="primary" %}}
When adding new documentation, please make sure it is included in both the `site/content/en/latest` directory and the `site/content/en/v#.#` directory (where v#.# is the highest version number) to ensure consistency across current and versioned docs.
{{% /alert %}}

### Editing Existing Docs

To work with the docs, just edit Markdown files in `site/content/en/latest`

### Previewing and Releasing the Docs
Use the following commands to build, preview, and optionally version the Envoy Gateway documentation:

Generate the static site files under site/public:

```bash
make docs
```

Preview the site locally by running:

``` shell
make docs-serve
```

If you want to generate a new release version of the docs, like `v0.6.0`, then run

```bash
make docs-release TAG=v0.6.0
```

This will update the VERSION file at the project root, which records current release version,
and it will be used in the pages version context and binary version output. Also, this will generate
new dir `site/content/en/v0.6.0`, which contains docs at v0.6.0，like `/api`, `/install` and etc.

## Publishing Docs

Whenever docs are pushed to `main`, CI will publish the built docs to GitHub
Pages. For more details, see `.github/workflows/docs.yaml`.

## Reference

Go to [Hugo](https://gohugo.io) and [Docsy](https://www.docsy.dev/docs) to learn more.

[Markdown]: https://daringfireball.net/projects/markdown/syntax
[latest-website]: /latest
