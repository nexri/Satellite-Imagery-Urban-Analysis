# Evaluating Metrics Dedicated to Public Transport Through Urban Density Gradient Analysis of Multi-Modal Satellite Imagery

## Authors
Paweł Tomkiewicz $^{1,2}$, Jacek Jaworski $^{2}$, Paweł Zielonka $^{2}$

$^{1}$ WSB Merito University in Gdańsk, Poland  
$^{2}$ NexRI Laboratory for Artificial Intelligence, Gdańsk

## Abstract

## Abstract
This paper presents a novel computational approach for evaluating urban metrics through density gradient analysis using multi-modal satellite imagery, with applications including public transport and other urban systems. By combining optical and Synthetic Aperture Radar (SAR) data, we develop a method to segment urban areas, identify urban centers, and quantify density gradients. Our approach calculates two key metrics: the density gradient coefficient (α) and the minimum effective distance (LD) at which density reaches a target threshold. We demonstrate that these metrics provide an effective screening tool for public transport analyses by revealing the underlying urban structure. Through comparative analysis of two representative cities with contrasting urban morphologies (monocentric vs polycentric), we establish relationships between density gradient characteristics and public transport network topologies. Cities with clear density peaks in their gradient plots indicate distinct urban centers requiring different transport strategies than those with more uniform density distributions. This methodology offers urban planners a cost-effective, globally applicable approach to preliminary public transport assessment using freely available satellite data.

## 1. Introduction

Recent advancements in remote sensing technology have greatly expanded access to diverse satellite data types, including optical imagery and Synthetic Aperture Radar (SAR). Platforms such as the Copernicus Data Space, Sentinel Hub, and commercial providers have democratized these datasets for researchers, urban planners, and commercial users [1-3]. This proliferation of open-access satellite data has catalyzed numerous analytical methodologies in urban studies, agriculture, environmental monitoring, and disaster management [4,5].

However, effectively analyzing this vast repository of multi-modal satellite data presents significant challenges, requiring robust computational resources and advanced mathematical modeling capabilities. Traditional methods that rely on manual processing and simplistic modeling often fall short in fully exploiting satellite data's potential [6,7]. In response, an ecosystem of startups and research initiatives has emerged to bridge the gap between complex satellite data and actionable insights, with particular focus on SAR data processing, analytics automation, and user-friendly dissemination [8]. Despite these advancements, there remains a critical need for simple, robust, and computationally efficient methodologies suitable for resource-limited environments where traditional, expensive urban planning methods may not be feasible or cost-effective [9].

A pressing global challenge is optimizing transportation infrastructure, which underpins economic growth, urban sustainability, and social equity. In many urban areas, transportation networks — including communications pathways, logistics, and especially public transit systems — lag behind optimal efficiency, contributing to congestion, pollution, and reduced quality of life [10,11]. Addressing this challenge requires innovative approaches capable of rapidly and reliably assessing transportation infrastructure efficiency through spatial urban characteristics.

This paper proposes a novel computational approach designed to analyze urban density gradients using multi-modal satellite imagery for public transport evaluation. Our methodology integrates optical and SAR data to efficiently segment urban areas, identify urban centers, and quantify spatial density distributions. We introduce two key metrics — the density gradient coefficient (α) and the minimum effective distance (LD) — offering urban planners a straightforward yet powerful means of preliminary assessment that directly connects urban morphology to public transport optimization strategies. This approach provides significant advantages in accessibility, resource utilization, and scalability, enabling robust transportation infrastructure assessment for diverse urban configurations, including monocentric and polycentric city structures [12,13].

The urban density gradient, which describes how building and population density change with distance from urban centers, has significant implications for public transport planning. Steep gradients (high α values) typically indicate compact urban forms that efficiently support mass transit, while shallow gradients suggest sprawling development patterns requiring different transport solutions. Through our analysis, we demonstrate that cities can be categorized based on their gradient density plots — with clear distinctions between monocentric cities (showing a single dominant peak) and polycentric cities (exhibiting multiple density peaks). These morphological differences have direct implications for optimal public transport network design.

## 2. Related Work

### 2.1 Urban Density Gradient Models and Transport Planning

Urban density gradient analysis originated with the classic monocentric city model pioneered by Alonso [14], Muth [15], and Mills [16]. This foundational work established the negative exponential density function describing how population density typically decreases with distance from the city center. Clark's [17] empirical work validated this model across numerous cities, confirming that population density follows the pattern:

$$D(r) = D_0 e^{-\alpha r}$$

Where:
- $D(r)$ is the density at distance r from the center
- $D_0$ is the central density
- $\alpha$ is the density gradient coefficient

Bertaud and Malpezzi [18] expanded this analysis to a global dataset of 48 cities, demonstrating how density gradients vary across different urban contexts and development stages, highlighting the relationship between density patterns and transportation efficiency. Cervero and Kockelman [19] further developed the connection between urban form and transport planning through their "3Ds" framework—density, diversity, and design—to explain how built environment characteristics influence travel behavior. Ewing and Cervero [20] later expanded this to the "5Ds" by adding destination accessibility and distance to transit, firmly establishing the theoretical link between urban density patterns and transport efficiency.

### 2.2 Monocentric versus Polycentric Urban Development

While the monocentric model provides a useful baseline, contemporary urban forms often exhibit polycentric structures. Garreau [21] documented the emergence of "edge cities," while Gordon and Richardson [22] tracked the systematic decentralization of employment and commercial activities in metropolitan areas. Theoretical frameworks for understanding polycentric development have been advanced by Anas et al. [23], who proposed models accounting for multiple centers and subcenters. McMillen and Smith [24] demonstrated that the number of subcenters in an urban area relates systematically to population size and commuting costs.

