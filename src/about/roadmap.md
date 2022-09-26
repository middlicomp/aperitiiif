---
layout: page
title: Roadmap
nav_order: 2
parent: About
---

# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 .no_toc }

---
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>
---

## Current & Upcoming

### For v1.0.0
{: .no_toc }

- [ ] Redeploy clean infrax & document
  - [ ] Rebuild S3 buckets from scratch
  - [ ] Redeploy serverless-iiif with overrides from scratch
  - [ ] Create guide for deployments & updates
  - [ ] Look into potential subdirs for image source bucket
  - [ ] Update secrets names & values in template repo and afiles repo
- [ ] Document user workflows, potential collection onboarding policy
  - [x] Create docs site
  - [x] Version MVP template repo
  - [ ] Test template repo it with docs
- [ ] Get feedback
  - [ ] From Bryan
  - [ ] From IIIF
  - [ ] From EdTech
  - [ ] From DSS – discuss grants?
  - [ ] From DLTS
- [ ] Look into supporting IIIF Presentation v3

## Past

### For v0.1.0 <span class="label label-green">Released!</span>
{: .no_toc }

- [x] Deploy [serverless-iiif](https://github.com/samvera-labs/serverless-iiif) to NYU DSS AWS account via SAM CLI
- [x] Configure S3 bucket to hold 'source' images
- [x] Create template repo with [sample images](https://github.com/nyu-dss/aperitiiif-batch-rijks-test/tree/main/src/kasukawa) and workflows.
- [x] Create [aperitiiif gem](https://github.com/nyu-dss/aperitiiif)
  + [x] implement thor cli
  + [x] use rubocop
  + [x] process multi-asset items
  + [x] use parallel gem for multi-thread processing
  + [x] process item-level metadata
  + [x] generate IIIF presentation manifest.json files
  + [x] generate IIIF presentation collection.json file
  + [x] generate index.html listing
  + [x] generate index.json listing
  + [x] write tests!!
  + [x] write command to lint batch, flag issues