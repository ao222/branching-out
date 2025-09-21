Need an API key to easily download ACS tables.

### How to get a Census API key:
Go to [https://api.census.gov/data/key_signup.html](https://api.census.gov/data/key_signup.html)
Enter your name and email.
You’ll immediately get an email with your key (a long string).

### Saving Environment Variable aka The API Key
bash (usually Mac or Linux):
export CENSUS_API_KEY="123abc456def789ghi..."
Windows PowerShell:
setx CENSUS_API_KEY "123abc456def789ghi..."

### Joining ACS to CoC Count General Workflow (unproven)
1. HUD CoC Geographies
CoCs (Continuums of Care) are HUD-defined regions used for homeless program reporting (HIC = Housing Inventory Count, PIT = Point-in-Time Count).
A CoC may cover:
A single county (e.g., Harris County, TX → TX-700),
Multiple counties, or
A portion of a city or metro area.
👉 HUD publishes shapefiles for CoC boundaries each year. Example: HUD Exchange GIS Data
.
2. ACS Geographies Available
ACS provides estimates at many levels:
Nation
State
County (FIPS-coded)
Tract / Block Group
Place (incorporated cities)
Metropolitan/Micropolitan Statistical Areas
Public Use Microdata Areas (PUMAs)
3. Recommended Geography for CoC Mapping
Best choice: County-level ACS data
Many CoCs are county-based or aggregations of counties.
County FIPS codes (state + county) can be matched to HUD’s CoC–County crosswalk.
For finer detail: Tract-level ACS data
Needed when CoC boundaries split counties (common in large metros).
Requires spatial join: overlay CoC shapefiles with Census tracts to apportion ACS estimates.
4. Mapping CoCs to ACS GeoIDs
HUD provides a CoC–County Crosswalk (CSV) each year (see HUD Exchange).
Example fields:
COCNUM   CountyName     State   FIPS
TX-700   Harris County  TX      48201
You can use the FIPS code (state+county) to join to ACS GeoID.
In ACS: GEOID is a 5-digit FIPS (2-digit state + 3-digit county).
In HUD crosswalk: FIPS is usually the same.
5. Workflow
Download HUD CoC–County Crosswalk for the year of interest.
Download ACS table(s) (e.g., B01003 for total population) at county level.
GEOID = state+county (5-digit FIPS).
Join ACS data to HUD crosswalk on FIPS code.
Aggregate ACS values by CoC code (COCNUM).
6. Special Cases
In split counties, you must use HUD’s shapefiles + Census tract-level ACS data, then do a spatial join:
Intersect CoC boundaries with Census tracts.
Use area-weighting (or population-weighting, if available) to allocate ACS estimates.
✅ Summary:
Use county-level ACS data if you just want a first-order match (most common).
Use tract-level ACS data + HUD shapefiles for precise mapping where CoCs don’t align to whole counties.

Join is through FIPS code → ACS GEOID.