Importantly for our work, Bertaud [25] argued that even polycentric cities typically maintain a dominant center, suggesting that gradient analysis remains valuable in complex urban systems. His concept of "urban spatial structure" describes both population distribution and trip patterns within metropolitan areas, providing a bridge between urban form and transport needs.

### 2.3 Public Transport Efficiency Metrics and Spatial Determinants

Public transport system efficiency has been evaluated through various metrics. Vuchic [26] established fundamental relationships between transport network design and urban form, while Mees [27] emphasized the importance of network planning over technological solutions. Newman and Kenworthy [28] demonstrated strong correlations between urban density and transport energy use across global cities, establishing approximately 35 people per hectare as a minimum density threshold for viable public transport service.

Building on this work, Cervero and Guerra [29] quantified the relationship between density and transit ridership, finding that light rail systems become cost-effective at densities of 30 people per hectare, while heavy rail requires approximately 45 people per hectare.

### 2.4 Remote Sensing for Urban Transport Analysis

Remote sensing applications in urban transport analysis have grown significantly. Thakuriah et al. [30] reviewed applications of geospatial data in transportation planning, while Taubenböck et al. [31] used remote sensing to identify urban growth patterns and their implications for sustainable transport planning. Li et al. [32] demonstrated methods for extracting road networks from high-resolution satellite imagery, and Barrington-Leigh and Millard-Ball [33] tracked global street-network connectivity and its relationship to transportation efficiency.

### 2.5 Multi-modal Satellite Data Fusion for Urban Studies

The integration of multiple satellite data types has proven particularly valuable for comprehensive urban analysis. Zhu et al. [34] reviewed methods for fusing optical and SAR data, highlighting complementary strengths that improve urban feature extraction. Esch et al. [35] developed the Global Urban Footprint using SAR data, demonstrating its effectiveness for identifying built-up areas globally, while Pesaresi et al. [36] created similar products using optical imagery through the Global Human Settlement Layer project.

Gamba and Dell'Acqua [37] showed that multi-sensor fusion techniques significantly improve the accuracy of urban area delineation and structural characterization. Li et al. [38] addressed the challenge of identifying urban centers from satellite imagery, developing automated methods that align with our approach to gradient analysis. Similarly, Taubenböck et al. [39] proposed methods for classifying urban spatial patterns from remote sensing data that directly inform public transport planning.

Our work builds upon these foundations by integrating density gradient analysis with multi-modal satellite data processing, among other things, for public transport analyses. By quantifying the relationship between urban morphology and transport network requirements through our proposed metrics, we provide a novel computational tool that bridges urban remote sensing and transport planning disciplines.

## 3. Methodology

### 3.1 Data Sources and Preprocessing
Our approach utilizes optical satellite imagery and Synthetic Aperture Radar (SAR) imagery from the Copernicus Data Space [1-3]. The multi-modal nature of our dataset leverages the complementary strengths of both data types: optical imagery provides visual features and textural information, while SAR offers penetration capability and illumination-independent measurements of urban structures [34, 35].

For our analysis pipeline, we use:
- Optical Sentinel-2 satellite true color images (RGB format)
- SAR Sentinel-1 backscatter intensity images (Interferometric Wide Swath, VV-polarisation)

Preprocessing includes:
- Image registration to ensure spatial alignment between optical and SAR data
- Standardization to a uniform pixel resolution
- Normalization of intensity values to comparable ranges
- Edge preservation to maintain critical urban boundaries during processing

### 3.2 Urban Structure Analysis Pipeline
Our methodology follows a systematic workflow as illustrated in Figure 1. The process consists of several key sequential steps:

![Urban Density Gradient Analysis Methodology Pipeline](figure_1.svg)

*Figure 1: Urban Density Gradient Analysis Methodology Pipeline. Flow diagram showing the processing sequence from Sentinel-1/2 imagery through multi-modal fusion, segmentation, and parallel analysis of urban centers and density gradients, yielding classification metrics α and LD for characterizing urban morphology*

A. **Edge detection and density mapping from optical imagery**: We apply Sobel operators to identify structural boundaries in optical images. These edge maps provide critical information about the spatial organization of urban features. Edge density is then calculated using Gaussian blurring to create a continuous density field that highlights areas with concentrated structural elements.

B. **SAR imagery processing for building structure identification**: SAR backscatter data is particularly sensitive to building structures due to corner reflections and multiple bounces from vertical surfaces [35, 37]. We normalize the SAR data for integration with optical-derived features to ensure comparable intensity scales.

C. **Multi-modal data fusion of optical and SAR data**: We combine the edge density information from optical imagery with the structural information from SAR data to create a comprehensive urban density map. To remove noise while preserving important structural edges, we apply Non-Local Means denoising, which is particularly effective at maintaining sharp transitions in urban boundaries.

D. **Urban area segmentation**: Using density thresholds derived from histogram decomposition of our combined image, we segment the urban landscape into three primary categories. The segmentation is performed using Gaussian mixture model decomposition of the combined image histogram to automatically determine optimal thresholds:

$$
S(x,y) =
\begin{cases}
  1 \text{ (Water)}, & \text{if } \rho(x,y) < \tau_{water} \\
  2 \text{ (Terrain)}, & \text{if } \tau_{water} \leq \rho(x,y) < \tau_{urban} \\
  3 \text{ (Urban)}, & \text{if } \rho(x,y) \geq \tau_{urban}
\end{cases}
$$

Where:
- $S(x,y)$ is the segmentation class at pixel location $(x,y)$
- $\rho(x,y)$ is the combined density value at pixel location $(x,y)$
- $\tau_{water}$ is the water threshold determined as the first intersection point between Gaussian components
- $\tau_{urban}$ is the urban threshold determined as the second intersection point between Gaussian components

These thresholds are automatically calculated for each image through the following process:

a. Decompose the histogram of the combined image into three Gaussian components
b. Identify intersection points between adjacent Gaussian components
c. Use the first intersection as the water threshold and the second intersection as the urban threshold

