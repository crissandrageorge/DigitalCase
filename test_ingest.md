# Test Ingest for Digital Case

> Test Ingestion conducted on 6.2.23

## Steps

1. Mount the Ingest Server

```
cd\Volumes
cd kelvin\smith\library
```

1. Fill in the Technical Metadata on the Google Sheet
- Column A is the titled parent where the collection will live
- Column B is the titled CModel
- islandora:compoundCModel for compound objects
- islandora:bookCModel for book objects
- islandora:pageCModel for individual pages of a book
- islandora:sp_large_image_cmodel for image objects
- islandora:oralhistoriesCModel for audio/video objects
- ir:citationCModel for scholarly output work
- Column C is the sequence which indicated the ingest order (single page 
objects get 1; multi-page objects get 1 (first page, 2,3,4...)

1. Go to shared Drive under the digitization folder
- "smb://ads.case.edu/ugen/documents/kelvin smith library/digitization."

1. Copy and paste the Google Sheet URL
1. Include the Cell range
1. Click 'Preprocess'
1. Click Preview SUbmitted File
1. Click the circle button as a sample if ingesting multiple things
1. Click Use selected row
1. Go to Templating
1. Go to Twig Template
1. Go to Twig Template input (to make the spreadsheet into MODS record)
1. Save Template
1. Load Existing Template (Digital Collections Mods)
1. Quality Check the output (Check if underscore is not within the column names)
1. CModel Mapping
1. DSID
1. DC, CLick Twig Template Options
1. Mods- Twig Templates
1. OBJ: Obj_file
1. Rest of options are to generate derivatives
1. If no transcript then full_text should not be created
1. Object Properties Map
- Leave top 2 boxes as parent and boxes checked
1. Object Label: User-friendly title that you want to label the object (use Title Information)
1. Sequence and ordering from the spreadsheet
1. Remote DS Sources- "local"
1. Click 'ingest'
1. Click where it says "id=" which will show the PID
1. if ready to ingest then click "Process Set"
1. Start Batch Ingesting
1. Click PID to look at object
> If there is no object then it means there is an error, whether there is not enough space on the server to generate 
derivatives, so then go to datastreams and if there is not the right numbers then you need to clear the ingest server. 
