# Geospatial
A geospatial analysis of risk and conditions and how they relate to communities and infrastructure in Yuba County.

## Takeaways
1. The **Yuba County communities** most at risk from wildfire are in the northeast portion of the county. Approximately in risk order, they are Brownsville, Dobbins, and Camptonville. However, Brownsville and Camptonville carry more difficulty for egress during a wildfire event. Strategies to mitigate risk in each community may differ based on risk factors such as community characteristics, land ownership, and landscape/vegetation characteristics.
2. Our analysis of **water infrastructure** at risk showed nuanced results dependent on location. The upper and lower watershed at New Bullards Bar has a higher risk than the middle. Riparian areas are generally at high risk due to heavy vegetation growth and post-fire impact, such as hillside erosion due to steep slopes or treatment impacts to listed species. The area to the southeast of Collins Lake is at higher risk, but much surrounding the lake is at low risk. The land surrounding Lake Francis is at low risk, but much of the land to the east of the lake is at high risk. Englebright Dam and surrounding riparian areas are at high risk.
3. **Downscaling, updating, or creating datasets**, such as climate change data, forest conditions, and road conditions, would make the risk analyses more accurate.

## Background
Like many counties in the Sierra Nevada foothills, Yuba County spreads across the valley up into the foothills ({numref}`location`). The vegetation cover and topography change dramatically, from level grasslands in the west county to steep, forested slopes in the east county. Water infrastructure, electrical infrastructure, and population centers are arrayed across this varied landscape. Yuba County’s forested areas are home to small, remote communities. Often bordering public lands, these communities are the most densely vegetated and expand from community centers into the wildland-urban interface. Our geospatial analysis focuses on the communities and infrastructure most at risk of wildfire in Yuba County. With these risk areas identified, Yuba County leadership, agencies, and community members can identify priority areas and develop informed strategies for treatment. 

```{figure} /figures/location.png
:height: 600px
:name: location
Yuba County's location in California shows generalized vegetation categories.
```

Over the past thirty years, the management of publicly managed forests in Yuba County has shifted away from timber production due to ecosystem impacts and financial unsustainability. This has resulted in more densely vegetated areas at risk for forest fires.

Local officials, agencies, and communities want to improve forest conditions but face barriers. Mitigating more damaging wildfires is a priority for the County, communities, Yuba Watershed Protection and Firesafe Council, and Yuba Water Agency.

While areas surrounding Yuba County have seen catastrophic fires covering large geographic regions in the last decade, Yuba County has experienced smaller-scale fires. To show this, we analyzed Sentinel-1 radar data, illustrating the striking difference in areas affected by fires from March 2019 to March 2023. We examined changes in the forest canopy in the landscapes surrounding Camptonville in Yuba County and Greenville in Plumas County. We found a difference of 7.5 km2 affected by fire in the Camptonville area of interest but a whopping two orders of magnitude greater difference of 1,047 km2 surrounding Greenville ({numref}`change`).

```{figure} /figures/change.png
:height: 600px
:name: change
Radar change detection analysis from Landsat 8 imagery between 2019-24. Imagery and computing courtesy of USGS and Google Earth Engine.
```

Water and electrical infrastructure in the foothills serve the remote communities in east county and the more populated west county. Clear roadway access and maintenance are critical for public safety; however, the needs and responsibilities vary across the region.

We wanted to visually represent risk, treatability, responsibility, partnership, and priority. These questions led us to who and what is at risk and what the risk level is.

## Study Questions
Our study questions were formed through engagement with key organizations and agencies in Yuba County, one-on-one conversations with Yuba County residents engaged in forestry and fire reduction roles, and concerns raised by respondents to the SWOT survey. To conduct the study, we aimed to address the following questions:
- What is at risk? And what is the level of risk?
- Who is at risk? And what is their level of risk?
- Who is responsible for addressing that risk?
- Where are their opportunities to work together to address risk if not responsible?
- What are some options to address these risks? (Options for treatment)
- What are some barriers to treating these risks? (e.g., lack of downscaled data or funding to mitigate risk)
- What is missing to address risk? (e.g., programs, funding, workforce, access, capacity, and data)

## Methods
We created three models based on available raster and vector data sets. The datasets were weighted in each circumstance according to the importance and impact on the community, infrastructure, or natural resources. We tended to use the suitability modeler tool in ArcGIS Pro since it easily uploaded the raster datasets, weighted them, and then combined them into a single model. Each model output creates a report showing the workflow's datasets, weighting, and visual representation. The only downside of using the suitability modeler is that it tended to crash the software when using large datasets. To address this issue, we clipped each dataset to a smaller area of interest (AOI) in the Yuba County region.