This adaptive approach improves robustness across different images and geographic regions by automatically adjusting thresholds to the specific characteristics of each image.

Morphological operations are then applied to refine the urban mask and remove noise:

$$U_{refined} = \text{Close}(\text{Dilate}(U_{initial}, k), k)$$

Where:
- $U_{initial}$ is the initial urban mask where $S(x,y) = 3$
- $k$ is a $5 \times 5$ structuring element
- Dilate and Close are standard morphological operations

To ensure meaningful urban analysis, we filter out small disconnected patches:

$$
U_{final}(x,y) =
\begin{cases}
1 & \text{if } (x,y) \in C_i \text{ and } \text{Area}(C_i) \geq 100 \text{ pixels} \\
0 & \text{otherwise}
\end{cases}
$$

Where:
- $C_i$ represents the $i$-th connected component in the urban mask.

E. **Urban center identification**: Urban centers are identified as regions with particularly high density values, defined by:

$$
C(x,y) =
\begin{cases}
  1, & \text{if } \rho(x,y) > \tau_{center} \text{ and } U_{final}(x,y) = 1 \\
  0, & \text{otherwise}
\end{cases}
$$

Where:
- $C(x,y)$ indicates whether pixel $(x,y)$ is part of an urban center
- $\rho(x,y)$ is the combined density value
- $\tau_{center} = 1.4$ is the urban center threshold
- $U_{final}(x,y)$ is the final urban mask

This approach aligns with established methodologies for identifying urban centers from remote sensing data [38, 40].

F. **Distance-based density gradient calculation**: We calculate how urban density changes with distance from identified urban centers using a Euclidean distance transform. For each distance increment, we calculate the mean density of all urban pixels at that distance, creating a density-distance profile that characterizes the urban structure.

To quantify this relationship systematically, we implement the following approach:

a. **Distance Transform**: Using the identified urban center points as reference locations, we apply a Euclidean distance transform to create a distance map where each pixel value represents its distance from the nearest urban center:

$$
D(x,y) = \min_{(c_x,c_y) \in C} \sqrt{(x-c_x)^2 + (y-c_y)^2}
$$

Where:
- $D(x,y)$ is the distance value at pixel location $(x,y)$
- $C$ is the set of all urban center points (locations where urban density exceeds the center threshold)

b. **Urban Area Filtering**: We extract distances and densities only for pixels within urban areas:

$$
D_{urban} = \{D(x,y) \mid (x,y) \in U\}
$$

$$
\rho_{urban} = \{\rho(x,y) \mid (x,y) \in U\}
$$

Where:
- $U$ is the set of all urban pixels (as identified in our segmentation)
- This ensures our gradient analysis focuses only on built-up areas

c. **Distance Binning and Mean Density Calculation**: For each integer distance value, we calculate the mean density of urban pixels at that distance:

$$
\rho(d) = \frac{1}{|P_d|} \sum_{p \in P_d} \rho(p)
$$

Where:
- $P_d = \{p \in U \mid d \leq D(p) < d+1\}$ is the set of urban pixels with distance in bin $d$
- Each bin has a width of 1 pixel, which corresponds to the satellite resolution (typically 5-20m)

The result is a series of points $(d, \rho(d))$ that represent how urban density changes with distance from urban centers. This density-distance profile forms the foundation for our gradient analysis and urban morphology classification. For subsequent analysis, we convert the pixel distances to real-world units (kilometers) by multiplying by the satellite resolution. The resulting density gradient profile directly informs public transport planners by revealing the spatial distribution of urban density.

### 3.3 Density Gradient Metrics
We calculate two key metrics for each analyzed city:

A. **Density Gradient Coefficient (α)**: The slope of the regression line through local minima in the density-distance curve, measured in units per kilometer. This value indicates how rapidly urban density decreases with distance from centers.

We calculate α through linear regression on selected density minima points using:

$$
\alpha = \frac{n\sum_{i=1}^{n}(d_i \cdot \rho_i) - \sum_{i=1}^{n}d_i \sum_{i=1}^{n}\rho_i}{n\sum_{i=1}^{n}d_i^2 - (\sum_{i=1}^{n}d_i)^2}
$$

Where:
- $d_i$ is the distance from urban center (in km) at point $i$
- $\rho_i$ is the urban density value at point $i$
- $n$ is the number of local minima points identified in the density gradient

The α coefficient provides a quantitative measure of urban compactness, analogous to the exponential decay parameter in Clark's urban density model [17], but adapted for multi-modal satellite data. Steeper gradients (more negative α values) typically indicate more compact urban forms with rapid density decreases moving away from centers.

B. **Minimum Effective Distance (LD)**: The distance at which urban density reaches a target threshold value considered minimal for efficient public transport service. This is calculated as the x-intercept of the regression line at the target density.

We calculate LD using the formula:

$$
LD = \frac{\rho_{target} - \beta}{\alpha}
$$

Where:
- $\rho_{target}$ is the target density threshold (typically set to the minimum density found in urban areas)
- $\beta$ is the y-intercept of the regression line
- $\alpha$ is the density gradient coefficient calculated above

This metric directly relates to Newman and Kenworthy's [28] and Cervero and Guerra's [29] findings on minimum density thresholds for viable public transport. It represents the effective radius within which public transport service is likely to be efficient based on density patterns.

### 3.4 Urban Morphology Classification
We classify cities based on their density gradient plots:

A. **Monocentric Cities**: Characterized by a single dominant peak in the density-distance curve, with density decreasing relatively uniformly with distance from the center. We aim to extend this definition to include cases with steeper density gradients, where density drops more rapidly as distance from the center increases.

B. **Polycentric Cities**: Exhibit multiple peaks in the density-distance curve, indicating several urban centers of varying intensity.

