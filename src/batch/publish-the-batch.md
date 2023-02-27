---
layout: page
title: "5: Publish the batch!"
nav_order: 5
parent: Craft a collection "batch"
---

# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-green">Admin</span>

- The user following these guides should be an NYU DSS staff member who has access to the batch repo's settings.
- They shouldn't need access to the GitHub organization's settings.

## Steps

1. Make sure GitHub Actions are enabled on the batch repository and trigger the actions to run. You can do this manually in the Actions GUI or by making a small temporary commit (like adding an empty `test.txt` file to the repo.)
2. Make sure the Lint and Deploy actions pass. When the Deploy action is finished, it will have published:

   - the batch images to one AWS S3 bucket
   - the completed IIIF manifests to another S3 bucket, and
   - a small catalog site to the `gh-pages` branch of the repo. (See the [Service Architecture](../about/overview.html#service-architecture))

   {: .note }

   > The secret AWS keys needed for the Deploy action **should already be configured** in the NYU DSS GitHub organization and will be inherited automatically by the batch repo.
   > If the Deploy action shows errors looking for secret environment variables, read the [Manage secrets and env vars ](../admin/manage-secrets-and-vars.html) page to troubleshoot.

3. Enable GitHub Pages on the batch repo with the following settings.

   - Source: `Deploy from branch`
   - Branch: `gh-pages` `/(root)`

4. The step above will trigger a new GitHub Action to publish the catalog site to https://middlicomp.github.io/aperitiiif-batch-CHANGEME (where `CHANGEME` is your new batch namespace)

5. Browse the catalog site to make sure all the IIIF images and manifests are working as expected.

FIN 🎉
