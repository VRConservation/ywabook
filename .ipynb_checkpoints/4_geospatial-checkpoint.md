# Geospatial
A geospatial analysis of communities and infrastructure at risk in Yuba County.

## Takeaways
1. The **Yuba County communities** most at risk from wildfire are in the Northeast portion of the county. Approximately in risk order, they are Brownsville, Dobbins, and Camptonville. However, Brownsville and Camptonville carry more difficulty for egress during a wildfire event, likely due to being more remote than Dobbins. **TRUE?**
2. Our analysis of **water infrastructure** at risk showed nuanced results dependent on location. The upper and lower watershed at New Bullards Bar has a higher risk than the middle. Riparian areas are generally at high risk. The area to the southeast of Collins Lake is at higher risk, but much surrounding the lake is at low risk. The land surrounding Lake Francis is at low risk, but much of the land to the east of the lake is at high risk. Englebright Dam and surrounding riparian areas are at high risk.
3. Downscaled, updated, or created datasets such as climate change data, forest conditions, and road conditions would make the 
risk analyses more accurately.

## Overview
Agency and business focus on forest health and treatment is a recognized priority of California. Workforce and business development are key parts of the state’s efforts toward improving forest health, largely to reduce wildfire risk and damage. This report focuses on Yuba County as a case study in statewide efforts to reestablish a forest-focused industry, treat forests, and address wildfire risk to communities, the infrastructure they rely on, and surrounding forests. 

Like many counties in the Sierra Nevada foothills, Yuba County spreads across the valley up into the foothills ({numref}`location`). The vegetation cover and topography change dramatically, from level grasslands in the west County to steep, forested slopes in the east County. The county’s water infrastructure and communities are spread across this varying landscape. Yuba County’s forested areas have small, remote communities. Often bordering public lands, these communities are the most densely vegetated and spread from community centers into the wildland-urban interface.

```{figure} /figures/location.png
:height: 600px
:name: location
Yuba County's location in California shows generalized vegetation categories.
```

Like many forests across California, forests in Yuba County over the past 30 years experienced a management shift away from timber production. The result is more densely vegetated areas at risk for forest fires. While areas surrounding Yuba County have seen catastrophic fires covering large geographic regions in the last decade, Yuba County has experienced smaller-scale fires. Mitigation for more damaging wildfires is a priority for the County, communities, Fire Safe Council, and Yuba County Water Agency. 

An analysis of Landsat 8 imagery shows this striking difference in areas affected by fires from March 2019 to March 2023. We examined changes in the forest canopy in the landscapes surrounding Camptonville in Yuba County and Greenville in Plumas County. Further analysis of the same region and period using Sentinel radar imagery found a difference of 7.5 km<sup>2</sup> affected by fire in the Camptonville area of interest and a difference of 1,047 km<sup>2</sup> surrounding Greenville ({numref}`change`).

```{figure} /figures/change.png
:height: 500px
:name: change
Radar change detection analysis from Landsat 8 imagery between 2019-24. Imagery and analysis courtesy of USGS and Google Earth Engine.
```

Water and electrical infrastructure are established among the foothills, serving the communities in East County and the more populated communities in West County. Roadways (type and responsibility for maintenance) are important for access, what is treated, and who is responsible for treatment. Local officials, agencies, and communities want to improve forest conditions, yet they face barriers. In Yuba County, some barriers were identified at a Fire Safe Council community meeting on October 9, 2024. 

We wanted to visually represent risk, treatability, responsibility, partnership, and priority. These questions led us to who and what is at risk and what their risk level is. 

For the radar analysis, we used Sentinel-1 data, with images from March 2019 and March 2024, a five-year difference. The backscatter was set to -0.15 and polarization to vertical horizontal, sometimes called VH. The VH and backscatter settings do a better job of capturing tree canopy change. Radar can capture imagery through clouds and smoke and gives a good measure of surface roughness or detect where trees used to be when comparing images. 

## Questions
To conduct the study, we aimed to address the following questions:

- What is at risk? And what is their level of risk? 
- Who is at risk? And what is their level of risk? 
- Who is responsible for addressing that risk? 
- If not responsible, where are their opportunities to work together to address risk? 
- What are some options to address these risks? (Options for treatment) 
- What are some barriers to treating these risks? (e.g., lack of downscaled data or funding to mitigate risk) 
- What is missing to address risk? (e.g., programs, funding, workforce, access, capacity, and data.) 

## Methods
We created three models based on available raster and vector data sets. The datasets were weighted in each circumstance according to the importance and impact on the community, infrastructure, or natural resources. We tended to use the suitability modeler tool in ArcGIS Pro since it easily uploaded the raster datasets, weighted them, and then combined them into a single model. Each model output could create a report showing the datasets, weighting, and visual representation of the workflow. The only downside of using the suitability modeler is that it tended to crash the software when large datasets were large. To address this issue, we clipped each dataset to a smaller area of interest (AOI) in the Yuba County region.

In general, the workflow for the geospatial analysis was

1. Download or link rest services for the datasets. 
2. Clip the dataset to the AOI
3. Upload the datasets to the model
4. Weight and transform each dataset
5. Run the model combining each weighted dataset
6. Perform additional analysis as needed, e.g., zonal statistics