The peak detection algorithm identifies local maxima in the density gradient plot with a prominence threshold scaled to the data range. Mathematically, we identify peaks where:

$$
\rho_i > \rho_{i-1} \text{ and } \rho_i > \rho_{i+1} \text{ and } \rho_i - \min(\rho_L, \rho_R) > p \cdot (\rho_{max} - \rho_{min})
$$

Where:
- $\rho_i$ is the density at point $i$
- $\rho_L$ and $\rho_R$ are the lowest density values between point $i$ and the nearest higher peaks to the left and right
- $p$ is the prominence factor (typically 0.02)
- $\rho_{max}$ and $\rho_{min}$ are the maximum and minimum density values across the entire profile

This classification methodology aligns with established urban morphology theories from Bertaud [25] and Anas et al. [23], providing a quantitative basis for distinguishing between different urban spatial structures using satellite data. Our approach not only identifies multiple centers in polycentric cities but also quantifies their relative importance and spatial relationships. This information is crucial for designing efficient public transport networks that serve complex urban spatial structures.

### 3.5 Implementation Simplicity
While the mathematical formulations presented in this methodology may appear complex, the actual Python implementation is remarkably straightforward thanks to several powerful libraries that handle much of the computational complexity. The implementation leverages:

- **OpenCV**: Provides essential image processing functions including edge detection (`cv2.Sobel`, `cv2.magnitude`), morphological operations (`cv2.dilate`, `cv2.morphologyEx`, `cv2.MORPH_CLOSE`), connected component analysis (`cv2.connectedComponentsWithStats`), and non-local means denoising (`cv2.fastNlMeansDenoising`).
- **NumPy**: Supports efficient array manipulations (`np.array`, `np.zeros_like`, `np.clip`), mathematical operations (`np.max`, `np.min`), and masked array functionality (`np.ma.masked_array`) crucial for density calculations.
- **SciPy**: Offers specialized functions such as distance transforms (`scipy.ndimage.distance_transform_edt`), peak finding algorithms (`scipy.signal.find_peaks`), and statistical analysis tools for regression (`scipy.stats.linregress`).
- **Matplotlib**: Enables the visualization of urban segmentation results and density gradient plots through functions like `plt.figure`, `plt.plot`, `plt.axhline`, and `plt.savefig`.
- **scikit-learn**: Provides metrics like mean squared error (`sklearn.metrics.mean_squared_error`) for validation of our gradient model.

Using these libraries, the complete urban density gradient analysis can be implemented in under 200 lines of code. This efficient implementation makes the methodology particularly valuable for resource-constrained settings, where complex urban analysis might otherwise be prohibitive.

The computational efficiency means that analysts can process entire cities in minutes rather than hours, enabling rapid comparative studies across multiple urban areas. The complete implementation, with additional examples and documentation, is available in an open-source repository under the MIT license at https://github.com/nexri/Satellite-Imagery-Urban-Analysis, making this methodology accessible to urban planners, researchers, and policy makers worldwide.

## 4. Results

This section presents the results of applying our multi-modal satellite imagery analysis methodology to two Polish urban areas with contrasting morphologies: Malbork and Klodzko. We present the output from each stage of our processing pipeline, demonstrating the progression from raw satellite data to quantified urban density gradients.

### 4.1 Satellite Imagery Results
In Figure 2, optical and SAR satellite imagery are presented for two analyzed urban areas: Malbork (left column) and Klodzko (right column). The optical images (Figure 2a-b, top row) reveal distinct urban morphologies. Malbork's optical image shows a compact urban structure divided by the Nogat River, with the distinctive castle complex visible in the central area. The two parts of the city separated by the river differ in size and complexity, with the eastern (right) section displaying a more complex urban pattern. Malbork's road network follows a predominantly radial configuration, with most roads converging toward the city center.

In contrast, Klodzko's optical image displays an urban area whose development is constrained by valley topography, with settlement distributed along several corridors defined by the surrounding terrain. This distinctive morphology is further shaped by the main road that traverses the urban area from south to north, resulting in a city configuration markedly different from Malbork's radial structure.

The SAR backscatter intensity images (Figure 2c-d, bottom row) highlight vertical structures, with brighter pixels indicating stronger returns from building walls and roofs. These SAR images clearly align with patterns visible in the optical imagery. Malbork's SAR image exhibits concentrated brightness in its central area, corresponding to its dense historic core, while Klodzko's SAR image reveals multiple bright zones distributed across its urban extent, reflecting its more dispersed development pattern.

![Original Satellite Imagery](figure_2.jpg)

*Figure 2: Input satellite data: (a) Malbork optical RGB image (left) and (b) Klodzko optical RGB image (right) in the top row; (c) Malbork SAR backscatter intensity image (left) and (d) Klodzko SAR backscatter intensity image (right) in the bottom row.*

### 4.2 Edge Detection and Fusion Results
In Figure 3, the edge detection results and combined optical-SAR urban density maps are presented. The top row shows edge detection results for Malbork (Figure 3a, left) and Klodzko (Figure 3b, right). These edge maps highlight the structural boundaries present in the urban fabric, revealing distinct patterns in both urban areas. Malbork's edge map displays a dense network in the central area with more regular, radially-organized patterns in peripheral zones. Klodzko's edge map, by contrast, exhibits more irregular structural patterns that reflect the topographical constraints on urban development.

The bottom row of Figure 3 presents the combined optical-SAR urban density maps for Malbork (Figure 3c, left) and Klodzko (Figure 3d, right). These maps integrate edge information from optical imagery with backscatter intensity from SAR data to produce comprehensive urban density representations. Brighter areas correspond to higher density values, effectively revealing the concentration of urban structures.

