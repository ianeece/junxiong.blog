---
lang: en
slug: hpc-ee-gcs-pipeline
title: A Pipeline with HPC, EE and GCS
date: 2017-05-08
tags: EarthEngine
---
<!-- more -->
![](http://oouh9u8nz.bkt.gdipper.com//hpc-ee-gcs-pipeline.jpg)

Today I plan to do some updates to the [Global Croplands @ 30m](https://croplands.org/app/map?lat=0&lng=0&zoom=2)

I need to do some merging of segmentation and classification. It is not a super complex thing to do just a few steps on different platform:

1. Export segmentation results as well as classification on Earthengine  to GCS;
1. Fetch exported tiles from GCS into HPC, and merge on HPC (Pleiades) with CPP program;
1. Upload the merged results back to GCS;
1. Finalized the merged results in Earthengine.


# Export segmentation with classification overlay

[Google Cloud Storage](https://console.cloud.google.com/storage/browser/junwork/?project=thinking-star-140602)

I’ve worked on [NASA Pleiades](https://www.nas.nasa.gov/hecc/resources/pleiades.html) for more than six years. 

```bash
gsutil -m cp -r gs://junwork/uganda/* .
```

earthengine create collection users/JunXiong1981/cropextent/uganda
