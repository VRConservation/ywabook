# Geospatial
A geospatial analysis of communities and infrastructure at risk in Yuba County.

## Takeaways
1. Where are communities and areas most at risk?
2. General findings
3. Suggestions for more analysis

## Overview
Agency and business focus on forest health and treatment is a recognized priority of California. Workforce and business development is a key part of the State’s efforts toward improving forest health, in large part to reduce wildfire risk and damage. This report focuses on Yuba County as a case study in statewide efforts to reestablish a forest-focused industry, treat forests, and address wildfire risk to communities, the infrastructure they rely on, and surrounding forests. 

Like many counties in the Sierra Nevada foothills, Yuba County spreads across the valley up into the foothills ({numref}`location`). The vegetation cover and topography changes dramatically, from level grasslands in west County to step, forested slopes in east County. The county’s water infrastructure and communities are spread across this varying landscape. Yuba County’s forested areas have small, remote communities. Often bordering public lands, these communities are the most densely vegetated, and spread from community centers into the wildland urban interface. Ranging from (population size), these communities (age, poverty, home ownership -second, primary). 

```{figure} /figures/location.png
:height: 600px
:name: location
Yuba County location in California showing generalized vegegation categories.
```

Publicly managed forests in Yuba County, like many across California, experienced a shift in management over the past 30 years that moved from timber production. A result is more densely vegetated areas at risk for forest fires. Wile areas surrounding Yuba County have seen catastrophic fires covering large geographic areas in the last decade, Yuba County has experienced smaller scale fires. Mitigation for more damaging wildfires is a priority for the County, communities, Firesafe Council, and Yuba County Water Agency.  

Water and electrical infrastructure are established among the foothills, both serving the communities in east County, and the more populated communities in west county. Roadways (type and responsibility for maintenance) are an important factor in access, what is treated, and who is responsible for treatment. Local officials, agencies, and communities want to improve forest conditions. Yet, they find themselves confronted by barriers. In Yuba County, some barriers identified are (barriers identified at a Firesafe Council community meeting on October 9, 2024 included) 

We wanted to provide visual representation of risk, treatability, responsibility or partnership, and priority. These questions lead us to who and what are at risk, and what is their risk level?  

## Questions
To conduct the study, we aimed to address the following questions:

- What is at risk? And what is their level of risk? 
- Who is at risk? And what is their level of risk? 
- Who is responsible for addressing that risk? 
- If not responsible, where are their opportunities to work together to address risk? 
- What are some options to address these risks? (Options for treatment) 
- What are some barriers to treating these risks? (e.g., lack of downscaled data, or funding to mitigate risk) 
- What is missing to address risk? (e.g., programs, funding, workforce, access, capacity and data.) 

## Geospatial analysis
We created three models based on available raster and vector data sets. The datasets were weighted in each circumstance according to the importance and impact on the community, infrastructure, or natural resources in question. We tended to use the suitability modeler tool in ArcGIS Pro since it easily uploaded the raster datasets, weighted them and then combined them in a single model. Each model output had the option of creating a report showing the datasets, weighting and visual representation of the work flow. The only downside of using the suitability modeler is it tended to crash the software when datasets were large. To address this we clipped each dataset to a smaller area of interest (AOI) in the Yuba County region.

In general the workflow for the geospatial analysis was

1. Download or link rest services for the datasets. 
2. Clip the dataset to the AOI
3. Upload the datasets to the model
4. Weight and transform each dataset
5. Run the model combining each weighted dataset
6. Perform additional analysis as needed, e.g., zonal statistics

The majority of datasets were downloaded from the Sierra Nevada Regional Resource Kit but others came from FRAP and national level datasets {cite}`resourcekit`. **Other Citations**. In general risk for any of the analyses increased moving from lower to higher elevations and agricultural to forested systems. Not surprising since we were were relying on datasets largely focused on fire and forest, but not great for the communities in the extreme northeast of county such as Camptonville, Dobbins, and Brownsville. Other datasets are cited in each section or within each figure below in the text.

### Egress risk
The egress risk analysis did not work well with the suitability modeler tool so we weighted and added the rasters together using Python and a Jupyter notebook ({numref}`egress`). The rasters and percent weighting were as follows

- Distance to cell tower (20%)
- Annual burn probability (40%)
- Ember load index (20%)
- Road density (20%)
- Population density (-10%). Reversed since the higher the population the more difficult it may be to exit
- Slope (10%)

```{figure} /figures/egress.png
:height: 600px
:name: egress
Wildfire egress risk analysis.
```

### Vulnerable communities
Communities in the heart of the high wildfire risk have slightly different threat levels despite the amount of thinning treatments surrounding them ({numref}`structures`). This may be due to a mismatch between treatment timing and dataset development or even a lag between impact of thinning and the dependent variables we examined in each dataset. It may also be due simply to topography or forest state surrounding the community. More research, ground-truthing, or anecdotal evidence could uncover the reason behind this phenomena.


```{figure} /figures/structures.png
:height: 600px
:name: structures
Wildfire threat community structures.
```

However, it may very well be that treatments are effective. If we zoom into Brownsville and Camptonville, many of the treated areas have lower risk levels ({numref}`comm_zoom.png`). In fact, zonal statistics analysis of treatments and the threat index showed that threats were in the lower third distribution of raster values (Mean = 31, Range 1-40 with 17 being high risk and 40 low risk).

```{figure} /figures/comm_zoom.png
:height: 400px
:name: comm-zoom
A zoom into the Brownsville/Camptonville region showing treatments and risk index levels.
```

### Water infrastructure
When we took ember load index, annual burn probability, distance from dams, and post-fire erosion risk, higher risk categories were still in the NE portion of the county, but there were large areas of lower risk scattered throughout the region ({numref}`water`).

```{figure} /figures/water.png
:height: 600px
:name: water
Wildfire threat to water infrastructure.
```

The smaller reservoir, Collins Lake, for instance showed mostly low risk around its shoreline, except a large area of high risk to the SE. Zooming into New Bullards Bar reservoir shows mostly low fire risk to water infrastructure closer to shore but higher risk further away from water areas ({numref}`nbb`). Riparian areas seem to be particularly higher risk, perhaps following findings that showed higher fire risk in this vegetation type due to lower treatment from vegetation/endangered species limitations in mixed conifer forests following the Angora Fire {cite}`safford`.

```{figure} /figures/nbb.png
:height: 400px
:name: nbb
A closer look at the New Bullards Bar Reservoir reveals low risk nearshore and high risk further afield.
```

## Barriers
To addressing risks

## Opportunities
To addressing risks