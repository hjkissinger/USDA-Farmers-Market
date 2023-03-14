## Changelog for USDA Farmers Market Registrations Post-Pandemic: Transitioning to Online Directories

**Identify and select relevant columns to questions:**<br>
* listing_id
* update_time
* listing_name
* location_address
* location_x
* location_y
* location_site
* location_indoor

**Reformat:**<br>
* Check data type
* Separate Date and time
* Add date columns
* Change data formats
* Separate out location_address into new columns (street, city, state, zip code)


**Export to csv and upload into google sheets (v7):**<br>
* Change Zip code column to string type
* Add conditional formatting to zip_code column: <br>
	=len(Q2:Q1057)<5 <br>
	=len(Q2:Q1057)>5
* Fix any zip code and state NAs or errors. 
* Fix street, city, and coordinate NAs and errors (Word case, missing streets, incorrect cities)
* Remove 2023 data

**Use pivot table in spreadsheets to check unique location sites and standardize them. Below are the groupings made for fm_df_v9:** <br>
Plaza/Square/Common - Arts Walk & Plaza, Back common, Civic Plaza, public lot, donated private land, Veterans Plaza, Welburn Square
Closed-off public street- On I street NW between…, closed off public street
Farm- on a farm from…
Federal/state government building grounds
Local government building grounds
Private business- outdoor basketball court, private business parking lot, business parking lots and courtyards and…, Coffee Creek…
Building- own retail building, co-located with wholesale market facility, Non-profit venue
Park- Cope’s park is a subsection…, public park
Healthcare institution Faith-based institution
Educational institution

**Use conditional formatting to highlight NAs in the location_site and location_indoor. Then look up NAs’ addresses on Google and replace NAs with the appropriate standardized grouping names:** <br>
Closed-off public street, Educational institution, Faith-based institution, farm, federal/state government ground, healthcare institution, local government ground, park, Plaza/Square/Commons, Private business

**Use pivot table in spreadsheets to check unique location sites and standardize them. Below are the groupings made for fm_df_v9:** <br>
Entire time open indoor, no indoor, part time open indoor.

**Use conditional formatting to locate duplicates in the listing id:**<br>
=countif($B$2:$B$1153, B2)>1
If present, remove NAs in listing_id

**Import back into RStudio: fm_df_v9**
