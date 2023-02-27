---
layout: page
title: '2: Collect the batch images'
nav_order: 2
parent: Craft a collection "batch"
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Role <span class="label label-yellow">Contributor</span>

- The user(s) responsible for curating the actual batch data should follow this guide with some guidance from an NYU DSS admin as needed.

## Objective

- Organize a folder of images into items that can be paired with metadata in the next step.

## Steps

1. Pick your workspace for gathering and organizing your batch images. A new folder on your Desktop would work great. Let's use the example `batch_workspace`.
2. Within your new folder, make another called `data`, e.g., `~/Desktop/batch_workspace/data`.
3. Pause to think about what constitutes an "item" within your batch. In other words, what will get organized into its own IIIF manifest? An item can comprise a single image (like a scanned photograph), or many (like pages in a manuscript).
4. Think about what scheme you'll use to create identifiers for your items. This can be an inherited scheme or a new one, but the simpler the better. When in doubt, you can identify items in order like `0001`, `0002`, `0003`, etc. The important thing is to have a clear idea of why and how identifiers will be applied to items.
5. Start moving your image data into the `data` directory with the following rules:
  - Images need to have one of the following file extensions: `.jpg`, `.jpeg`, `.png`, `.tif`, or `.tiff`.
  - Any single image directly in `data` will be treated as a single-image item. The name of the file (minus the extension) is the item identifier.
  - If you want to make a multi-image item, make a folder within `data` using the id and fill it with the item's images.


## Example

As an example result, the following batch data structure creates 5 items with the following identifiers: `001`, `002`, `003`, `004`, and `005`. `001`, `002`, `004`, and `005` each include 1 image only, whereas item `003` has 3 images that will show up in alphanumeric order.
```
batch_workspace
├── data
│   ├── 001.jpg
│   ├── 002.jpg
│   ├── 003
│   │   ├──001.tif
│   │   ├──002.tif
│   │   └──003.tif
│   ├── 004.png
|   └── 005.jpg

```
