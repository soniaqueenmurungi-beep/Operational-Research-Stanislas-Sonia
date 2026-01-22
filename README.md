# Operational-Research-Stanislas-Sonia
Below is a **single, clean README** you can use for **both notebooks**.
It’s written in clear, professional Markdown and explains **what the files do, how they relate, and how to run them**.

You can copy-paste this directly into a `README.md`.

---

# ☀️ Solar Irradiance Analysis and Visualization (CAMS Data)

This project analyzes **clear-sky solar irradiance** using data from the **Copernicus Atmosphere Monitoring Service (CAMS)**.
It downloads irradiance data, processes it into usable formats, and visualizes it through **time series, heatmaps, and geographic maps**.

The project consists of **two Jupyter notebooks**, each with a distinct role.

---

## 📁 Files in this repository

### 1️⃣ `solar detection.ipynb`

**Purpose:**
Data acquisition and preprocessing.

**What this notebook does:**

* Connects to the **Copernicus ADS (Atmosphere Data Store)** using `cdsapi`
* Downloads **CAMS gridded solar radiation** data
* Variables retrieved:

  * **GHI** – Global Horizontal Irradiance
  * **BHI** – Direct Horizontal Irradiance
  * **DHI** – Diffuse Horizontal Irradiance
  * **BNI (DNI)** – Direct Normal Irradiance
* Uses a **user-defined geographic bounding box**
* Opens the NetCDF file correctly using `xarray` + `h5netcdf`
* Converts the dataset into a clean CSV file:

  ```
  output_data_irradiance.csv
  ```

**Key output:**

* `output_data_irradiance.csv`
  (Latitude, longitude, time, and irradiance values)

---

### 2️⃣ `Untitled7 (1).ipynb`

**Purpose:**
Analysis and visualization of the processed irradiance data.

**What this notebook does:**

* Loads `output_data_irradiance.csv`
* Extracts:

  * Time-series at the **nearest grid point**
  * Spatial snapshots at specific times
* Produces:

  * 📈 **Time-series plots** of GHI, DNI (BNI), and DHI
  * 🟦 **Heatmaps** showing spatial variation of irradiance
  * 🗺️ **Real geographic maps** with coastlines and borders
  * 🌈 **Smoothed heatmaps** using interpolation for presentation
  * 🎞️ Optional animated heatmaps over time

**Key visualizations:**

* Daily solar cycles (day–night pattern)
* Spatial irradiance differences across the selected region
* Clear-sky solar availability patterns

---

## 🌍 Data source

* **Dataset:** CAMS Gridded Solar Radiation
* **Provider:** Copernicus Atmosphere Monitoring Service (CAMS)
* **Access:** [https://ads.atmosphere.copernicus.eu](https://ads.atmosphere.copernicus.eu)
* **Sky condition:** Clear-sky
* **Format:** NetCDF (opened with `h5netcdf`)

---

## ⚙️ Requirements

These notebooks are designed to run in **Google Colab** or a local Python environment.

Required libraries:

```bash
pip install cdsapi xarray h5netcdf netcdf4 pandas numpy matplotlib cartopy scipy
```

> ⚠️ Cartopy may require system dependencies if running locally.
> Google Colab is strongly recommended.

---

## 🔐 API configuration (important)

To download CAMS data, you need an **ADS API key**.

In Colab or locally, set:

```python
CDSAPI_URL = "https://ads.atmosphere.copernicus.eu/api"
CDSAPI_KEY = "your-api-key-here"
```

⚠️ **Do not share your API key publicly.**

---

## 📊 Scientific notes

* CAMS data is **gridded model output**, not satellite imagery.
* Heatmaps may appear **blocky** for small regions due to grid resolution.
* Smoothed maps use **interpolation for visualization only** and do not add new physical information.
* BNI is equivalent to **DNI (Direct Normal Irradiance)**.

---

## 🧭 Typical workflow

1. Run **`solar detection.ipynb`**

   * Downloads and prepares the data
2. Run **`Untitled7 (1).ipynb`**

   * Analyzes and visualizes the data

---

## ✅ Summary

This project provides:

* Reliable access to **clear-sky solar irradiance data**
* Correct scientific handling of CAMS NetCDF files
* Clear visualizations in both **time and space**
* A solid foundation for **solar energy, PV, or climate studies**

---

If you want, I can also:

* Rewrite this README for **GitHub publication**
* Add **figures/screenshots references**
* Create a **short project abstract** for a report or thesis
