# Image Processing Project 1

A Python and Jupyter Notebook project for five classical image processing exercises: image enhancement, denoising, edge detection and region segmentation, background removal, and retinal blood vessel extraction. Each exercise includes its notebook, input data, and generated outputs.

> This repository contains coursework and example implementations. See `Project1.pdf` for the original assignment and `HW1_Report_Ehsan_Shafiei_40561321002.pdf` for the project report.

## Project layout

```text
.
├── Project1.pdf
├── HW1_Report_Ehsan_Shafiei_40561321002.pdf
├── 1 Image Enhancement/
│   ├── Input/
│   ├── outputs/
│   └── solution.ipynb
├── 2 Denoising/
│   ├── Input/data/
│   ├── outputs/
│   ├── requirements.txt
│   └── solution.ipynb
├── 3 Edge Detection and Region Segmentation/
│   ├── Input/                # Images and GroundTruth annotations
│   ├── outputs/
│   └── solution.ipynb
├── 4 Remove Background/
│   ├── Input/
│   ├── outputs/
│   ├── seeds.json
│   └── solution.ipynb
└── 5 Region Extraction/
    ├── Input/                # Retinal images and reference masks
    ├── outputs/
    └── solution.ipynb
```

## Exercises

1. **Image enhancement** — compare contrast stretching, histogram equalization, and gamma correction, with visual and statistical summaries.
2. **Denoising** — compare spatial filters on Gaussian and salt-and-pepper noise using PSNR and regional analysis.
3. **Edge detection and region segmentation** — evaluate Sobel, Prewitt, Laplacian, and LoG edge detectors, then compare Otsu, adaptive thresholding, and K-means segmentation against human annotations.
4. **Background removal** — extract foreground objects with OpenCV GrabCut; inspect masks and transparent outputs. The notebook also includes an optional interactive seed selection workflow.
5. **Retinal vessel extraction** — compare channel/preprocessing choices and classical segmentation methods against manual vessel masks within the training region.

## Requirements

Python 3.10 or newer and Jupyter Notebook or JupyterLab are recommended. Install the shared packages from the project root:

```bash
python -m pip install numpy opencv-python matplotlib pandas jupyter
```

Exercise 4's optional interactive desktop interface also uses PyQt5:

```bash
python -m pip install PyQt5
```

Exercise 2 includes a `requirements.txt` with its dependencies; from that exercise folder, you can install them with:

```bash
python -m pip install -r "2 Denoising/requirements.txt"
```

## Run a notebook

Start Jupyter from the repository root so the notebooks can locate the project folders:

```bash
jupyter lab
```

Then open the `solution.ipynb` in the exercise you want to run and execute its cells in order. Results are written to that exercise's `outputs/` directory. Some notebooks have optional interactive cells; their README files explain how to use them.

## Notes

- Keep each exercise's `Input/` data alongside its notebook; notebooks use these relative project paths.
- Generated outputs are included as part of the current project results.
- The datasets and assignment documents are included for educational use as supplied with the coursework. Check the applicable course and dataset terms before redistributing them publicly.
