# Image Denoising with Spatial Filters

## Objective

The objective of this assignment is to study how different spatial filters remove noise and how their parameters affect image details. You will compare Mean, Median and Gaussian filters on images corrupted by Gaussian and Salt-and-Pepper noise. You will also examine why a high global PSNR does not always mean that edges and textures have been preserved well.

All images are 8-bit grayscale images with intensity values in the range `[0, 255]`.

## Dataset

The `data/clean` directory contains five reference images.

| Image | Main characteristic |
| --- | --- |
| `house.png` | Smooth regions and geometric edges |
| `mandrill.png` | Dense textures and fine details |
| `peppers.png` | Smooth intensity changes and curved boundaries |
| `resolution_chart.png` | Thin lines and high-contrast structures |
| `synthetic_regions.png` | Controlled smooth, edge, and texture regions |

For every clean image, four corrupted versions are provided in `data/noisy`.

| Noise version | Parameters |
| --- | --- |
| Gaussian | Mean 0 and standard deviation 10 |
| Gaussian | Mean 0 and standard deviation 25 |
| Salt-and-Pepper | Total density 0.05 |
| Salt-and-Pepper | Total density 0.15 |

The file `data/base_manifest.csv` maps every noisy image to its clean reference and records the noise parameters and random seed.

## Required filters

Apply the following filters to every noisy image.

1. Mean Filter
2. Median Filter
3. Gaussian Filter

For Mean, Median, and Gaussian filters, test at least the following kernel sizes.

```text
3 × 3, 5 × 5, and 7 × 7
```

For the Gaussian Filter, report the value of `sigma`. Use the same evaluation procedure for all filters.

## PSNR evaluation

First calculate the PSNR of each noisy image with respect to its corresponding clean image. Then calculate the PSNR of every filtered output with respect to the same clean image.

\[
MSE=\frac{1}{MN}\sum_{x=1}^{M}\sum_{y=1}^{N}
\left[f(x,y)-\hat f(x,y)\right]^2
\]

\[
PSNR=10\log_{10}\left(\frac{255^2}{MSE}\right)
\]

Convert both images to a floating-point data type before subtraction. Do not calculate PSNR between a noisy image and a filtered image. The reference must always be the clean image.

Record the results in `results_template.csv`. Each row must identify the clean image, noisy image, noise type, filter, filter parameters, noisy-image PSNR, filtered-output PSNR, PSNR improvement, and runtime.

## Region-based analysis

For `synthetic_regions.png`, calculate PSNR for the complete image and separately for the following regions.

- Smooth region using `data/roi_masks/smooth.png`
- Edge region using `data/roi_masks/edge.png`
- Texture region using `data/roi_masks/texture.png`

White pixels in a mask identify the pixels included in the regional PSNR calculation. Black pixels are ignored. The masks are used only for evaluation. The filters must still be applied to the complete noisy image.

## Creative method

You may propose an additional denoising strategy for bonus credit. 

## Required submission

- Complete source code
- Completed `results.csv`
- Selected output images and identical comparison crops
- Regional PSNR table for the synthetic image
- Discussion of the strengths and weaknesses of all three required filters

## Included files

```text
Base_Image_Denoising_Homework/
├── README.md
├── PREVIEW_BASE.png
├── requirements.txt
├── results_template.csv
├── data/
│   ├── clean/
│   ├── noisy/
│   ├── roi_masks/
│   └── base_manifest.csv
```

Install the Python dependencies with the following command.

```bash
python -m pip install -r requirements.txt
```



---

## Answer notebook

# Exercise 2 - Image Denoising

Open solution.ipynb and run the workflow from top to bottom. It compares Mean, Median, Weighted Median, Gaussian, and Morphology filters using 3x3, 5x5, and 7x7 kernels against clean references. Morphology uses an elliptical structuring element and averages grayscale opening and closing.

The notebook reports PSNR and runtime for every configuration, evaluates synthetic-region ROI masks, saves every filtered image, and creates one consistent-crop montage per noisy input. Each montage shows the clean and noisy images, every method/kernel output, and the best-PSNR result as the final panel. Best is selected by full-image PSNR against that input clean reference.

Generated files under outputs/: results.csv (all evaluations), regional_psnr.csv (full and ROI PSNR), all_filter_outputs/ (all filtered images), selected_outputs/ (best result per input), and comparison_crops/ (all-method montages with best last).
