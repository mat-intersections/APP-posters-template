# APP poster generator for Inter/sections

This is a repository with information on how to automatically generate the posters for the Advanced Placement Projects, because this was very inconsistent and took forever in the first year when it was done manually.

It uses InDesign and is not even a script: it uses a little-known but very handy feature called Data Merge, which allows you to create a template page, feed a CSV file with your data to InDesign, and it will generate each page for you using the data. This method has many advantages:
- consistency (not everybody has to do their own poster from a template, which invariably results in people shifting or resizing things or computers having font issues)
- maintainability: just update something in the template, and the change is reflected in all the outputs
- it's significantly more time-efficient (and time is certainly a precious resource for everyone towards the end of the APP)

## Prerequisites

- InDesign CS6+
- Excel, LibreOffice, Google Spreadsheet, or anything that can deal with CSVs
- the fonts [Montserrat](https://www.fontsquirrel.com/fonts/montserrat) and [Office Code Pro](https://github.com/nathco/Office-Code-Pro/releases) installed on your computer

Only one person needs to generate all the posters of course, so not everyone doing the placement need these.

## Instructions

One person must gather all the data from everyone about their placement project. Doing this with a Google Forms might be more efficient than dealing with emails, because then you can get answers as a CSV and copy-paste them into the template.

Open **projects.csv** with Excel or LibreOffice, updating all the data as needed. Save as a CSV file, making sure you set values to be in quotes. If InDesign still chokes on it for some reason, try TSV/tab delimited.

All images must be placed in the images/ folder and the path in the column called **@Picture** must start with **./images/** so that InDesign recognise they are in a path relative to the template. There is no sanity check on images so please make sure that they are fit for print (adjusted for CMYK if they're bright, and at least 2150px wide for printing it on A3 @ 180dpi).  
*(Note about the @Picture header field: it MUST start with an @ to indicate an image, if you modify it by mistake you have to type a single quote ' before the @ otherwise Excel will treat it as a formula and give you an error.)*


In InDesign, open **template.idml**. Go to **Window > Utilities > Data Merge**, and in the menu of the panel (the tiny three-line icon at the right of the tabs), choose Select Data Source and pick the CSV again (or **Update Data Source**, if available). Click Preview and you should see the first row working. If it doesn't work copy and drag the placeholders again.

**When updating the template** please always save as IDML not INDD, this will avoid many future bugs between InDesign versions and it plays a bit nicer with source control.  
Note that when you open an IDML in newer versions of InDesign it opens it as a template (ie creates an Untitled copy) so you have to make sure you overwrite/save when needed.


### Template status

As of now the template provided is just a starting point with placeholders and the fonts. Please update this README when you update the template with:

- [ ] correct Inter/sections colours
- [ ] sponsors logos
- [ ] improved layout

## Exporting

When you're done adjusting the template, in the Data Merge menu choose Create Merged Document. Options should be left as default. It will create a new document where every page is a poster. Ta-da! Review all the pages to make sure there is no overset text and to adjust the cropping of images, and you should be done. Export as print quality PDF (cmd-E) — note that there is 3mm of bleed in the template provided and you have to manually check the Bleed option, and crop marks, in the Export panel.

If you have questions or issues you can't resolve you can still email me: <io@victorloux.uk>

## More info

This is an old but good tutorial if you need more out of Data Merge: [The Indesigner #43](http://www.theindesigner.com/podcasts/tid43_theindesigner_43.mp4)
