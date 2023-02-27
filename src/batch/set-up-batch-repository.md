---
layout: page
title: "0: Set up the batch repository"
nav_order: 0
parent: Craft a collection "batch"
---

# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-green">Admin</span>

- The user following these initial setup steps **must** have user permissions to create a new repository in the [nyu-dss](https://github.com/nyu-dss) GitHub organization.
- They also **should** have access to repository settings.

## Steps

1. Go to the <a href="https://github.com/middlicomp/aperitiiif-batch-template" target="_blank">middlicomp/aperitiiif-batch-template</a> and click "Use this template."

2. Follow the instructions on GitHub to make the new repository with these settings:

- [ ] The **owner** must be `nyu-dss`
- [ ] The **repository name** must be `aperitiiif-batch-CHANGEME`, where `CHANGEME` will serve as the unique namespace for the entire batch. Choose wisely!
- [ ] The repository must be **Public**

3. When the new repository has been created

- [ ] Delete the `README.md` file
- [ ] Rename the `README-template.md` to `README.md`
- [ ] Change all of the instances of `CHANGEME` in the new `README.md` file to the batch namespace you chose in step 2.
- [ ] Fill out the remaining info in the new `README.md`

4. Add the batch contributors (if applicable) as GitHub contributors to the repository. They will need write access but **do not** need admin access to any repo settings.
