# Sentinel-2 Land-Cover Classification

## Project Overview
This project uses Sentinel-2 multispectral satellite imagery to perform land-cover classification over a selected area in Kanpur, India.

The workflow combines spectral bands, NDVI, Sentinel-2 Scene Classification Layer (SCL) labels, and a Random Forest classifier to distinguish vegetation, non-vegetated surfaces, and water.

## Study Area
- Location: Kanpur, Uttar Pradesh, India
- Satellite: Sentinel-2
- Product: Sentinel-2 Level-2A
- Acquisition date: 13 December 2025
- Selected scene cloud cover: 3.69%
- Analysis: 512 × 512 pixel crop

## Data and Features
The model uses five features:
- Blue
- Green
- Red
- Near-Infrared (NIR)
- Normalized Difference Vegetation Index (NDVI)

NDVI is calculated as:

NDVI = (NIR - Red) / (NIR + Red)

The Sentinel-2 Scene Classification Layer (SCL) was used to derive three reference classes:
- Vegetation
- Not vegetated
- Water

## Methodology
1. Search and select a Sentinel-2 scene using the Microsoft Planetary Computer STAC API.
2. Read and crop the required multispectral bands.
3. Calculate NDVI.
4. Align SCL labels with the 10 m feature grid.
5. Extract training samples from the three reference classes.
6. Train a Random Forest classifier.
7. Evaluate the model using test accuracy, classification report, and confusion matrix.
8. Visualize the RGB image, NDVI, and predicted land-cover map.

## Results
- Test samples: 4,000
- Overall test accuracy: 95.35%

### Class-wise performance

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Vegetation | 0.82 | 0.81 | 0.82 |
| Not vegetated | 0.97 | 0.98 | 0.97 |
| Water | 0.89 | 0.45 | 0.60 |

The model performs well on non-vegetated surfaces and vegetation. Water detection is weaker, with a recall of 0.45.

## Limitations
- Reference labels are derived from the Sentinel-2 SCL product rather than independent ground-truth observations.
- The three classes are imbalanced, with substantially fewer water samples.
- Built-up areas and bare soil are not separately classified.
- Results are based on one crop and one acquisition date and should not be generalized to all of Kanpur.

## Future Improvements
- Evaluate using independent reference data.
- Improve representation of the water class.
- Extend the workflow to additional dates and locations.
- Develop a more detailed land-cover classification.
- Explore temporal change detection.

## Tools and Libraries
Python, Google Colab, NumPy, Rasterio, Matplotlib, scikit-learn, Sentinel-2, Microsoft Planetary Computer, STAC

## Author
Aditi Singh