Malbork's combined image exhibits a more pronounced contrast in brightness distribution, with clearly defined high-density areas that stand out against the surrounding regions. The central area displays particularly bright values, making it easier to detect high-density urban zones. This distinct brightness pattern facilitates clear identification of both the overall urban area boundary and the city center.

In contrast, Klodzko's combined image shows a more uniform color distribution across its urban extent, making the detection of high-density areas more challenging. This uniformity reflects Klodzko's more dispersed urban pattern, where density varies less dramatically across the urban area. Despite this relative uniformity, the combined image still effectively delineates the overall urban area boundary, though with less pronounced internal density variations compared to Malbork.

![Edge Detection and Combined Images](figure_3.jpg)

*Figure 3: Edge detection and fusion results: (a) Malbork edge detection result (left) and (b) Klodzko edge detection result (right) in the top row; (c) Malbork combined optical-SAR urban density map (left) and (d) Klodzko combined optical-SAR urban density map (right) in the bottom row.*

### 4.3 Histogram Decomposition and Urban Centers
In Figure 4 there are presented the histogram decomposition results and the segmented urban areas with identified centers. The top row shows histogram decomposition for Malbork (Figure 4a, left) and Klodzko (Figure 4b, right). In both cases, the algorithm identified three main components in the value histograms.

For Malbork, the histogram decomposition plot reveals three clearly distinct components: the lowest one corresponding to the river values distribution on the combined image, the mid-range component representing land areas, and the third component related to the brightest values indicated as urban. The thresholds were automatically detected at τ_water = 0.51 and τ_urban = 1.02. It's important to note that the amplitude of these components cannot be treated as a direct measurement of the area of a given landscape type. Rather, it is a value histogram showing the frequency of given intensity values. However, in Malbork's case, a clear intersection of these components arises at the values given above.

In the case of Klodzko, the situation is quite similar but may be misleading since there are no significant water components in the urban area. Thus, the water threshold (τ_water = 0.53) should be treated as distinguishing different land components with varying SAR reflectivity. The urban threshold was detected at τ_urban = 1.02, identical to Malbork's value. Despite this complexity, the histogram analysis still effectively enables the delineation of urban areas and the identification of urban centers.

The bottom row of Figure 4 presents the segmented urban areas with identified centers for Malbork (Figure 4c, left) and Klodzko (Figure 4d, right). These images show urban areas in gray and urban centers in red, based on the density thresholds derived from the histogram analysis. Malbork's segmentation shows a single dominant center corresponding to its historic core, while Klodzko's segmentation displays multiple proportionate centers distributed across its urban footprint.

![Histogram and Urban Centers](figure_4.jpg)

*Figure 4: Histogram analysis and segmentation: (a) Malbork histogram decomposition (left) and (b) Klodzko histogram decomposition (right) in the top row; (c) Malbork segmented urban area with identified urban centers (left) and (d) Klodzko segmented urban area with identified urban centers (right) in the bottom row.*

### 4.4 Urban Density Gradient Results
Figure 5 presents the urban density gradient plots for both study areas, quantifying the spatial distribution of urban density as a function of distance from identified centers. These visualizations enable direct comparative analysis of the fundamental urban structural characteristics of Malbork and Klodzko.

![Density Gradient Plots](figure_5.jpg)

*Figure 5: Urban density gradient analysis: (a) Malbork density gradient plot (left) and (b) Klodzko density gradient plot (right). Each figure consists of two connected plots: the upper portion shows gradient density and fitting (yielding α values), while the lower portion shows deviations from the fitted line, highlighting areas of varying uniformity.*

Figure 5a (left) depicts Malbork's density gradient, characterized by a relatively uniform density decrease with distance from the center. The linear regression analysis yields a gradient coefficient α = -0.018/km, while the minimum effective distance (LD) is calculated at 21.8 km. Conversely, Figure 5b (right) illustrates Klodzko's density gradient, with a linear regression yielding α = -0.013/km and LD = 23.4 km. The visualization incorporates additional statistical parameters through color-coding, including the variation of gradient values with respect to all identified centers and the interquartile ranges (IQR, 25-75%) of all center-to-urban gradient distributions, providing comprehensive quantitative metrics for structural comparison.

The lower portions of Figures 5a and 5b display the difference plots, constructed by calculating the deviation between observed density values and the fitted regression model at each distance increment. This deviation analysis, computed as (observed density - fitted density), effectively identifies regions where urban development diverges from the idealized linear gradient model, revealing areas of both uniformity and non-uniformity in the urban fabric and highlighting zones containing multiple density peaks.

Malbork's difference plot exhibits a notably uniform pattern extending approximately 1 km from the center, with minimal deviation from the regression model, followed by increased variability characterized by multiple peaks of varying amplitudes and inter-peak distances. In contrast, Klodzko's difference plot demonstrates perturbations throughout the entire urban extent, including areas proximal to the center, with both perturbation frequency and amplitude increasing proportionally with distance. This quantitative analysis confirms the qualitative observations from the satellite imagery examination, indicating that Klodzko exhibits a less centralized and more heterogeneously distributed urban pattern compared to Malbork's more concentrated structure.

## 5. Discussion

Our study intentionally selected two Polish urban areas—Malbork and Klodzko—as they represent distinct urban morphologies while sharing comparable regional contexts. This selection enables direct comparative analysis of how different urban forms influence density gradients and their implications for public transport.

Malbork (population: approximately 38,500) is a historically significant city in northern Poland characterized by a classic monocentric urban structure. Its development has been shaped by its medieval origins, with the UNESCO World Heritage Teutonic Knights' castle forming a clear historical center [40]. The city's urban fabric radiates outward from this central point, following a relatively uniform pattern typical of traditional European urban development. With an area of approximately 17.2 km², Malbork maintains a moderate population density of about 2,240 people per km².

