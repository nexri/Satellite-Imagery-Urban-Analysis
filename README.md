# Satellite Imagery Urban Analysis

A Python toolkit for analyzing urban density patterns from satellite imagery using optical and SAR data. This tool segments land cover types, measures urban density gradients, and visualizes spatial patterns to quantify urban structure.

## Overview

This project processes satellite imagery to:
1. Detect edges and create density maps from optical imagery
2. Combine optical and SAR data for improved urban detection
3. Segment images into water, terrain, and urban areas
4. Calculate urban density gradients from city centers
5. Generate visualizations for urban analysis

## Input Data

The tool uses two primary inputs:
- Optical satellite imagery (e.g., `gdansk_optical_1.jpg`)
- SAR (Synthetic Aperture Radar) imagery (e.g., `gdansk_sar_1.jpg`)

Satellite data can be obtained from the [Copernicus Data Space](https://browser.dataspace.copernicus.eu/).

## Configuration Parameters

Key parameters that can be adjusted:

```python
# Segmentation thresholds
water_threshold = 0.4        # Below this value is classified as water
urban_threshold = 1.25       # Above this value is classified as urban
urban_center_threshold = 1.4 # Above this value is classified as urban center

# Resolution settings
satellite_pixel_resolution = 20  # 20m per pixel

# Scale intervals for plots
image_x_tick_interval = 5000     # 5km intervals for main maps
gradient_x_tick_interval = 1000  # 1km intervals for gradient plots
```

## Output Visualizations

The tool generates several visualizations:

### 1. Original & Sobel Edge Detection
Shows the original image alongside Sobel edge detection results to highlight urban boundaries and structures.

### 2. Edge Density & SAR
Displays the derived edge density map and the SAR image, both normalized to 0-1 range.

### 3. Combined & Segmented
Shows the combined edge density and SAR information alongside the segmented land cover classification:
- Blue: Water
- Green: Terrain
- Red: Urban areas

### 4. Urban Density & Urban Centers
Visualizes the urban density distribution and highlights urban centers (areas with density above the `urban_center_threshold`).

### 5. Urban Density Gradient
Plots how density changes with distance from urban centers:
- Calculates Alfa (slope of density gradient) in units per km
- Shows the distance at which density reaches a target value
- Provides MSE (Mean Squared Error) of the gradient fit

## Usage Example

```python
# Input paths
optical_image_path = 'data/gdansk_optical_1.jpg'
sar_image_path = 'data/gdansk_sar_1.jpg'

# Run the analysis
# ... (main code here)

# Results are saved in the data folder:
# - data/gdansk_original_sobel.png
# - data/gdansk_density_sar.png
# - data/gdansk_combined_segmented.png
# - data/gdansk_urban_analysis.png
# - data/gdansk_urban_density_gradient.png
```

## Dependencies

- OpenCV (cv2)
- NumPy
- Matplotlib
- SciPy

## License

[MIT License](LICENSE)
