Evapotranspiration Reference Processing

# 1) List of Stations
# Cropland
- DE-Brs: https://meta.icos-cp.eu/resources/stations/ES_DE-Brs
- DE-Geb: https://meta.icos-cp.eu/resources/stations/ES_DE-Geb
- DE-Kli: https://meta.icos-cp.eu/resources/stations/ES_DE-Kli
- DE-RuS: https://meta.icos-cp.eu/resources/stations/ES_DE-RuS
# Grassland 
- DE-Gri: https://meta.icos-cp.eu/resources/stations/ES_DE-Gri
- DE-GsB: https://meta.icos-cp.eu/resources/stations/ES_DE-GsB
- DE-RuR: https://meta.icos-cp.eu/resources/stations/ES_DE-RuR

Map of Stations: <img width="582" height="620" alt="image" src="https://github.com/user-attachments/assets/c2f8985d-5bac-4b08-8422-918fd41e80d3" />


# 2) ICOS Flux Tower Network
Description: 
The Integrated Carbon Observation System, ICOS, provides standardised and open data from close to 180 measurement stations across 16 European countries. The stations observe greenhouse gas concentrations in the atmosphere as well as carbon fluxes between the atmosphere, the land surface and the oceans. Thus, ICOS is rooted in three domains: Atmosphere, Ecosystem and Ocean.

The ICOS community consists of more than 500 scientists in both its current Member and Observer countries and beyond. More than 80 renowned universities or institutes are a part of the ICOS community. The ICOS community has strong connections to colleagues and operators outside ICOS. ICOS-based knowledge supports policy- and decision-making to combat climate change and its impacts.

Data structure: 
half-hourly standard FLUXNET product including gap-filled NEE, GPP,
RECO and all the related variables and uncertainty and gap-filled version of selected
meteorological variables. Data are processed by the ICOS ETC starting from the
FLUXES and METEO data files using the ONEFlux pipeline. The code used is available
through the ICOS ETC GitHub repository and processing described in Pastorello et al.
2020 (Scientific Data) https://doi.org/10.1038/s41597-020-0534-3

Data structure:
| First Header  | Second Header | Third Header |
| ------------- | ------------- | ------------- |
| TIMESTAMP_START  | Content Cell  | Content Cell  |
| TIMESTAMP_END  | Content Cell  | Content Cell  |
| H_CORR  | Sensible heat flux  | W m-2  |
| LE_CORR  | Latent heat flux  | W m-2  |
| TA_F  | Air temperature  | deg C  |
| WD  | Wind direction  | Decimal degrees  |
| WS  | Wind speed  | m s-1  |


# 3) NASA ECOSTRESS 
Data description:

# 4) LE to ETa Conversion Method
Method description:
References: 
Code example: 
