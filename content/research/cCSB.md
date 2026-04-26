+++
title = 'concordant Crop Sequence Boundaries'
date = '2026-04-25T10:16:49-04:00'
keywords = ['agicuture', 'land cover']
+++
The concordant Crop Sequence Boundaries is a field boundary dataset which is an improved version of the Crop Sequence boundaries which relies on the similarity of the crop sequences to merge field fragments together, producing more stable field boundaries through time. 

If you want to try using the dataset, you can download it [here](). I would not suggest its use for areas which have poor crop detection in the Cropland Data Layer, eveywhere else should be fairly ok. I would suggest to use the field boundaries from [Yan and Roy 2016](https://lcluc.umd.edu/metadata/conterminous-united-states-conus-field-extraction) to confirm your results. 

## Weird Fields
The largest field in the dataset is in Flordia and is a large orange operation, which covers several square miles. 

In Central Kanas there are a lot of circle irrigation systems which have different interior and exterior crops. These are just cool to see in the data.   

Areas in southern Georgia which are converting to lodgepole pine production have really odd fields, as the CDLs produce highly fragmented pixel productions, leading to very small fields, which are scattered throughout the landscape. This exemplifies issues with detection in the CDL product and how the manifest in the cCSB. 

Thankfully, there are mostly normal fields across the rest of the dataset. :-)

## Generating Code
The generating code for the dataset is avalible on [github](https://github.com/hsizek/concordant-crop-sequence-boundaries). The code is under a MIT license, but please do share what you do with it!

## Contact me about the dataset
Feel free to contact me about the dataset, whether it is your particular use case, questions about the data quality, or how the dataset is generated. 