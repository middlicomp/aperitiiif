---
layout: page
title: '3: Create the batch metadata'
nav_order: 3
parent: Craft a Batch
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-yellow">Contributor</span>

- The user(s) responsible for curating the actual batch data should follow this guide with some guidance from an NYU DSS admin as needed.

## Objective

- Create a CSV spreadsheet of metadata to describe each item in your batch.

## Steps

1.  Create your spreadsheet in your preferred software. (Google sheets or Open Office are recommended; Microsoft Excel is **strongly discouraged.**)
2. Add the first three column headers: `id`, `label`, and `description`. The first is **required** for aperitiiif to work and the second and third are **highly encouraged.**
3. Add a row for each item you created in [the last tutorial](collect-the-batch-images.html) and fill in the `id` column. For the example batch in the last tutorial, this would look like the following:

    | id | label | description |
    |:---|:------|:------------|
    | 001|||
    | 002|||
    | 003|||
    | 004|||
    | 005|||

4. Next fill in the `label` and `description` fields for the items.
5. Lastly, if you have custom metadata that you would like to display in the final IIIF manifests, you can create new columns. To be shown, the header name needs to have the prefix `meta.` For example, to have the IIIF manifests to show "Place of Origin" information, you would add the following:

    | id | label | description | meta.Place of Origin |
    |:---|:------|:------------|:---------------------|
    | 001|||Ogulin, Croatia|
    | 002|||Borilovets, Vidin|
    | 003|||Gomesende, Galicia|
    | 004|||Chai Chumphon, Uttaradit|
    | 005|||Bo Suphan, Suphan Buri|

    {: .note }
    > Every single row ***must*** have a unique `id` that matches a batch item.
    > For every other column (e.g., `description`), a blank field is OK; it just won't show up in the manifest. For this reason, a blank is preferable to something like `N/A`, which will clutter the manifest.

6. When your spreadsheet is complete (it can always be updated later!) save it then export a copy to CSV format.

7. Move the exported CSV into the folder you created in the last tutorial (e.g., `batch_workspace`) and rename it `records.csv`