In contrast, Klodzko (population: approximately 27,000) in southwestern Poland exhibits a more complex polycentric structure. Its development has been significantly constrained by the surrounding mountainous topography of the Kłodzko Valley [41]. The city's urban pattern follows several corridors defined by the valleys, resulting in a more distributed settlement pattern. With an area of approximately 25 km², Klodzko has a lower population density of about 1,080 people per km², reflecting its more dispersed urban form.

Both study areas were analyzed using Copernicus Data Space satellite imagery at an identical 5-meter spatial resolution. This consistent resolution is sufficient to identify individual buildings and street patterns while enabling efficient processing of the entire urban area. The Copernicus database provided high-quality, cloud-free optical imagery and corresponding SAR data for both locations, making them ideal candidates for our multi-modal analysis approach. The selection of these contrasting urban morphologies—one compact and monocentric, the other dispersed and polycentric—within the same national context provides an excellent test case for evaluating the effectiveness of our density gradient methodology for public transport assessment.

In this study, we used building density as an input parameter, primarily due to its data availability – it might be reliably and efficiently extracted from satellite imaging, which offers wide coverage and regular updates. In contrast, population density data is often outdated, inconsistently collected, or unavailable for many regions, especially in rapidly growing urban areas. Furthermore, building density serves as a reasonable and accessible proxy for population density, as numerous studies have shown a strong statistical correlation between the two. Areas with high building density typically correspond to zones with higher concentrations of inhabitants, making it a practical substitute in spatial planning contexts. By using building density, we ensured a more scalable and reproducible approach to transport planning, especially in regions lacking detailed demographic data. This method also supports dynamic analysis as satellite imaging data can reflect urban development over time.

The density gradient difference plots (Figure 5) reveal distinctive patterns that quantitatively confirm the qualitative observations of urban morphology evident in the satellite imagery. These differences have significant implications for public transport in each city which are revealed or more detaily analized in Figure 6.

![Regional analysis of density gradient differences](figure_6.jpg)

*Figure 6: Regional analysis of urban density gradient differences: (a) Malbork with three distinct regions (left) and (b) Klodzko with three regions (right). Green background indicates uniform regions, and red background highlights highly variable regions. For Malbork, Region 1 (0-1.41 km) shows remarkable uniformity, while Regions 2 (1.41-4.96 km) and 3 (4.96-8.10 km) display increasing variability. For Klodzko, all regions—Region 1 (0-1.70 km), Region 2 (1.70-4.65 km), and Region 3 (4.65-8.41 km)—display significant variability with no uniform central region.*

Malbork's difference plot exhibits a remarkably uniform pattern extending approximately 1.4 km from the center (Region 1 in Figure 6a, highlighted in green), with minimal deviation from the regression model. This uniformity indicates a well-defined, coherent urban core with consistent density—a characteristic ideal for hub-based public transport systems. Beyond this 1.4 km radius, the plot begins to show a variable region (Region 2, 1.4-4.96 km) of multiple medium-height peaks, representing secondary density nodes at intermediate distances. At farther distances (Region 3, 4.96-8.1 km), the peaks demonstrate higher amplitude but wider spacing, indicating sparse but concentrated satellite developments. The entire variable region spans from 1.4 to 8.1 km, as clearly visualized in Figure 6a. This pattern aligns with Malbork's visual appearance in both optical and SAR imagery (Figures 2a, 2c), which shows a compact central area surrounded by distinct, separated development clusters.

In contrast, Klodzko's difference plot shows perturbations throughout the entire urban extent, including areas proximal to the center. As illustrated in Figure 6b, Klodzko exhibits a completely variable pattern with no uniform region, with the variable region extending from 0 to 8.4 km. The analysis reveals three distinct regions: Region 1 (0-1.7 km), Region 2 (1.7-4.65 km), and Region 3 (4.65-8.4 km), all characterized by significant perturbations. Both perturbation frequency and amplitude increase proportionally with distance from the identified centers. This pattern indicates a less centralized, more heterogeneously distributed urban structure with multiple density nodes of comparable significance. The consistent presence of peaks even near the nominal "center" suggests that Klodzko lacks a dominant central core, reflecting its development constraints imposed by valley topography. These observations are consistent with the optical and SAR imagery analysis (Figures 2b, 2d), which reveals a more dispersed urban pattern following topographical features.

The gradient coefficient (α) values provide further quantitative evidence of the morphological differences between the two cities. Malbork's steeper gradient (α = -0.018/km) compared to Klodzko's more gradual decline (α = -0.013/km) confirms that Malbork has a more centralized urban structure with density decreasing more rapidly with distance from the center. This steeper gradient typically indicates urban forms that can more efficiently support traditional hub-and-spoke public transport networks [28, 29].

The minimum effective distance (LD) metric further illustrates the transport planning implications of these different urban forms. Malbork's LD value of 21.8 km compared to Klodzko's 23.4 km indicates that Klodzko requires a larger service area to effectively cover its population due to its more dispersed development pattern. This finding aligns with established research showing that more compact urban forms generally enable more efficient public transport service coverage [29, 42].

Our analysis revealed potential methodological limitations that should be addressed in future studies. We found that the gradient and density metrics may vary depending on the threshold definitions derived from histogram decomposition. This sensitivity suggests that adding additional channels to the combined image could increase value resolution, resulting in more precise decomposition and ultimately better-defined gradient factors. While our current segmentation algorithms yield consistent results that align with the literature, further refinements could improve accuracy and robustness. Particularly, enhanced edge detection techniques and more sophisticated multi-modal fusion approaches could better delineate urban boundaries in complex topographical settings like those found in Klodzko.

The validity of our data is further supported by consistency across multiple Polish cities beyond those presented in this study. However, we recognize that threshold sensitivity could introduce variability when applying our methodology to dramatically different urban morphologies or in regions with significantly different built environment characteristics. Future research should explore adaptive thresholding techniques that automatically adjust to regional architectural and urban planning differences.

