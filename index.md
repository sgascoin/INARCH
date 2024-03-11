# Sentinel-2 snow products

## Data

### Level 2B products (L2B)

Sentinel-2 level 2B snow products have a 5-day revisit and a spatial resolution of 20 m. 

`LIS_S2-SNOW-FSC*.tif` provides the fractional snow cover:
- 0: No-snow
- ]0-100]: Snow cover fraction in percent
- 205: Cloud including cloud shadow
- 255: No data (permanent water bodies are classified as nodata)

`LIS_S2-SNOW-FSC-QCFLAGS*.tif` provides quality flags for more expert users:
- bit 0: MAJA sun too low for an accurate slope correction
- bit 1: MAJA sun tangent
- bit 2: water mask
- bit 3: tree cover density > 90%
- bit 4: snow detected under thin clouds
- bit 5: tree cover density undefined or unavailable
- bit 6: FSC in shaded slope set to 100

The filename of the product indicates the acquisition time in UTC. For example `LIS_S2-SNOW-FSC_T11UNT_20170704T185934_1-10_01.tif` corresponds to 2017/07/04 18:59:34

`LIS_S2-SNOW-FSC_*.xml` provides various metadata. 

### Level 3B products (L3B)

Sentinel-2 level 2B snow products have a 1-year period and a spatial resolution of 20 m. Each level 3B products is an aggregation of level 2B products over a hydrological year. The default period is 01 Sep to 31 Aug for sites in in the northern hemisphere, 01 Mar to 28-29 Feb in the southern hemisphere.

- `*SCD*.tif`: snow cover duration in number of days i.e. the *total* number of snow days over the period.
- `*SMOD*.tif`: date of snow disappearance (Snow Melt-Out Date), defined as the last date of the longest snow period. The dates are given in number of days since the first date of the synthesis.
- `*SOD*.tif`: date of snow appearance (Snow Onset Date), defined as the first date of the longest snow period. The dates are given in number of days since the first date of the synthesis.
- `*NSP*.tif`: number of snow periods, a snow period being a continuous period of snow cover at the daily time step (experimental)
- `*NOBS*.tif`: number of clear observations to compute the SCD, SMOD, SOD and NSP (can be used as a quality indicator)

The filename of the product also indicates the aggregation period
- `start_date-end_date` (date in `yyymmdd` format)

### Data access

