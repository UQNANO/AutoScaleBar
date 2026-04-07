# SEM Scale Bar Tool (Auto SSC)

A lightweight, browser-based tool for adding **accurate scale bars to SEM images**, with automatic calibration using `.ssc` metadata files.

Designed for **nanofabrication, SEM metrology, and electron beam lithography (EBL)** workflows, this tool enables fast, reliable figure generation without manual calibration.

---

## 🚀 Overview

SEM images are often exported without embedded, trustworthy pixel calibration. This tool solves that problem by:

* Automatically extracting **true pixel size** from `.ssc` files
* Correctly interpreting **Step Size** (the physically meaningful calibration)
* Applying calibration instantly to matching images
* Rendering accurate, publication-ready **scale bars**

All processing is done locally in your browser — **no installation required**.

---

## 🔬 Key Features

### 🧠 Automatic Pixel Calibration

* Parses `.ssc` metadata files
* Correctly prioritises calibration sources:

  ```
  Step Size > XStep/YStep > PixelSize > Resolution > HFW
  ```
* Handles unit conversion:

  * m → nm
  * mm → nm
  * µm → nm

### 🔗 Automatic File Matching

* Zero-config pairing of:

  ```
  sample.tif ↔ sample.ssc
  ```
* Also supports matching via `.ssc` internal reference:

  ```
  Bitmap=sample.tif
  ```

### 🖼 Broad Image Support

Compatible with common SEM export formats:

* PNG
* JPG / JPEG
* BMP (common in SEM systems)
* TIFF / TIF (microscope exports)
* WebP

### 📏 Accurate Scale Bar Rendering

* Uses true nm/pixel calibration
* Real-time overlay
* Suitable for:

  * publications
  * reports
  * lab documentation

### ⚡ Batch-Friendly Workflow

* Drag-and-drop multiple files
* Works regardless of order:

  * load `.ssc` first ✅
  * load images first ✅
* Auto-updates calibration dynamically

---

## 🧠 How It Works

1. Drag SEM images and `.ssc` files into the browser
2. Tool parses `.ssc` metadata:

   ```
   Step Size = 0.0025 µm
   ```
3. Converts to:

   ```
   2.5 nm/pixel
   ```
4. Matches `.ssc` to image
5. Applies calibration automatically
6. Renders scale bar

---

## 📂 Example Workflow

Drop files together:

```
sample1.tif
sample1.ssc
sample2.bmp
sample2.ssc
```

Result:

* Pixel size detected automatically
* Scale bars rendered instantly
* No manual input required

---

## 🔬 Calibration Example

From `.ssc` file:

```
Step Size=0.0025µm
```

Converted:

```
0.0025 µm = 2.5 nm/pixel
```

This value is used directly for scale bar computation.

---

## ⚠️ Important Notes

### 1. Step Size is Critical

Many SEM systems include multiple calibration fields, but:

* **Step Size = physically correct pixel spacing**
* PixelSize may be:

  * display-scaled
  * software-dependent
  * unreliable

This tool always prioritises **Step Size** when available.

---

### 2. Encoding Handling

`.ssc` files often use Windows-1252 encoding, especially for:

```
µm
```

The tool correctly handles this to avoid parsing errors.

---

### 3. Matching Behaviour

Matching priority:

1. Filename match (preferred)
2. `.ssc` internal reference (`Bitmap=`)

Example:

```
ARPsi_0000.tif
ARPsi_0000.ssc
```

---

### 4. Limitations

* Proprietary formats (e.g. DM3, vendor-specific raw formats) are not supported directly
* TIFF decoding depends on browser capabilities (works in modern Chrome/Edge)

---

## 🛠 Installation

No installation required.

### Option 1 — Direct Use

Open the HTML file in a browser:

```
double-click → open in Chrome or Edge
```

### Option 2 — Local Server (recommended)

```bash
python -m http.server
```

Then open:

```
http://localhost:8000
```

---

## 🎯 Use Cases

* SEM imaging and documentation
* Nanofabrication process verification
* EBL pattern inspection
* CD measurement visualisation
* Publication figure preparation
* Cleanroom workflows

---

## 🔧 Technical Details

### Calibration Logic

Pixel size is extracted and normalised to:

```
nm/pixel
```

### Supported `.ssc` Fields

* Step Size
* XStep / YStep
* PixelSize
* Resolution
* HFW (computed fallback)

---

## 🚀 Roadmap

Planned enhancements:

* 📊 CSV export (filename, pixel size, metadata)
* 🧠 SSC mismatch detection
* 📂 Folder-level batch import
* 🔍 Metadata overlay (kV, WD, magnification)
* 🎛 Adjustable scale bar styles

---

## 🤝 Contributing

Contributions are welcome, especially for:

* Additional SEM format support
* UI improvements
* Metadata parsing enhancements

---

## 📜 License

GNU GPL-3.0

---

## 👤 Author

Developed for advanced nanofabrication workflows at:

**Centre for Microscopy & Microanalysis (CMM)**
The University of Queensland

---

## 💡 Acknowledgement

This tool supports SEM/EBL users working with:

* Raith EBPG systems
* Raith eLINE systems
* Photonics and quantum fabrication workflows
* Automated metrology pipelines

---

## 📬 Feedback

If you encounter issues with specific SEM formats or `.ssc` variations, please open an issue or share a sample file.

---