In general, the workflow for the geospatial analysis was
1. Download or link rest services for the datasets.
2. Clip the dataset to the AOI.
3. Upload the datasets to the model.
4. Weight and transform each dataset.
5. Run the model combining each weighted dataset.
6. Perform additional analysis as needed, e.g., zonal statistics.

Most datasets were downloaded from the Sierra Nevada Regional Resource Kit {cite}`resourcekit`, but others came from CAL FIRE’s Fire and Resource Assessment Program (FRAP) and national level datasets {cite:p}`census`. For the radar analysis, we used Sentinel-1 data, with images from March 2019 and March 2024, a five-year difference. The backscatter was set to -0.15 and polarization to vertical horizontal, sometimes called VH. The VH and backscatter settings do a better job of capturing tree canopy change. Radar can capture imagery through clouds and smoke and gives a good measure of surface roughness or detect where trees used to be when comparing images.

Generally, the risk for any analyses increased when moving from lower to higher elevations and agricultural to forested systems. This is unsurprising since we relied on datasets focusing on fire, forest, and topography. The analysis presented important considerations for the communities in the extreme northeast of the county, such as Camptonville, Dobbins, and Brownsville. Other datasets are cited in each section or within each figure below in the text.

## Egress Risk
The egress risk analysis did not work well with the suitability modeler tool, so we weighted and added the rasters using Python and a Jupyter Notebook. The rasters and percent weighting were as follows:
- Distance to cell tower (20%)
- Annual burn probability (40%)
- Ember load index (20%)
- Road density (20%)
- Population density (-10%). Reversed since the higher the population, the more difficult it may be to exit.
- Slope (10%)

**The results show higher egress risk or difficulty for Brownsville and Camptonville**, likely due to their remote location and distance to major roads. Community members may benefit from additional education about evacuation plans and routes. ({numref}`egress`).

```{figure} /figures/egress.png
:height: 600px
:name: egress
Wildfire egress risk analysis.
```

 ## Vulnerable Communities
Although we didn’t add age as a factor to egress risk, populations over 65 are more vulnerable to wildfire due to lower mobility, lack of access or knowledge of tech, and aging housing or inability to implement home hardening ({numref}`over65`). While elderly residents in all communities may benefit from assistance, Dobbins and Oregon House communities had higher concentrations of residents over 65. **These regions may benefit from focused assistance programs for home hardening, defensible space, fuel breaks, and emergency planning**. 

```{figure} /figures/over65.png
:height: 600px
:name: over65
Percent of Yuba County residents over 65.
```
 
Poverty and wildfire risk are linked because higher-risk areas tend to be in disadvantaged communities {cite:p}`hino`. Generally, poverty is not high in Yuba County, with higher percent poverty near urban areas ({numref}`poverty`). Nevertheless, poverty is at the 2nd highest level in the County's northeast corner, so these communities are much more prone to egress risk and fire damage. **Communities around Brownsville, Camptonville, Challenge, Clipper Mills, and Strawberry Valley may benefit from financial assistance programs for private property clearing**. 

```{figure} /figures/poverty.png
:height: 600px
:name: poverty
Percent of Yuba County residents affected by poverty.
```
 
Communities in the heart of the high wildfire risk have slightly different threat levels despite the amount of thinning treatments surrounding them ({numref}`structures`). This may be due to a mismatch between treatment timing and dataset development or even a lag between the impact of thinning and the dependent variables we examined in each dataset. It may also be due simply to topography or forest state surrounding the community. **More research, ground truthing, or anecdotal evidence could uncover the reason behind this phenomenon**.

```{figure} /figures/structures.png
:height: 600px
:name: structures
Wildfire threat community structures.
```
 
In the SWOT survey, community members identified absentee landowners and unoccupied housing as a wildfire threat since home hardening may be less likely to occur for property maintenance, and owners may not be able to extinguish smaller fires before they explode ({numref}`empty`). Note that the highest incidence of empty housing tracks the highest wildfire risk areas in the County. **This northeast region may benefit from focused outreach to second homeowners, seasonal residents, or absentee landowners on the importance of thinning, home hardening, and community safety**. 

```{figure} /figures/empty.png
:height: 600px
:name: empty
Percent empty housing units in Yuba County.
```
 
Despite existing threats, treatments may be effective. If we zoom into Brownsville and Camptonville, many treated areas have lower risk levels ({numref}`community`). Zonal statistics analysis of treatments and the threat index showed that threats were in the lower third distribution of raster values (Mean = 31, Range 1-40 with 17 being high risk and 40 low risk).

