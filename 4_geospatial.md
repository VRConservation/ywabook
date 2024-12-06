# Yuba Geospatial Analysis

## Introduction
Agency and business focus on forest health and treatment is a recognized priority of California. Workforce and business development is a key part of the State’s efforts toward improving forest health, in large part to reduce wildfire risk and damage. This report focuses on Yuba County as a case study in statewide efforts to reestablish a forest-focused industry, treat forests, and address wildfire risk to communities, the infrastructure they rely on, and surrounding forests. 

Like many counties in the Sierra Nevada foothills, Yuba County spreads across the valley up into the foothills. The vegetation cover and topography changes dramatically, from level grasslands in west County to step, forested slopes in east County. The county’s water infrastructure and communities are spread across this varying landscape.  

Yuba County’s forested areas have small, remote communities. Often bordering public lands, these communities are the most densely vegetated, and spread from community centers into the wildland urban interface. Ranging from (population size), these communities (age, poverty, home ownership -second, primary). 

Publicly managed forests in Yuba county, like many across California, experienced a shift in management over the past 30 years that moved from timber production. A result is more densely vegetated areas at risk for forest fires. Wile areas surrounding Yuba county have seen catastrophic fires covering large geographic areas in the last decade, Yuba County has experienced smaller scale fires. Mitigation for more damaging wildfires is a priority for the County, communities, Firesafe Council, and Yuba County Water Agency.  

Water and electrical infrastructure are (constructed, established, ) among the foothills, both serving the communities in east County, and the more populated communities in west county. Roadways (type and responsibility for maintenance) are an important factor in access, what is treated, and who is responsible for treatment.  

Local officials, agencies, and communities want to improve forest conditions. Yet, they find themselves confronted by barriers. In Yuba county, some barriers identified are (barriers identified at a Firesafe Council community meeting on October 9, 2024 included) 

We wanted to provide visual representation of risk, treatability, responsibility or partnership, and priority. These questions lead us to who and what are at risk, and what is their risk level?  

Goal: We want to show who and what is at risk, the level of risk, how accessible treatment is, and who may lead addressing treatment.  

## Overview

## Questions
We aimed to address the following questions:

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
5. Run the model combining each weigthed dataset
6. Perform additional analysis as needed, e.g., zonal statistics

The majority of datasets were downloaded from the Sierra Nevada Regional Resource Kit {cite:t}`rrk` but others came from FRAP and national level datasets. **Citations**. In general risk for any of the analyses increased moving from lower to higher elevations and agricultural to forested systems. Not surprising since we were were relying on datasets largely focused on fire and forest, but not great for the communities in the extreme northeast of county such as Camptonville, Dobbins, and Brownsville {numref}`location`.

```{figure} /figures/location.png
:height: 300px
:name: location
Yuba County location in California showing generalized vegegation categories.
```

### Egress risk


### Vulnerable communities


### Water infrastructure


## Barriers
To addressing risks

## Opportunities
To addressing risks