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

One reusable Page Builder content and layout unit.

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