```{figure} /figures/community.png
:height: 400px
:name: community
A zoom into the Brownsville/Camptonville region showing treatments and risk index levels.
```
 
## Water Infrastructure
When we combined the ember load index, annual burn probability, distance from dams, and post-fire erosion risk to create a water infrastructure risk index, higher risk categories were still in the northeast portion of the county. Still, large areas of lower risk were scattered throughout the region ({numref}`water`).

```{figure} /figures/water.png
:height: 600px
:name: water
Wildfire threat to water infrastructure.
```

Collins Lake, for instance, showed mostly low risk around its shoreline, except for a large area of high risk to the southeast. Zooming into New Bullards Bar Reservoir shows mostly low fire risk to water infrastructure closer to shore but higher risk further away from the reservoir ({numref}`nbb`). The upper and lower watersheds of New Bullards Bar generally had higher risk. Riparian areas seem to be particularly higher risk, perhaps following findings that showed higher fire risk in this vegetation type due to lower treatment from vegetation/endangered species limitations in mixed conifer forests following the Angora Fire {cite}`safford`. **Riparian areas on the Yuba River between New Bullards Bar and Englebright Dam were particularly high**.

```{figure} /figures/nbb.png
:height: 400px
:name: nbb
A closer look at the New Bullards Bar Reservoir reveals low-risk areas nearshore and the high-risk regions north and south of the dam.
```
 
Due to limited available data, our analysis focused on dams and spillways. Further analysis of water infrastructure (canals, meters, storage, flumes, etc.) would provide a clearer picture of infrastructure at risk in these communities. **Additional analysis may also include electrical infrastructure and communication towers**. 

Addressing infrastructure and community risk across landownership is essential. Infrastructure crosses land ownership boundaries, communities are adjacent to public and private lands, and wildfire is not selective about whose land is burning. Examining the average pixel value for the Risk Index across public lands showed that **federal lands were at high risk**, whereas lower elevation county and state lands were low risk ({numref}`agency`). **Yuba Water Agency ranked in between, likely given the mix of low to high-risk land across its holdings**. These results are especially relevant to interagency, landscape-scale collaborations. 

```{figure} /figures/agency.png
:height: 400px
:name: agency
Average value by pixel across public land ownerships. The nonprofit value is for one landholding at Rice's Crossing Reserve along the Yuba River, owned by the Bear Yuba Land Trust.
```

 ## Listed Species & Fire
Threatened and endangered species can be at risk from fires since their habitats tend to be small or fragmented. When fire frequency is outside the normal range of variation, species can be at higher risk. The location of listed species can limit compliance for forest health and infrastructure projects. We analyzed listed species richness and time since last fire to create a suitability map across the northwestern portion of the County. Portions of this analysis mirror select methodologies used by {cite:p}`kelsey` but were not as in-depth for this study.

The analysis found a similar trend of higher suitability moving uphill northwest in the county {numref}`species`. However, in lower elevations, there were two areas where species richness is higher at Texas Hill and south of Camptonville, where the listed species and fire index is higher.

Many organizations are beginning to examine the impacts of forest health projects on biodiversity, water, or species. The species impact map in the geospatial chapter could be deepened and used for planning, engaging partners, and as one metric to measure project impacts on the landscape. Similar approaches could be taken for economic and local business development.

```{figure} /figures/species.png
:height: 600px
:name: species
Listed species richness and time since last fire suitability map.
```

## Barriers & Opportunities
Downscaled datasets for the county are generally non-existent or not focused on wildfire risk analysis, although the Regional Resource Kit data was usually very useful for this exercise. Finer-scale data and ground-truthing would make the analysis much more accurate and show specific parcels, or forest stands most at risk or needing thinning and prescribed fire treatments.

**Our analysis was limited to publicly accessible data and datasets from partnering organizations**. Further analysis would benefit from additional data and could provide a clearer picture of:
-  Infrastructure risks of electrical resources, water storage, and communications.
- Absentee landowners using tax address information.
- Roadways using road type or conditions (i.e., paved, gravel, dirt.) for ingress and egress.

## Parting Thoughts
Yuba County faces significant wildfire risks, particularly in its northeastern communities like Brownsville, Dobbins, and Camptonville, where challenges in egress and dense vegetation heighten the threat. An analysis of water infrastructure shows varying risk levels across different regions, with areas such as the upper and lower watershed of New Bullards Bar and riparian zones being especially vulnerable. To improve the accuracy of risk assessments, updated datasets on climate change, forest conditions, and road statuses are crucial. By identifying these high-risk areas and utilizing enhanced data, Yuba County leaders and community members can prioritize and implement targeted mitigation strategies to protect lives, property, and critical infrastructure from wildfire impacts.