# Built-Up Areas (2022) FAQ

## Who created the 2022 version of Built-Up Areas?
Ordnance Survey created [OS Open Built Up Areas](https://osdatahub.os.uk/downloads/open/BuiltUpAreas "OS Open Built Up Areas Download Page") with the first version being published in December 2022 under Open Government Licensing (OGL). The Office for National Statistics and Scottish Government made significant contributions in the design of the dataset to ensure it is fit for purpose and focussed on the needs of the wider public sector.

## What is the difference between ‘OS Open Built Up Areas’ and ‘Built-Up Areas (2022)’?
Built-Up Areas (2022) is the name ONS are using for this product. This is to retain consistency with the naming of previous products like this that have been produced roughly every decade since the 1980s. The geometry and associated GSS codes of the two versions are identical. However, the format of the naming is different with ‘Built-Up Areas (2022)’ providing three name columns: BUA22NM, BUA22NMW and BUA22NMG. BUA22NM either contains the English name or the Welsh/Gaelic name where no alternative English name exists. BUA22NMW contains the Welsh name where an alternative English name exists. BUA22NMG contains the Gaelic name where an alternative English name exists. 2022 Built Up Areas also contains a centroid location for each area, provided in British National Grid Eastings and Northings and Latitude and Longitude. 

## Where can I find more information about Built-Up Areas (2022)?
Ordnance Survey’s [product information page]( https://www.ordnancesurvey.co.uk/business-government/products/os-open-built-up-areas "OS Open Built Up Areas Product Information Page") for OS Open Built Up Areas contains further information and their [product support page]( https://www.ordnancesurvey.co.uk/business-government/tools-support/os-open-built-up-areas "OS Open Built Up Areas Product Support Page") contains links to PDFs providing an [overview]( https://www.ordnancesurvey.co.uk/documents/product-support/user-guide/os-open-built-up-areas-overview.pdf "OS Open Built Up Areas Overview PDF") and [technical specification]( https://www.ordnancesurvey.co.uk/documents/product-support/tech-spec/os-open-built-up-areas-technical-specification.pdf "OS Open Built Up Areas Technical Specification PDF") of the product

## Are the 2022 Built-Up Areas the same geography as the 2011 Built-Up Areas?
The 2022 Built-Up Areas were created using a methodology based on the 2011 version. However, there are some notable improvements and changes that mean the 2022 Built Up Areas should be considered a new geography and not a continuation of the 2011 Built-Up Areas or 2011 Built-Up Area Subdivisions. This means statistics produced for areas with the same name are not directly comparable. 
Differences include:
* 2022 Built-Up Areas were created using 25m by 25m cells. The 2011 version used 50m by 50m cells.
* 2022 Built-Up Areas that are 200 metres or less away from each other have not been merged together to form a single area. The 2022 Built-Up Areas are more similar to a layer created from 2011 Built-Up Area Subdivisions and 2011 Built-Up Areas that couldn’t be subdivided.

## Will a ‘merged’ version of 2022 Built Up Areas that joins nearby areas together, like the 2011 Built-Up Areas did, be produced?
Yes. This is planned for 2023 and will be called Built-Up Conglomerations.

## Why do only some 2022 Built-Up Areas have Welsh or Gaelic names?
We have only used the data contained in OS Open Built Up Areas to populate our name fields. If Ordnance Survey do not currently hold a Welsh or Gaelic name in their data used to assign names to areas then we cannot currently include them.

## How are Built-Up Areas (2022) in Scotland different to NRS Scottish Settlements and Localities?
Built-Up Areas in Scotland are not designed to replace [NRS Settlements or Localities](https://www.nrscotland.gov.uk/statistics-and-data/statistics/statistics-by-theme/population/population-estimates/settlements-and-localities "NRS Settlements or Localities webpage"). The methodologies used to create these products are different so are not comparable. NRS have also published a [short paper](https://www.nrscotland.gov.uk/files//statistics/population-estimates/sl-bua-note-nov-22.pdf “NRS Settlements and Localities and OS Open Built Up Areas PDF note to users") that explains the key differences between the two products and suggestions on which product to use in Scotland in certain circumstances. 

## How were centroids for Built-Up Areas (2022) calculated?
Due to some Built-Up Areas having odd shapes, centroid locations calculated in R using the st_centroid and st_point_on_surfance functions in the sf package were deemed inappropriate. This was because centroids either didn’t fall within the area they were meant to represent or because they were placed in locations that could not be considered near the centre of features. As such, a custom method was used. 100,000 random points were generated inside each area. A [convex hull]( https://en.wikipedia.org/wiki/Convex_hull "Convex hull Wikipedia page") was then produced around each area. Whichever of the 100,000 points in an area was furthest away from its convex hull was selected as that areas centroid. For a limited number of areas a further adjustment was done to ensure all centroids would intersect with clipped to the coastline 2022 Local Authority District boundaries.

## How have the GSS codes been assigned to Built-Up Areas (2022)?
Entity codes beginning E63 (England), W45 (Wales) and K08 (Wales/England cross-border) have been assigned unique instance codes based on each areas centroid location. Codes for each entity have been allocated based on their British National Grid Nothing coordinates from North to South. Entity codes beginning S45 (Scotland) have been assigned in ascending alphabetical order. 

## Do any Built-Up Areas (2022) intersect with the English/Scottish border?
No. If they did they would have also been assigned the K08 entity code.

## Does ONS intend to publish their own version of the Built Up Extents and Non Built Up Extents layers available in OS Open Built Up Areas?
OS Open Built Up Areas actually consists of three layers:
* Built Up Areas
* Built Up Extents
* Non Built Up Extents

The ‘Built Up Areas’ layer is the most similar to previous geographies and is what we would consider to the ‘primary’ layer, hence why it has been assigned GSS codes. The other layers do not have separate GSS Codes, instead they have been given ‘Related to GSS Codes’ identifiers in the OS dataset. 

We are exploring how we can best support these layers whilst also adhering to the [GSS Geography Policy](https://analysisfunction.civilservice.gov.uk/policy-store/gss-geography-policy/ "GSS Geography Policy"). In the meantime we suggest you access these layers via the [OS Data Hub](https://osdatahub.os.uk/downloads/open/BuiltUpAreas "OS Open Built Up Areas Download Page") if needed, but if this option does not meet your requirements please e-mail ons.geography@ons.gov.uk and we will do our best to help. 
