# Satellite Imagery Urban Analysis

A Python toolkit for analyzing urban density patterns from satellite imagery using optical and SAR data. This tool segments land cover types, measures urban density gradients, and visualizes spatial patterns to quantify urban structure.

For comprehensive details and methodology, please refer to our research paper:
[Urban Density Analysis from Satellite Imagery: A Combined Optical-SAR Approach](https://arxiv.org/abs/2504.11128)

## Overview

This project processes satellite imagery to:
1. Detect edges and create density maps from optical imagery
2. Combine optical and SAR data for improved urban detection
3. Segment images into water, terrain, and urban areas
4. Calculate urban density gradients from city centers
5. Generate visualizations for urban analysis

## Folder Structure

The project uses the following folder structure:
- `input_data/`: Contains input satellite imagery files
- `output_data/`: Stores all generated visualizations and analysis results

## Input Data

The tool uses two primary inputs:
- Optical satellite imagery (e.g., `input_data/gdansk_optical_1.jpg`)
- SAR (Synthetic Aperture Radar) imagery (e.g., `input_data/gdansk_sar_1.jpg`)

Satellite data can be obtained from the [Copernicus Data Space](https://browser.dataspace.copernicus.eu/).

## Configuration Parameters

Key parameters that can be adjusted:

```python
# Resolution settings
satellite_pixel_resolution = 15  # 15m per pixel

# Scale intervals for plots
image_x_tick_interval = 5000     # 5km intervals for main maps
gradient_x_tick_interval = 1000  # 1km intervals for gradient plots
```

### Automatic Threshold Calculation

The latest version of the tool automatically calculates the following thresholds using histogram decomposition:

- `water_threshold`: Threshold between water and terrain (calculated from intersection of Gaussian components)
- `urban_threshold`: Threshold between terrain and urban areas (calculated from intersection of Gaussian components)
- `urban_center_threshold`: Threshold for urban centers (calculated from urban density analysis)

This eliminates the need for manual threshold adjustment and makes the analysis more adaptive to different satellite imagery inputs.

## Output Visualizations

The tool generates several visualizations in the `output_data/` folder:

### 1. Original Image & Sobel Edge Detection
- `{base_name}_original.png`: The original optical satellite image
- `{base_name}_sobel.png`: Sobel edge detection results highlighting urban boundaries and structures

### 2. Edge Density & SAR
- `{base_name}_density.png`: The derived edge density map (0-1 range)
- `{base_name}_sar.png`: The normalized SAR image (0-1 range)

### 3. Combined & Segmented
- `{base_name}_combined.png`: Combined edge density and SAR information
- `{base_name}_segmented.png`: Segmented land cover classification:
  - Blue: Water
  - Green: Terrain
  - Red: Urban areas

### 4. Urban Density & Urban Centers
- `{base_name}_urban_density.png`: Urban density distribution
- `{base_name}_urban_centers.png`: Urban centers (areas with density above the automatically calculated `urban_center_threshold`)

### 5. Density Gradients
- `{base_name}_urban_density_gradient.png`: Plot of density change with distance from urban centers
- `{base_name}_enhanced_density_gradient.png`: Enhanced density gradient with statistical analysis:
  - Calculates Alfa (slope of density gradient) in units per km
  - Shows the distance at which density reaches a target value
  - Provides MSE (Mean Squared Error) of the gradient fit

## Usage Example

```python
# Define folder structure
input_dir = 'input_data'
output_dir = 'output_data'

# Input paths
optical_image_path = os.path.join(input_dir, 'Malbork_2024-10-01-00_00_2024-10-01-23_59_Sentinel-2_Quarterly_Mosaics_True_Color_Cloudless.jpg')
sar_image_path = os.path.join(input_dir, 'Malbork_2025-04-08-00_00_2025-04-08-23_59_Sentinel-1_IW_VV+VH_VV_-_decibel_gamma0.jpg')

# Run the analysis
# ... (main code here)

# Results are saved in the output_data folder with the base name from the input file
```

## Dependencies

- OpenCV (cv2)
- NumPy
- Matplotlib
- SciPy
- scikit-image
- scikit-learn
- networkx

## License

[MIT License](LICENSE)
