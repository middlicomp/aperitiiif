---
layout: page
title: Overview
nav_order: 1
parent: Project
---
# Project Overview <span class="label label-purple">Work in Progress!</span>
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

## Abstract


## Architecture

[![diagram]({{ '/media/aperitiiif.jpg' | absolute_url }})]({{ '/media/aperitiiif.pdf' | absolute_url }})

1. Canonical Metadata and Image Data  
a. GitHub Repo

2. IIIF Image API  
a. [serverless-iiif](https://github.com/samvera-labs/serverless-iiif) implementation    
b. Source image S3 bucket  
c. GitHub Action uses [aperitiiif gem](https://github.com/nyu-dss/aperitiiif) to process images, syncs them to S3 source bucket

3. IIIF Presentation API  
a. S3 bucket for published json  
b. GitHub Action uses [aperitiiif gem](https://github.com/nyu-dss/aperitiiif) to generate IIIF Presentation API resources, syncs them to S3 presentation bucket

4. Discovery  
a. Github Action uses [aperitiiif gem](https://github.com/nyu-dss/aperitiiif) to generate 2 indices of resources produced (`index.html` for humans, `index.json` for machines), publishes them to Github Pages

## Workflow

**Setup** (GitHub)
1. Admin creates repo for new collection using `aperitiiif-batch-template` named `aperitiiif-batch-collectionname` where `collectionname` will be the namespace used for resources generated.
2. Admin adds S3 secrets to the repo enviroment.
3. Admin enables Actions and GitHub pages on the repo.
4. Admin gives curator(s) write access to the repo. They can add images and metadata but cannot access settings or secrets.  

**Ingest (GitHub)**  
1. Curator adds images to `src/data` directory (multipart object structure TBD) and metadata via CSV file to `src/metadata`.
2. Curator adds metadata defaults as needed to the `config.yml` file
3. When committed to the `main` branch, a GitHub Action will convert images to tif, namespace them by prepending the collection name and any subfolder names, and sync them to the S3 source image bucket.
4. It will also use the [O'Sullivan gem](https://github.com/iiif-prezi/osullivan) to generate Presentation API JSON resources (e.g., manifests, canvases, etc.) and sync them to the S3 presentation bucket.
5. Lastly, it will also create listings of resources published (html and json) and deploy them to GitHub pages.

**Publish (AWS)**
1. The Presentation API resources that have been synced are done and ready. There is no additional work for AWS to do.
2. The images synced to the S3 source image bucket are now accessible by the serverless-iiif lambda policy. Requests that hit the IIIF Image API lambdas (via Cloudfront) trigger derivative builds to an S3 cache bucket.
