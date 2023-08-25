??? quote "What is SDMX?"
	SDMX, which stands for Statistical Data and Metadata eXchange is an international initiative that aims at standardizing and modernizing (“industrializing”) the mechanisms and processes for the exchange of statistical data and metadata among international organizations and their member countries.

	Simply, SDMX is a new technology that simplifies the transmission of statistical data. SDMX is a standard and technology to style and transmit data using machine-to-machine language. It is a:

	- Logical model to describe and structure content
	- Standard for automatic communication
	- Technology supporting standardization

### SDMX at STC
Currently, Census Profile information is available at all geography levels via an SDMX API.  This providers a modern, streamlines method of connecting to Statistic's Canada Census data.
  
In the near future, all CODAR products will be available via an SDMX API.  A small example is included below.

<b> [Learn more about the 2021 Census Profile SMDX API](https://www12.statcan.gc.ca/wds-sdw/2021profile-profil2021-eng.cfm) </b>

<br>

>NOTE:
>This feature is still under exploration. As GAE continues to explore and learn about SDMX, we are excited about the possibilities it offers to improve our ability to derive insights from data.

### API Example
``` py title="STC Census Profile SDMX Python API"

import pandas as pd
import pandasdmx as sdmx
info = {
  "id": "STC_CP",
  "url": "https://api.statcan.gc.ca/census-recensement/profile/sdmx/rest",
  "name": "STC Census Profiles"
}
sdmx.add_source(info, id=None, override=True)
stc = sdmx.Request('STC_CP')
resp = stc.data('df_pr')
#df_pr- Canada, provinces and territories dataflow
data = resp.to_pandas()
#returns a series with a multi-index, "2-d series; 3-d data frame"
data

```
The code above returns this multi-index data frame:
![sdmx_frame](images/knowledge/sdmx_out.PNG)
After conditioning of the *Ref_Area* column, you can then join it to a spatial data frame or geography layer.


|Dataflow code||Name of Dataflow|
|---||---|
|DF_PR *||Canada, provinces and territories <br> *used in example above*|
|DF_ADA||aggregate dissemination area|
|DF_CD||census divisions|
|DF_CMACA||census metropolitan areas and census agglomerations|
|DF_CSD||census subdivisions (municipalities)|
|DF_CT||census tracts|
|DF_DA||dissemination areas|
|DF_DPL||designated places|
|DF_ER||economic regions|
|DF_FED||federal electoral districts (2013 Representation Order)|
|DF_POPCNTR||population centres|



<b> [SDMX API CHEAT SHEET](https://github.com/sdmx-twg/sdmx-rest) : The SDMX Technical Working Group has also published a two-page cheat sheet (PDF, 83 KB) that summarizes the main points of the SDMX 2.1 RESTful API. </b>