The data by Sentinel-2 tile are available from different sources. European catchments are already covered by Copernicus Land and can be obtained from [https://doi.org/10.2909/3e2b4b7b-a460-41dd-a373-962d032795f3](https://doi.org/10.2909/3e2b4b7b-a460-41dd-a373-962d032795f3). INARCH catchments outside Europe were processed by CNES over the period 2020-2023 and are available from [https://hydroweb.next.theia-land.fr/](https://hydroweb.next.theia-land.fr/). I cropped some of these INARCH products by region of interest to simplify the data download and use (contact me if you wish to modify the region). The cropped products are available here: [https://mycore.cnrs.fr/index.php/s/XmwmjpqWKXuyFMS](https://mycore.cnrs.fr/index.php/s/XmwmjpqWKXuyFMS). In the future I may include more catchments, especially in Europe if that is useful. Below are the snow cover duration (SCD) from the level 3B products.

![WolfCreek](https://github.com/sgascoin/INARCH/assets/29677722/bfe775de-3fd1-44dc-8b11-2398572bbe03)
![ValleHermoso](https://github.com/sgascoin/INARCH/assets/29677722/22a6e123-3df2-4525-8d88-70cb90fddbe6)
![Salcca](https://github.com/sgascoin/INARCH/assets/29677722/8eed5316-9f69-4078-9cca-2ae9e1ace29e)
![ReynoldsCreek](https://github.com/sgascoin/INARCH/assets/29677722/5846cc1d-3e88-431a-b936-046ebba6f80e)
![Peyto](https://github.com/sgascoin/INARCH/assets/29677722/bbccac5b-7127-4ffe-9c07-2a34daf3ffb8)
![Marmot](https://github.com/sgascoin/INARCH/assets/29677722/b5020ee9-ca42-4b8d-a9dc-047204f1ee58)
![Leiwuqi](https://github.com/sgascoin/INARCH/assets/29677722/398fa629-a119-40e5-bbda-0ddbd888951a)
![Langtang](https://github.com/sgascoin/INARCH/assets/29677722/c0c03c69-6e4e-4400-aeea-df0756360cf3)
![Kyzylsu](https://github.com/sgascoin/INARCH/assets/29677722/15645781-6da7-4b93-87bc-8d8c633293d6)
![Helen](https://github.com/sgascoin/INARCH/assets/29677722/fcc5b091-cfb0-43cb-91f1-3d758d93778c)
![Fugle](https://github.com/sgascoin/INARCH/assets/29677722/2a0edc34-1199-4017-b3cb-5958b5c8307f)
![Fortress](https://github.com/sgascoin/INARCH/assets/29677722/d7444457-4df7-4960-86a9-7d931eb3e445)
![EsteroLasBayas](https://github.com/sgascoin/INARCH/assets/29677722/cf16c8ce-c78a-49a1-b897-edf2ec601e22)
![Djankuat](https://github.com/sgascoin/INARCH/assets/29677722/f79ac52b-53ce-48ee-bd03-4aad267c3305)
![Brewster](https://github.com/sgascoin/INARCH/assets/29677722/b6e4c621-fc03-4d2e-9331-f8ae9e6f2007)

The map below indicates where to access the (non-cropped) data.

<iframe width="100%" height="300px" frameborder="0" allowfullscreen allow="geolocation" src="//umap.openstreetmap.fr/fr/map/sentinel-2-snow-products_1036308?scaleControl=false&miniMap=false&scrollWheelZoom=false&zoomControl=true&editMode=disabled&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=false&captionMenus=true"></iframe><p><a href="//umap.openstreetmap.fr/fr/map/sentinel-2-snow-products_1036308?scaleControl=false&miniMap=false&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=null&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=false&captionMenus=true">Full screen</a></p>

## Method

The data were generated using the [MAJA]([url](https://gitlab.orfeo-toolbox.org/maja/maja/)) and [LIS]([url](https://gitlab.orfeo-toolbox.org/remote_modules/let-it-snow)https://gitlab.orfeo-toolbox.org/remote_modules/let-it-snow) pipeline [1]. MAJA and LIS are open source software created at [CESBIO]([url](https://www.cesbio.cnrs.fr/)) and maintained in collaboration with CNES. This pipeline is used in operational mode for Theia (CNES) and Copernicus Land (EEA).

The snow cover detection is based on several test including the the normalized difference snow index (NDSI). The snow cover fraction is also computed using the NDSI using an empirical function. The accuracy of the snow detection at 20 m resolution (i.e. 0 > FSC ≥ 100) was estimated to 94% (proportion of correct classifications) [2]. The accuracy of the snow cover fraction was estimated to ~30% at 20 m resolution [3]. The snow cover detection can fail in steep shaded slopes and dense forests. The algorithm was not optimized to discriminate snow and ice, therefore other methods should be used to determine the snow cover area on glaciers. The set of INARCH tiles (outside Europe) was generated using the latest version of LIS (1.10) which includes an enhanced algorithm for shaded snow. Quality flags can be used to filter these pixels. In addition, FSC products with a non-valid ZS value (-1000) are expected to be less reliable (see in the metadata file).

Feel free to [open an issue](https://github.com/sgascoin/INARCH/issues) if you have a request or a comment.

## References

[1] Gascoin, S., Grizonnet, M., Bouchet, M., Salgues, G., & Hagolle, O. (2019). Theia Snow collection : High-resolution operational snow cover maps from Sentinel-2 and Landsat-8 data. Earth System Science Data, 11(2), 493‑514. https://doi.org/10.5194/essd-11-493-2019

[2] Barrou Dumont, Z., Gascoin, S., Hagolle, O., Ablain, M., Jugier, R., Salgues, G., Marti, F., Dupuis, A., Dumont, M., & Morin, S. (2021). Brief communication : Evaluation of the snow cover detection in the Copernicus High Resolution Snow & Ice Monitoring Service. The Cryosphere, 15(10), 4975‑4980. https://doi.org/10.5194/tc-15-4975-2021

[3] Gascoin, S., Barrou Dumont, Z., Deschamps-Berger, C., Marti, F., Salgues, G., López-Moreno, J. I., Revuelto, J., Michon, T., Schattan, P., & Hagolle, O. (2020). Estimating Fractional Snow Cover in Open Terrain from Sentinel-2 Using the Normalized Difference Snow Index. Remote Sensing, 12(18). https://doi.org/10.3390/rs12182904