Most datasets were downloaded from the Sierra Nevada Regional Resource Kit, others came from FRAP and national level datasets {cite}`resourcekit` or the US Census Bureau {cite:p}`census`. Generally, the risk for any analyses increased when moving from lower to higher elevations and agricultural to forested systems. This is unsurprising since we relied on datasets that focused on fire and forest. Still, it is not great for the communities in the extreme northeast of the county, such as Camptonville, Dobbins, and Brownsville. Other datasets are cited in each section or within each figure below in the text.

## Egress Risk
The egress risk analysis did not work well with the suitability modeler tool, so we weighted and added the rasters using Python and a Jupyter Notebook. The rasters and percent weighting were as follows:

- Distance to cell tower (20%)
- Annual burn probability (40%)
- Ember load index (20%)
- Road density (20%)
- Population density (-10%). Reversed since the higher the population, the more difficult it may be to exit
- Slope (10%)

The results show higher egress risk or difficulty for Brownsville and Camptonville, likely due to their remote location and distance to major roads ({numref}`egress`).

```{figure} /figures/egress.png
:height: 600px
:name: egress
Wildfire egress risk analysis.
```

Although we didn't add age as a factor to egress risk, populations over 65 are more vulnerable to wildfire due to lower mobility, lack of access or knowledge of tech, and aging housing or inability to implement home hardening ({numref}`over65`). 

```{figure} /figures/over65.png
:height: 600px
:name: over65
Percent of Yuba County residents over 65.
```

## Vulnerable Communities
Poverty and wildfire risk are linked because higher-risk areas tend to be in disadvantaged communities {cite:p}`hino.` Generally, poverty is not high in Yuba County, with higher percent poverty near urban areas ({numref}`poverty`). Nevertheless, poverty is at the 2nd highest level in the NE corner of the county, so these communities are much more prone to egress risk and fire damage.

```{figure} /figures/poverty.png
:height: 600px
:name: poverty
Percent of Yuba County residents affected by poverty.
```

Communities in the heart of the high wildfire risk have slightly different threat levels despite the amount of thinning treatments surrounding them ({numref}`structures`). This may be due to a mismatch between treatment timing and dataset development or even a lag between the impact of thinning and the dependent variables we examined in each dataset. It may also be due simply to topography or forest state surrounding the community. More research, ground truth, or anecdotal evidence could uncover the reason behind this phenomenon.

```{figure} /figures/structures.png
:height: 600px
:name: structures
Wildfire threat community structures.
```
Community members identified unoccupied housing as a wildfire threat since home hardening may be less likely for property maintenance, and owners may be unable to extinguish smaller fires before they explode ({numref}`empty`). Note that the highest incidence of empty housing tracks the highest wildfire risk areas in the County.

```{figure} /figures/empty.png
:height: 600px
:name: empty
Percent empty housing units in Yuba County.
```


However, it may very well be that treatments are effective. If we zoom into Brownsville and Camptonville, many treated areas have lower risk levels ({numref}`comm_zoom`). Zonal statistics analysis of treatments and the threat index showed that threats were in the lower third distribution of raster values (Mean = 31, Range 1-40 with 17 being high risk and 40 low risk).

```{figure} /figures/comm_zoom.png
:height: 400px
:name: comm_zoom
A zoom into the Brownsville/Camptonville region showing treatments and risk index levels.
```

## Water Infrastructure
When we combined the ember load index, annual burn probability, distance from dams, and post-fire erosion risk to create a water infrastructure risk index, higher risk categories were still in the NE portion of the county. Still, large areas of lower risk were scattered throughout the region ({numref}`water`).

```{figure} /figures/water.png
:height: 600px
:name: water
Wildfire threat to water infrastructure.
```

Collins Lake, for instance, showed mostly low risk around its shoreline, except for a large area of high risk to the SE. Zooming into New Bullards Bar reservoir shows mostly low fire risk to water infrastructure closer to shore but higher risk further away from the reservoir ({numref}`nbb`). The upper and lower watersheds of New Bullards Bar generally had higher risk. Riparian areas seem to be particularly higher risk, perhaps following findings that showed higher fire risk in this vegetation type due to lower treatment from vegetation/endangered species limitations in mixed conifer forests following the Angora Fire {cite}`safford`. Riparian areas on the Yuba River between New Bullards Bar and Englebright Dam seemed particularly high.

```{figure} /figures/nbb.png
:height: 400px
:name: nbb
A closer look at the New Bullards Bar Reservoir reveals low-risk nearshore and high-risk, particularly north and south of the dam.
```
Examining the average pixel value for the Risk Index across public lands showed that federal lands were at high risk, whereas lower elevation county and state lands were low risk ({numref}`agency`). Yuba Water Agency ranked in between, likely given the mix of low to high-risk land across its holdings.

```{figure} /figures/agency.png
:height: 400px
:name: agency
Average value by pixel across public land ownerships. The nonprofit value is for one landholding at Rice's Crossing Reserve along the Yuba River, owned by the Bear Yuba Land Trust.
```

## Barriers & Opportunities
Downscaled datasets for the County are generally non-existent or not focused on wildfire risk analysis, although the Regional Resource Kit data was usually very useful for this exercise. Finer-scale data and ground-truthing would help make the analysis much more accurate and possibly show specific parcels or forests that stand most at risk or need thinning or prescribed fire treatments.