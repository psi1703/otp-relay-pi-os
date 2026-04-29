---
title: Help Docs Maintainer Overview
section: Overview
order: 0
slug: overview
wizard: false
---

# Help Docs Maintainer Overview

This page is for maintainers of the OTP Relay portal documentation pipeline.

It is intentionally excluded from the RTA Wizard floating guide, because portal users do not need to see documentation about where markdown, screenshots, or generated files are stored.

## User-facing guide content

Edit the topic pages in this folder:

```bash
docs/help/*.md
```

The build script converts those markdown files into:

```bash
frontend/help/wizard-guide.json
```

The portal loads that generated JSON at runtime for the RTA Wizard floating guide.

## Screenshots and images

Store source screenshots in:

```bash
docs/help/assets/
```

Reference screenshots from markdown like this:

```md
![Description](assets/example.png)
```

The build script copies screenshots to:

```bash
frontend/help/assets/
```

The portal serves them as:

```text
/help/assets/example.png
```

## Generated output

Do not manually edit generated files in:

```bash
frontend/help/
```

That folder is rebuilt by:

```bash
python3 scripts/build_help_docs.py
```

## Excluding maintainer-only pages from the wizard

Use this frontmatter on pages that should remain reference-only:

```yaml
---
wizard: false
---
```

User-facing pages should either use the default mapping in `scripts/build_help_docs.py` or specify explicit wizard steps:

```yaml
---
wizard_steps: [password_reset]
---
```