Our findings suggest promising directions for future research, particularly in developing optimization algorithms for urban transportation systems based on the parameters identified in this study. Since the α coefficient, LD metric, and region characteristics demonstrate consistency across our analysis, they could serve as input variables for models that define optimal urban transportation systems. This approach is planned for our next research phase, along with more comprehensive analysis of a larger sample of cities.

Even with the current data, our urban morphology classification provides clear guidance for public transportation strategies. For Malbork, the well-defined uniform Region 1 indicates an ideal environment for a centralized hub-based transit system, while the surrounding variable regions would benefit from feeder services connecting to this hub. In contrast, Klodzko's lack of a uniform central region and its three distinct variable regions suggest the need for a distributed transit system with multiple interconnected routes rather than a single dominant hub. This three-tiered communication scheme would better serve Klodzko's dispersed urban pattern and accommodate its topographical constraints.

## 6. Conclusions and Future Work

Our research demonstrates that multi-modal satellite imagery analysis can effectively inform public transport planners through the quantification of urban density gradients. By combining optical and SAR data, we have developed a methodology that efficiently segments urban areas, identifies urban centers and subcenters, and calculates key metrics characterizing urban morphology. The density gradient coefficient (α) and minimum effective distance (LD) metrics offer planners an effective screening tool to understand urban structure and its implications for transport efficiency.

The comparative analysis of Malbork and Klodzko illustrates how different urban morphologies require distinct public transport strategies. Malbork's monocentric structure with a well-defined uniform central region (α = -0.018/km) suggests an ideal environment for a hub-based transit system, while Klodzko's polycentric pattern with no uniform center (α = -0.013/km) indicates the need for a distributed network with multiple interconnected routes. These findings align with established urban planning principles while providing quantitative metrics to guide specific interventions.

Despite showing promising results, our approach would benefit from enhanced image channel integration to increase value resolution and improve threshold definition sensitivity. The segmentation algorithms, while already yielding consistent results, could be further refined to improve accuracy in complex topographical settings.

Future work could extend this approach by incorporating temporal analysis to track urban development and transport adaptation over time, developing predictive models for optimal transport network design based on our density metrics, creating automated tools for global city comparison, and integrating socioeconomic and travel behavior data for more comprehensive planning. Additionally, optimization algorithms that use our identified parameters as input variables could define optimal urban transportation systems tailored to specific urban morphologies.

The methodology presented in this paper offers urban planners a cost-effective, globally applicable approach to preliminary public transport assessment using freely available satellite data. In an era of rapid urbanization and increasing pressure on transportation infrastructure, our approach bridges the gap between remote sensing and transport planning, ultimately supporting more sustainable, efficient, and equitable urban mobility systems worldwide.

## Acknowledgments

The authors acknowledge the use of 2024/2025 data from the Sentinel-1/Sentinel-2 missions, made available through the European Union's and the European Space Agency's (ESA) Copernicus Programme. The data were accessed via the Copernicus Browser and processed by the authors.

## References

1. Drusch, M., Del Bello, U., Carlier, S., Colin, O., Fernandez, V., Gascon, F., Hoersch, B., Isola, C., Laberinti, P., Martimort, P., Meygret, A., Spoto, F., Sy, O., Marchese, F., & Bargellini, P. (2012). Sentinel-2: ESA's Optical High-Resolution Mission for GMES Operational Services. Remote Sensing of Environment, 120, 25-36.

2. Torres, R., Snoeij, P., Geudtner, D., Bibby, D., Davidson, M., Attema, E., Potin, P., Rommen, B., Floury, N., Brown, M., Traver, I.N., Deghaye, P., Duesmann, B., Rosich, B., Miranda, N., Bruno, C., L'Abbate, M., Croci, R., Pietropaolo, A., Huchler, M., & Rostan, F. (2012). GMES Sentinel-1 mission. Remote Sensing of Environment, 120, 9-24.

3. Berger, M., Moreno, J., Johannessen, J.A., Levelt, P.F., & Hanssen, R.F. (2012). ESA's sentinel missions in support of Earth system science. Remote Sensing of Environment, 120, 84-90.

4. Pesaresi, M., Ehrlich, D., Ferri, S., Florczyk, A., Freire, S., Halkia, M., Julea, A., Kemper, T., Soille, P., & Syrris, V. (2016). Operating procedure for the production of the Global Human Settlement Layer from Landsat data of the epochs 1975, 1990, 2000, and 2014. Publications Office of the European Union.

5. Ban, Y., Gong, P., & Giri, C. (2015). Global land cover mapping using Earth observation satellite data: Recent progresses and challenges. ISPRS Journal of Photogrammetry and Remote Sensing, 103, 1-6.

6. Wu, C., & Murray, A.T. (2003). Estimating impervious surface distribution by spectral mixture analysis. Remote Sensing of Environment, 84(4), 493-505.

7. Small, C., & Sousa, D. (2016). Humans on Earth: Global extents of anthropogenic land cover from remote sensing. Anthropocene, 14, 1-16.

8. Geoawesomeness. (2024). Geospatial Startups and Companies Directory. Retrieved from Geoawesomeness website.

9. Esch, T., Heldens, W., Hirner, A., Keil, M., Marconcini, M., Roth, A., Zeidler, J., Dech, S., & Strano, E. (2017). Breaking new ground in mapping human settlements from space – The Global Urban Footprint. ISPRS Journal of Photogrammetry and Remote Sensing, 134, 30-42.

10. Bertaud, A. (2018). Order without design: How markets shape cities. MIT Press.

11. Rodrigue, J.P. (2020). The geography of transport systems. Routledge.

12. Angel, S., Parent, J., Civco, D.L., Blei, A., & Potere, D. (2012). The dimensions of global urban expansion: Estimates and projections for all countries, 2000–2050. Progress in Planning, 75(2), 53-107.

