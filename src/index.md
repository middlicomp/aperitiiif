---
layout: home
title: About
nav_order: 1
has_children: true
---

# Aperitiiif 🥂 <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

Craft batch publishing with serverless IIIF for digital research and scholarship.
{: .fs-6 .fw-300 }

Aperitiiif is a workflow and set of components for batch publishing [IIIF](https://iiif.io)-compliant image collections. It addresses the needs of research and scholarly collections—needs often distinct from collections formally acquired and stewarded by research institutions.

Aperitiiif leverages a multi-tenant [serverless-iiif](https://github.com/samvera-labs/serverless-iiif) implementation on AWS. "Batches" (i.e.,  discrete research collections) are managed via GitHub repos. GitHub handles all of the scoped user auth,  GitHub Actions workflows create the IIIF manifests and deploy the generated resources to AWS, and GitHub Pages hosts an automated catalog site to present items for reuse. This architecture enables flexible user contributions with lower overhead for financial cost and technical maintenance.

[![diagram]({{ '/media/aperitiiif.jpg' | absolute_url }})]({{ '/media/aperitiiif.pdf' | absolute_url }})
