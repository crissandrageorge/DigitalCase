# Notes from Video Walkthrough
> Step-by-step guide for ingestion

# Upload to Ingest Server
-  In order to ingest objects, you'll need to upload the corresponding files to the dedicated ingest server. 

** Go to Server and make sure that is mounted**
```
cd /Volumes
cd kelvin\smith\library
```
### After navigating to the rest of the files
```
rsync --progress --chmod=g+rw * batch@ingest.case.edu:/home/batch/
```
** ask repo developer for the password **



# Create a New Collection
1. ingest.case.edu
1. log into VPN
1. Manage
1. Collection
1. Choose content model type
1. Add an object to the collection
1. New Collections = collections, if not, choose the option 
1. Leave "Collection PID" blank which prompts our handle server to create a unique numerical PID.

> XACML policies are how we set permissions on viewing objects. When creating a collection, you can inherit the XACML 
policy from the collection it is nested under. In this case, our new collection is nested under the Kelvin Smith Library collection.

1. In almost all cases, you will check yes to inherit the collection policy and then select the name of the parent collection from the drop down menu. Scenarios where this is not applicable are outlined in the ingest procedures page.
1. This page is a metadata form that maps to a MODS record. Fill out the information you know about the collection according to the collection-level metadata guidelines found here. At the end of the form, click on the "Ingest" button to complete the process.

# Prepare Technical Metadata for Ingest
1. The Electronic Resources Metadata Librarian (ERML) will create a Google spreadsheet filled out with descriptive information about the objects. Using AirTable, they will indicate when that is complete and tag the Digital Collections Manager (DCM) to let them know. The DCM is then responsible for filling out the technical fields in the spreadsheet that connect each object to a file and a location in Digital Case. In the sample image to the right, everything highlighted in purple is part of the technical metadata.

1.  Column A is titled parent and it is where you will specify what collection each object should live in. For individual objects, you will put the PID of the collection. For books or compound objects, you will connect the pages to the parent object by using the row number of the object itself. For example, if row 4 is a book that contains 3 pages, each page will be indicated by an individual row on the spreadsheet with the number 4 listed as its parent. 

1. Column B is titled CModel which stands for "content model." This is where you'll indicate what kind of object each row is. For example, is this a single image, a book, a page of a book, a video, etc. There are many content types available in Islandora, but the following are a list of what we use:
- islandora:compoundCModel for compound objects

- islandora:bookCModel for book objects

- islandora:pageCModel for individual pages of a book

- islandora:sp_large_image_cmodel for image objects

- islandora:oralhistoriesCModel for audio/video objects

- ir:citationCModel for scholarly output work

1. Column C is titled sequence which indicates the ingest order for each object. When working with stand alone objects such as an image, there is only 1 object in the sequence which you'll indicated by entering the number 1 into that row. For multi-page objects such as a front and back of a postcard or multiple pages in a book, the sequence will indicate the order that each page is displayed in. For books, the book itself is 1 and then the first page is also 1 with the following pages listed as 2, 3, 4, etc. 

1. Column D is titled obj_file which indicates the location and file name of the object file associated with each row of data. All files slated for Digital Case should be uploaded to the local ingest server located at "/home/batch/." Following the location you'll put the name of the file and it's file extension. For books and compound objects, you will leave the obj_file blank because that object will be made up of the pages or other objects listed below it.


# Breakdown of Google Drive Folder
- All object files live on a shared drive under the Digitization folder. The path for that folder is as follows: "smb://ads.case.edu/ugen/documents/kelvin smith library/digitization." If you do not have access to that folder, open a UTech help ticket for permissions.
- "Special Collections" : Department Collections -> Special Collections -> DC Ingest -> All files


## Ingestion Procedures

> Demo looks into the process for Patron Request Digitization
> Upload files to server
> Quality control the descriptive metadata
> multi-importer
1. Google URL
* google sheet needs to be shared openly online, so be sure to have the share option open *
1. copy and paste URL
1. Cell range: Object metadata!A1:AE2 [ adjust as need]
1. click Preprocess
1. Preview Submitted File
1. click circle button as a sample if ingesting multiple things
1. Click Use Selected row
1. Go to Templating
1. Go to Twig Template Input (makes spreadsheet into Mods Record)
1. Save Template
1. Load Existing Template (Digital Collections Mods)
1. Quality check into the Output tab to make sure there are no typos and to make sure nothing got lost (check if underscore is not within the column names
1. CModel Mapping
1. DSID (Data stream ID)
1. DC, click "Twig Template Options"
1. Mods- Twig Templates
1. OBJ- "obj_file"
1. Rest of areas, it is generating derivatives
1. if no transcript then Full_text should be don't create
1. Object Properties Mapping
1. leave top two as parent and boxes checked
1. Object Label: User-friendly title that you want to label the object- just use title information
1. Sequence and ordering- form spreadsheet
1. Remote DS Sources- "local"
1. Click "ingest"
1. click where it says "id="
1. shows PID and if it is ready to ingest
1. click "Process Set"
1. Start Batch Ingesting
1. click PID to look at the object

> If you do not see your image, that can mean there is an error. Meaning there is not enough space on the server to generate the derviatives, so go to datastreams. If you do not to see the right numbers, then you need to clear the ingest server. 





### Prerequistes
- airtable will notify that there are projects that are ready to go
- go into google drive and identify the spreadsheet
- Title and to the right is the description metadata
- columns to the left are technical metadata (where it is going and what is it)

> Ingest procedures are partly crafted based on the size of the collection and the capacity of the ingest server. Based on the server capacity, you'll need to determine how much can be ingested at one time. For example, the Cleveland Bystander volumes have a high page number count and therefore only one volume can be ingested at a time. For smaller objects such as images or pamphlets with a low page count, you'll be able to ingest many full objects at one time. For guidance on ingest server capacity, consult with the Repository Developer. 

> Once you've determined the amount of files you'll be ingesting at once, move on to step 3 to locate those files and upload them.

