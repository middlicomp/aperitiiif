---
layout: page
title: "4: Add batch data to the repository"
nav_order: 4
parent: Craft a collection "batch"
---

# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-yellow">Contributor</span>

- The user(s) responsible for curating the actual batch data should follow this guide with some guidance from an NYU DSS admin as needed.
- They will need write privileges to commit changes to the batch repo.

## Steps

1. Clone the batch repository created in [tutorial 0: Set up the batch repository](set-up-batch-repository.html)

   ```sh
   git clone git@github.com:middlicomp/aperitiiif-batch-CHANGEME.git
   ```

2. In your cloned copy, open the `src` folder and delete the `data` folder and `records.csv` file.

3. Copy the new `data` folder and `records.csv` you created in tutorials [2](collect-the-batch-images.html) and [3](create-batch-metadata.html) into the repository's `src` directory.

   {: .optional }

   > If you have a local Ruby development environment set up, you can test the batch locally at this point before committing the changes. For instructions, see [Using the aperitiiif cli](../admin/use-aperitiiif-cli.html).

4. Add, commit, and push the changes to GitHub

   ```sh
   git add .
   git commit -m 'init batch data'
   git push
   ```
