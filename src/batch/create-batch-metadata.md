---
layout: page
title: '3: Create the batch metadata'
nav_order: 3
parent: Craft a collection "batch"
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-yellow">Contributor</span>

- The user(s) responsible for curating the actual batch data should follow this guide with some guidance from an NYU DSS admin as needed.

## Objective

- Create a CSV spreadsheet of metadata to describe each item in your batch.

## Steps

1.  Create your spreadsheet in your preferred software.

    {: .note }
    > Google Sheets or Open Office are recommended. Microsoft Excel is **strongly discouraged** because it uses a fickle ANSI encoding scheme that hides line break characters and often garbles spreadsheet data. Take our word for it (no pun intended) and avoid Microsoft Office for this work!

2. Add the first three column headers: `id`, `label`, and `description`. The first is **required** for aperitiiif to work and the second and third are **highly encouraged.**
3. Add a row for each ***item*** you created in [the last tutorial](collect-the-batch-images.html) and fill in the `id` column. For the example batch in the last tutorial, this would look like the following:

    | id | label | description |
    |:---|:------|:------------|
    | 001|My first label|Description for my first item...|
    | 002|My second label|Description for my second item...|
    | 003|My third label|Description for my third item...|
    | 004|My fourth label|Description for my fourth item...|
    | 005|My fifth label|Description for my fifth item...|

      {: .note }
      > If your item has multiple files, they will be automatically loaded as long as you followed the instructions in [2: Collect the batch images](collect-the-batch-images.html). The metadata in each row should refer to the entire item; Aperitiiif does not currently support asset-level metadata (e.g., labels for each page in a book item.)

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

6. When your spreadsheet is complete (it can always be updated later!) save it then export a copy to CSV format using UTF-8 encoding.

7. Move the exported CSV into the folder you created in the last tutorial (e.g., `batch_workspace`) and rename it `records.csv`
