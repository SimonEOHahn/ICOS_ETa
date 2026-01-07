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

Map of Stations:
<img width="582" height="620" alt="image" src="https://github.com/user-attachments/assets/c2f8985d-5bac-4b08-8422-918fd41e80d3" />

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

Data structure of important Variables:
| Variable  | Description | Unit |
| ------------- | ------------- | ------------- |
| TIMESTAMP_START  | ISO timestamp start of averaging period  | YYYYMMDDHHMM  |
| TIMESTAMP_END  | ISO timestamp end of averaging period  | YYYYMMDDHHMM  |
| H_CORR  | Sensible heat flux  | W m-2  |
| LE_CORR  | Latent heat flux  | W m-2  |
| TA_F  | Air temperature  | deg C  |
| WD  | Wind direction  | Decimal degrees  |
| WS  | Wind speed  | m s-1  |


# 3) NASA ECOSTRESS 
Data description: 
Evapotranspiration (ET) is one of the main science outputs from the ECOsystem Spaceborne 
Thermal Radiometer Experiment on Space Station (ECOSTRESS) mission (Fisher et al., 2020). 
ET is a Level-3 (L-3) product constructed from a combination of the ECOSTRESS Level-2 (L-2) 
Land Surface Temperature (LST) product (Hulley et al., 2022) and ancillary data sources. The 
rate of ET is controlled by many environmental and biological controls including: incoming 
radiation, the atmospheric water vapor deficit, soil water availability, and vegetation physiology 
and phenology (Brutsaert, 1982; Monteith, 1965; Penman, 1948). Therefore, to accurately model 
ET, it remains important to consider these variables. 

# 4) LE to ETa Conversion Method
Method description:
Evapotranspiration (ET) can be calculated from latent heat (LE) by dividing by latent heat of vaporization (λ): ET=LE/λ
Latent heat of vaporization varies slightly with temperature, but is often set to 2.45 MJ kg-1 which is the value for an air temperature of 20 °C. Allen et al. (1998) also provides an equation for calculating λ with air temperature variation, see Annex 3 equation 3-1: λ=2.501−(2.361×10−3)×Ta

In R, this was implemented using following code: 
latent_heat_vaporization <- function(temp) {
  2.501e6 - 2370 * temp
lambda = latent_heat_vaporization(TA_F),
ETa = (LE_CORR / lambda) * 86400  # mm/day

Note: DE-Brs and DE-GsB use LE_F_MDS instead of LE_CORR, as LE_CORR (corrected LE_F_MDS) is not present in their dataset. 


References: Allen et al. (1998) https://www.fao.org/4/x0490e/x0490e00.htm