13. Newman, P., & Kenworthy, J. (2015). The end of automobile dependence: How cities are moving beyond car-based planning. Island Press.

14. Alonso, W. (1964). Location and Land Use: Toward a General Theory of Land Rent. Harvard University Press.

15. Muth, R.F. (1969). Cities and Housing: The Spatial Pattern of Urban Residential Land Use. University of Chicago Press.

16. Mills, E.S. (1972). Studies in the Structure of the Urban Economy. Johns Hopkins University Press.

17. Clark, C. (1951). Urban Population Densities. Journal of the Royal Statistical Society: Series A (General), 114(4), 490-496.

18. Bertaud, A., & Malpezzi, S. (2003). The Spatial Distribution of Population in 48 World Cities: Implications for Economies in Transition. World Bank Report.

19. Cervero, R., & Kockelman, K. (1997). Travel Demand and the 3Ds: Density, Diversity, and Design. Transportation Research Part D: Transport and Environment, 2(3), 199-219.

20. Ewing, R., & Cervero, R. (2010). Travel and the Built Environment: A Meta-Analysis. Journal of the American Planning Association, 76(3), 265-294.

21. Garreau, J. (1991). Edge City: Life on the New Frontier. Doubleday.

22. Gordon, P., & Richardson, H.W. (1996). Beyond Polycentricity: The Dispersed Metropolis, Los Angeles, 1970-1990. Journal of the American Planning Association, 62(3), 289-295.

23. Anas, A., Arnott, R., & Small, K.A. (1998). Urban Spatial Structure. Journal of Economic Literature, 36(3), 1426-1464.

24. McMillen, D.P., & Smith, S.C. (2003). The Number of Subcenters in Large Urban Areas. Journal of Urban Economics, 53(3), 321-338.

25. Bertaud, A. (2003). The Spatial Organization of Cities: Deliberate Outcome or Unforeseen Consequence? World Development Report Background Paper.

26. Vuchic, V.R. (2005). Urban Transit: Operations, Planning, and Economics. John Wiley & Sons.

27. Mees, P. (2010). Transport for Suburbia: Beyond the Automobile Age. Earthscan.

28. Newman, P., & Kenworthy, J. (1999). Sustainability and Cities: Overcoming Automobile Dependence. Island Press.

29. Cervero, R., & Guerra, E. (2011). Urban Densities and Transit: A Multi-dimensional Perspective. Institute of Transportation Studies, University of California, Berkeley.

30. Thakuriah, P., Tilahun, N., & Zellner, M. (2017). Big Data and Urban Informatics: Innovations and Challenges to Urban Planning and Knowledge Discovery. In Seeing Cities Through Big Data (pp. 11-45). Springer.

31. Taubenböck, H., Esch, T., Felbier, A., Wiesner, M., Roth, A., & Dech, S. (2012). Monitoring Urbanization in Mega Cities from Space. Remote Sensing of Environment, 117, 162-176.

32. Li, Y., Tan, Y., Li, Y., Qi, S., & Tian, J. (2020). A Deep Learning-Based Method for the Detection of Roads from Remote Sensing Imagery. Remote Sensing, 12(9), 1444.

33. Barrington-Leigh, C., & Millard-Ball, A. (2017). The World's User-Generated Road Map is More than 80% Complete. PLOS ONE, 12(8), e0180698.

34. Zhu, X.X., Tuia, D., Mou, L., Xia, G.-S., Zhang, L., Xu, F., & Fraundorfer, F. (2017). Deep Learning in Remote Sensing: A Comprehensive Review and List of Resources. IEEE Geoscience and Remote Sensing Magazine, 5(4), 8-36.

35. Esch, T., Marconcini, M., Felbier, A., Roth, A., Heldens, W., Huber, M., Schwinger, M., Taubenböck, H., Müller, A., & Dech, S. (2013). Urban Footprint Processor—Fully Automated Processing Chain Generating Settlement Masks from Global Data of the TanDEM-X Mission. IEEE Geoscience and Remote Sensing Letters, 10(6), 1617-1621.

36. Pesaresi, M., Huadong, G., Blaes, X., Ehrlich, D., Ferri, S., Gueguen, L., Halkia, M., Kauffmann, M., Kemper, T., Lu, L., Marin-Herrera, M.A., Ouzounis, G.K., Scavazzon, M., Soille, P., Syrris, V., & Zanchetta, L. (2013). A Global Human Settlement Layer from Optical HR/VHR RS Data: Concept and First Results. IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, 6(5), 2102-2131.

37. Gamba, P., & Dell'Acqua, F. (2016). Multi-resolution Data Fusion for Urban Area Characterization. In Global Urban Monitoring and Assessment through Earth Observation (pp. 91-106). CRC Press.

38. Li, X., Gong, P., & Liang, L. (2015). A 30-Year (1984–2013) Record of Annual Urban Dynamics of Beijing City Derived from Landsat Data. Remote Sensing of Environment, 166, 78-90.

39. Taubenböck, H., Weigand, M., Esch, T., Staab, J., Wurm, M., Mast, J., & Dech, S. (2019). A New Ranking of the World's Largest Cities—Do Administrative Units Obscure Morphological Realities? Remote Sensing of Environment, 232, 111353.

40. UNESCO World Heritage Centre. (2011). Castle of the Teutonic Order in Malbork. Retrieved from UNESCO World Heritage List website.

41. Latocha, A. (2017). Geomorphologically-oriented land use planning for sustainable development in mountainous areas: A case study of the Kłodzko Valley, SW Poland. Geomorphology, 297, 72-82.

42. Kenworthy, J.R., & Laube, F.B. (1999). Patterns of automobile dependence in cities: an international overview of key physical and economic dimensions with some implications for urban policy. Transportation Research Part A: Policy and Practice, 33(7-8), 691-723.