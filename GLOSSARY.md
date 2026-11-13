# Domain context

This file defines the shared language for DelGrosso's DG2Go.

## Product terms

**DG2Go**

This repository: the DelGrosso's DG2Go website (dg2gofood.com) and its Sanity Studio, owned by DelGrosso Foods Inc.

**Website**

The public Next.js application in `frontend/`.

**Studio**

The separately deployed Sanity editing application in `studio/`.

**Sanity project**

The hosted Sanity resource for this repository (project ID `egfhtk7k`).

**Dataset**

The named content store inside the Sanity project (`production`).

**Site settings**

Global editable Website identity and content, including the site name, navigation, footer, and contact details.

**Page Builder**

The ordered section editor used to compose a page.

**Section**

One Page Builder unit with a Sanity schema, a GROQ projection, and a React renderer. The Starter ships a minimal section library: Rich Text and Scaffold. Every other section belongs to its own project copy.

**Scaffold**

A placeholder section that holds a page's intended content before a real section exists for it. It has a name, rich text, and a proposed section shape. The Website renders it with a visible internal marker during Building, and the launch check fails while one is published.

**Blocks Archive**

The `blocksArchive` array on a page document. A replaced Scaffold moves here instead of being deleted. The Website never queries or renders it.

**Draft**

Content visible to an authorized editor through preview before publication.

**Published content**

Content available to public Website visitors.

**Redirect**

A permanent route from an old public URL to its current destination.

## Ownership rules

- Code owns layout, rendering rules, validation, and safe fallbacks.
- Sanity owns editor-managed content and site settings.
- This repository owns its Sanity project, dataset, credentials, and hosting.
