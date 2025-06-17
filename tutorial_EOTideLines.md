
<a href="https://www.ohb-ds.de/en/geospatial-solutions/earth-observation-solutions" target="_blank">
    <img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/EOTideLines_test_dark.png" alt="Image" width="150"/>
</a>

# EOTideLines: Monitoring Tidal Bathymetry from Space

<a href="https://www.ohb-ds.de/en/geospatial-solutions/earth-observation-solutions" target="_blank"><img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/OHB_DS_logo_white.png" alt="Image" width="150"/></a>&nbsp;&nbsp;in collaboration with&nbsp;&nbsp;<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/ESA_logo_2020_Deep.png" alt="Image" width="100"/>
<br><br>

[**EOTideLines**](https://eotideline.lab.dive.edito.eu/) is an Earth Observation product that monitoring the state of the tidal bathymetry. It displays the latest position of low tide line derived from Landsat and Sentinel-2 optical images coupled with a tidal model. This contour delineates the low-tide bathymetry and can be used to:
- Provide near-real time information of the state of the intertidal bathymetry.
- Highlight the presence of transient features like sand banks, shoals and channels.
- Identify potential obstacles that can impair navigability in harbour entrances and delay operations.
- Support better planning and execution of dredging works by understanding past migration rates and direction of sand transport.
- Provide historical insights to better understand geomorphological changes in tidal bathymetry.

A short video on how to use the webapp is available [here](https://www.youtube.com/watch?v=h_SVAUlRhDY&ab_channel=OHBDigitalServices).

> This product was funded by the European Space Agency (ESA) under the EO for the Port of the Future (EO4PORTS) initiative: ESA AO/1-11850/23/I-DT.

> Contact [Dr. Kilian Vos](mailto:kilian.vos@ohb-ds.de) for more information or requests on [**EOTideLines**](https://eotideline.lab.dive.edito.eu/).

### 🛰️ How does it work?
- An image processing algorithm analyses publicly available imagery (Landsat and Sentinel2) and links the images with a tidal model to map the low-tide line. 
- The low-tide lines can be visualized in the portal for various areas (currently North Sea coast of Germany, NL and Belgium) and time periods (currently 2020-date). 
- Users can download the data as spatial layers (GeoJSON files) to integrate in a GIS environment. 

### 💡 Benefits 
- Enhanced situational awareness for maritime operations. 
- Improved planning and execution of dredging activities. 
- Better understanding of nearshore coastal dynamics and sediment transport. 

### 🛠️ Methodology
The step-by-step methodology developed to extract the low-tide line from publicly available satellite imagery is briefly described here:
<ol>
<li><strong>Retrieve imagery of AOI</strong></li> 
All the available Landsat 5, 7, 8, 9 and Sentinel-2 images are retrieved from their respective collections.
<br><br>
<li><strong>Assign a tide level to each image</strong></li> 
The global tide model developed by CNES 
<a href="https://www.aviso.altimetry.fr/en/data/products/auxiliary-products/global-tide-fes/release-fes22.html" target="_blank">
    FES2022 (Finite Element Solution)
</a>
is used to assign a tide level to every satellite image.
<a href="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Wadden_Sea_32UME_050_tide_timeseries_v5.jpg" target="_blank">
    <img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Wadden_Sea_32UME_050_tide_timeseries_v5.jpg" alt="tides"
    style="width: 75%; height: auto; object-fit: contain;" />
</a>
<br><br>
<li><strong>Compute a low-tide NDWI composite</strong></li>
The satellite images captured at low tide (bottom 30% of the springs tidal range) are used to compute a composite NDWI (Normalized Difference Water Index) image. 
The 70th percentile is taken when calculating the composite to give more weight to dry pixels. 
<br><br>
<li><strong>Extract the sand/water contours</strong></li>
Use the NDWI contrast between water and wet sand to extract the low-tide line from the composite as a vector line.
<a href="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/2024_Wadden_Sea_32UME_048_lowtideline_v5.jpg" target="_blank">
<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/2024_Wadden_Sea_32UME_048_lowtideline_v5.jpg" alt="tides"
style="width: 75%; height: auto; object-fit: contain;" />
</a>
<li><strong>This process is repeated for each 10x10km grid cell and can be applied anywhere globally.</strong></li>
</ol>

### 🌐 Use Cases

#### 1. Navigability along the Holwerd-Ameland ferry route

In the Wadden Sea (Netherlands part), the ferry route between the island of Ameland and Holwerd on the mainland faces issues due to the accumulation of sand in the navigation channel. According to [local newspapers](https://nltimes.nl/2023/06/26/six-possible-solutions-ameland-ferry-issues-consideration), the narrowing of the width of the channel has led to situations where ferries cannot safely pass each other, resulting in delays and cancellations. The channel also needs to be dredged on a daily basis, which comes at a huge financial and environmental cost.

<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Ameland_ferry/ferryline6.png" alt="ferry"
style="width: 50%; height: auto; object-fit: contain;" />
<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Ameland_ferry/ferry_line4.jpg" alt="ferry"
style="width: 40%; height: auto; object-fit: contain;" />

With Earth Observation and the EOTideLines data on tidal bathymetry, we can monitor the evolution of the navigation channel and surrounding sand features over the last few years. 

By mapping the low tide line on composite satellite imagery we can extract the current position of the navigation channel and its width. 

<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Ameland_ferry/ferry_line_1.jpg" alt="ferry" style="width: 85%; height: auto; object-fit: contain;" />

By going back in time with the satellite archive, we can also observe how this channel has evolved over the last 5 years as sediment gets stirred and reshaped by currents, tides and winds.

 When looking at changes in Low Tide Line over the last few years, it is clear that this is a very dynamic environment with sand features moving up to 100 metres within a year. In particular, there is a large shoal next to the navigation channel that is constantly being reshaped and has migrated West by almost half a kilometre between 2020 and 2024.

<img src="https://minio.dive.edito.eu/oidc-kvos/eotideline/assets/Ameland_ferry/ferryline7_edit.png" alt="ferry" style="width: 85%; height: auto; object-fit: contain;" />

While the satellite observations do not provide a solution to the management of the Holwerd-Ameland ferry line, the low tide lines provide important data on the dynamics of the coastal system that can be used by environmental planners and maritime operators to inform their strategies. If the navigation channel is continuously migrating West, can it be an option to create a new route East of the sand shoal?

**This application demonstrates the value of including satellite observations in a coastal Digital Twin to better understand how changes in bathymetry can affect navigability.**
