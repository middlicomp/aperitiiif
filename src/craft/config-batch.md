---
layout: page
title: '1: Update batch configuration'
nav_order: 1
parent: Craft a Batch
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-green">Admin</span>

- The user following these guides should be an NYU DSS staff member with who collaborates with the batch contributor to understand the shape and goals of the batch data.
- They will need to use valid YAML Syntax.

## Steps

1. Open the file `config.yml`. It should look something like this:
    ``` yaml
    # batch config

    label:          'Rijksmuseum Demo'
    description:    'Demo collection for aperitiiif service'
    attribution:    'Provided by Rijksmuseum via Wikimedia Commons'

    presentation_api_url: 'https://nyu-dss-serverless-iiif-presentation-test.s3.us-east-1.amazonaws.com'
    image_api_url:        'https://twt4gwyokx4jxgo2tcptgtn4v40qajbb.lambda-url.us-east-1.on.aws/iiif/2'

    records:
      file: 'src/records.csv'
      defaults:
        logo: 'https://upload.wikimedia.org/wikipedia/commons/6/67/Rijks_museum_logo.png'
        source: 'https://commons.wikimedia.org/wiki/Category:Prints_by_Katsukawa_Shunsh%C5%8D_in_the_Rijksmuseum_Amsterdam'
    ```
2. Update the `label`, `description`, and `attribution` fields with the new batch's information. Note: this is for the batch as a whole!
3. Keep `presentation_api_url` and `image_api_url` as is.
4. Keep `records` `file` as is.
5. Update `records` `defaults` to for your batch's needs. This is where you can specify metadata that is the same for every item without cluttering your spreadsheet. A great example is a logo for the institution providing access to the items. You can delete this section if it doesn't apply.
