Hi I am Pete,
I like science and technology

# ColabCode

A collection of Google Colab notebooks covering physics simulations, maths,
data analysis and image/video processing. Each notebook has an **Open in Colab**
badge at the top, so it can be run straight from GitHub without installing anything locally.

## Notebooks

### Physics: pendulums

| Notebook | What it does |
|----------|--------------|
| [Galileos_Pendulum_A01_DO_NOT_ALTER.ipynb](Galileos_Pendulum_A01_DO_NOT_ALTER.ipynb) | The reference version (do not edit). Derives the equation of motion of a simple pendulum from the Lagrangian with SymPy, solves it numerically with SciPy `odeint`, and animates a row of 16 pendulums of different lengths as a "pendulum wave". |
| [Galileo's_Wave_Interactive_Pendulum_A02_y_dimension_small_angle.ipynb](Galileo's_Wave_Interactive_Pendulum_A02_y_dimension_small_angle.ipynb) | Variation on A01 using small starting angles (π/6) and pendulum lengths chosen to give a classic pendulum-wave pattern, animated with Matplotlib. |
| [Variation_on_Galileo's_Wave_Pendulum_TimeDelay_Variable_lengths_and_g.ipynb](Variation_on_Galileo's_Wave_Pendulum_TimeDelay_Variable_lengths_and_g.ipynb) | Further variation adding time delays between pendulums and letting the acceleration `g` vary with pendulum length. Includes the period formula T = 2π√(L/g). |

Based on work by Mr P. Solver on YouTube.

### Animation: bell ringing

These notebooks build a video of a church bell being "rung up", swinging through
increasing angles, by compositing two SVG images (the frame and the bell in its
wheel), rendering each frame to PNG with `cairosvg` and joining them into an MP4 with OpenCV.

| Notebook | What it does |
|----------|--------------|
| [Cld_FIXED_Aug2026_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas.ipynb](Cld_FIXED_Aug2026_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas.ipynb) | **Use this one.** Fixed version: clears old frames before each run so the video no longer jumps at the end, and keeps all settings (angles, frame rate, pause, scale, pivot) in one config cell. |
| [Aug2026_TEST_for_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas_ipynb.ipynb](Aug2026_TEST_for_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas_ipynb.ipynb) | Original test version that the fixed notebook is based on. Adds a pause at the end of each swing. |
| [Cld2_Aug2026_TEST_for_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas.ipynb](Cld2_Aug2026_TEST_for_WORKS_Ringing_Up_VIDEO_v6_Transparent_Bell_Swinging_Dual_canvas.ipynb) | Intermediate test version. |

Needs `FrameOnly.svg` and `BellinWheel.svg` in `My Drive/Images_png_svg_jpg_etc` on Google Drive.
The finished video is saved as `video_v6.mp4`.

### Maths

| Notebook | What it does |
|----------|--------------|
| [Primes_plus.ipynb](Primes_plus.ipynb) | Finds all primes up to a number and the first *n* primes, plots them against a linear trend, and plots the gaps between consecutive primes as a line chart and histogram. Also includes a factorial routine. |
| [Volume_of_Cone_vs_Theta.ipynb](Volume_of_Cone_vs_Theta.ipynb) | Cutting a sector of angle θ out of a disc and rolling the rest into a cone: plots the cone's volume against θ and finds the angle that gives the largest volume. |
| [Azimuth_and_distance.ipynb](Azimuth_and_distance.ipynb) | Asks for two points (e.g. UTM coordinates), plots them, and calculates the distance and azimuth (bearing) between them, shown on a polar plot. |

### Data analysis

| Notebook | What it does |
|----------|--------------|
| [3D_Earthquake_clustering1.ipynb](3D_Earthquake_clustering1.ipynb) | Exercise using the R `quakes` dataset (earthquakes near Fiji, via `pydataset`). Plots locations sized by magnitude and coloured by depth, then clusters them with scikit-learn KMeans, in 2D (lat/long) and 3D (with depth), with and without scaling. Includes interactive Plotly 3D plots. |
| [3D_Earthquake_clustering1_USGSdatafromSEAsia.ipynb](3D_Earthquake_clustering1_USGSdatafromSEAsia.ipynb) | The same analysis on real USGS data: 689 earthquakes of magnitude 5.5 and above across SE Asia, 2016 to 2026. Plots locations sized by magnitude and coloured by depth, clusters them with KMeans (fixed `random_state`, so results repeat) on lat/long and on lat/long/depth, and shows them in static and interactive Plotly 3D plots. Reads [data/EarthQuakeData_SE_Asia.csv](data/EarthQuakeData_SE_Asia.csv), so it needs no Google Drive. |

### Astronomy: image conversion

| Notebook | What it does |
|----------|--------------|
| [mp4_to_fits.ipynb](mp4_to_fits.ipynb) | Converts an MP4 video (e.g. a solar timelapse from a SeeStar telescope) into a series of FITS (`.fit`) files that astronomy software can import. Frames are extracted with MoviePy, split into colour channels and written with Astropy. Note that frames pass through JPEG, which loses some quality. |

## Running locally

The Colab badge is the quickest way in. To run a notebook on your own machine
instead (Python 3.9 or newer):

```bash
git clone -b TestingBranch https://github.com/CharalapML/ColabCode.git
cd ColabCode
python3 -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

`requirements.txt` covers the earthquake notebooks. The other notebooks may need
extra packages (for example `sympy`, `scipy`, `cairosvg`, `opencv-python`,
`moviepy`, `astropy`) and some read files from Google Drive, so they are best run in Colab.

## Data

`data/EarthQuakeData_SE_Asia.csv` was exported from the
[USGS Earthquake Catalog](https://earthquake.usgs.gov/earthquakes/search/).
USGS data is in the public domain.
