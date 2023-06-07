To update data of a given entity type, a unique identifier is required to identify the record to be altered upon update. Best choice is to use the numeric `_system_object_id` of EasyDB (other options are `_id` or `_uuid`m, depending on the use case). 

The examples below describe the load process of issue https://github.com/gtadigital/experimentaldesign-datacuration/issues/29 

Then, create/organise your data as .csv file and check the integrity of the data (same number of columns in every row, no data noise in the file, empty lines and line breaks within the row are allowed but not recommended). Make sure the table starts with the `_system_object_id` in the first column and label the columns according to their content. 

![Bildschirmfoto 2023-06-07 um 16 29 17](https://github.com/gtadigital/cms-datacuration/assets/30504518/89ac3b22-bf35-4a99-a4e0-c962e5f17a5a)

### Step 1 Open CSV Importer
Log into the CMS and navigate to the entity type you wish to import, in our case [Œuvres](https://collections.gta.arch.ethz.ch/lists/oeu), Open the CSV Importer: 


### Step 2 Import Setting
Next, add the basic settings to the import process: 
![Bildschirmfoto 2023-06-07 um 16 43 41](https://github.com/gtadigital/cms-datacuration/assets/30504518/b258f62e-eb47-4cd1-beef-18e0b2fedc5a)

* CSV file `ed-cd-29-loadfile-isler-appellation-english.csv` (locate the loadfile)
* CSV field names `1. row` (choose row with column header)
* Target field name `None` (working with Target fieldnames is not recommended)
* Object type* `_Œuvres, Built Works, Projects` (choose the Entity Type you want to import)
* Pool* `gta Archives` (choose the Pool you want the records to be imported)
* Mask* `Generic \Œuvres` (choose the data mask, this choice depends on the pool)
* Tags mode `Add Tags` (or choose `Replace Tags` if needed)

* Pool for linked records* `gta Archives`(required even if no links are imported)
* Comment `data curation experimental design / loading English œuvres appellation / v2 [ed-dc-29, th]` (will appear in the change log of each records, should be standardised and contain reference to the issue in question)

### Step 3 Field Mapping
Next, map the columns of the loadfile to the corresponding fields in the data base. In our example: 
* `_system_object_id` => `_system_object_id`
* `oeu_nc_name_english` => `oeu_nc_name` ==> `en-US`  

<img width="1811" alt="Bildschirmfoto 2023-06-07 um 18 16 06" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/5a49ad70-9fba-4765-95e2-d70f23ff1561">

### IMPORTANT: Step 4 Setting Update Field
To make sure, data are not being imported/added but updated, switch back to `Import Settings` and select: 
* `Update field` => `_system_object_id`

<img width="1828" alt="Bildschirmfoto 2023-06-07 um 20 25 26" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/1ba552d9-b624-49c4-b04b-bba6054a10ef">

### Step 5 Preflight
Run `Prepare...` at the bottom right of the CSV-Importer window to run a preflight for the import.
 
The Status section (bottom left of the CSV-Importer window) will display statistics on the preflight. If the data are consistent, the count of `Row` (available) will equal the count of `Ready`. If not, check your data. 

Also, this is the moment to verify that the records are currently being updated and not inserted. 

<img width="1828" alt="Bildschirmfoto 2023-06-07 um 20 37 14" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/1dd668e4-a0f7-4187-a8f1-232d46e2340c">

### Step 6 Data Update
Run `Update`. In case you have both records to be updated and inserted, the button will adjust accordingly.
Important to verify the number of updated/inserted records. 
   
<img width="1828" alt="Bildschirmfoto 2023-06-07 um 21 10 21" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/738b9e85-8f88-4996-a8cd-75b3d6b08320">

The Importer will show progress (number of loaded records or lines vs. number lines to load until completion). 

**Important: do not close the window until completion**
<img width="1828" alt="Bildschirmfoto 2023-06-07 um 21 10 50" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/bed36f0b-f75d-495b-887c-e7262adc2b5e">


### Step 7 Protocol
After completion, a window will allow downloading a protocol, that consists of the loadfile, annotated with statuses. It is absolutely crucial to download this protocol and store it alongside the loadfile. 

In addition, the status will be updated in the status panel. Check that all records are being updated before you close the importer window (status overview will be lost and must be extracted from protocol file)
<img width="1828" alt="Bildschirmfoto 2023-06-07 um 21 12 18" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/0c36b2cc-87ed-4332-80f8-094ff9d54648">

### Step 8 Verify Import
For forensic reasons, it is advised to run a search and verify the number of updated records in the front end (query by used and date range in the changelog).  

<img width="1842" alt="Bildschirmfoto 2023-06-07 um 21 21 33" src="https://github.com/gtadigital/cms-datacuration/assets/30504518/53b7e2c9-8a1c-47de-9148-10cd5a142d5f">

