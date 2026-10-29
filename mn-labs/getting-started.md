# Getting started

← [All labs](README.md)

You need a Windows PC (x86_64) with **Google Chrome or Microsoft Edge**. Firefox and Safari do not work. Plan 15 minutes.

## 1. Download and unzip

1. Click [FeatureFinder-local-v365-windows-x86_64-MN-labs.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/FeatureFinder-local-v365-windows-x86_64-MN-labs.zip) (25 MB). It downloads to your *Downloads* folder.
2. Click [urine_POS.zip](https://github.com/YasinEl/temp_share/releases/download/urine-pos-test-data-2026-10-28/urine_POS.zip) (135 MB). Labs 7 and 8 need other data; their start pages list it.
3. In File Explorer, right-click each zip → **Extract All…** → **Extract**. Do not run the app from inside the zip.
   - The app folder is `FeatureFinder-local-v365-windows-x86_64`. The ten MN Lab dashboards and the spectral
     library are already inside. Worksheets, handouts and any extra files a lab needs are linked on that lab's page.
   - The data folder is `centroided_mzML`: 11 `.mzML` files, `metadata.tsv` and `MD5SUMS.txt`.

## 2. Start the app

1. Open the folder `FeatureFinder-local-v365-windows-x86_64`.
2. Double-click **Start Feature Finder - This Computer** (Windows may hide the `.bat` ending; the type column says
   *Windows Batch File*).
3. If Windows shows *Windows protected your PC*: click **More info** → **Run anyway**. The programs are unsigned, not
   malware.
4. A small black window opens. **Leave it open**: closing it stops the app. Your browser opens at
   `http://127.0.0.1:8000`. If it does not, type that address into Chrome or Edge.
5. You do **not** need to download spectral libraries. The app zip already contains the student library
   (`MN_student_library.mgf`, the 1,785 GNPS spectra these datasets match). The **Setup** tab lists it under
   spectral libraries, ticked. Do not press **Download standard libraries**: that fetches 3.5 GB and makes the
   library search much slower. If the Setup tab says *no libraries installed*, download
   [MN_student_library.mgf](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_student_library.mgf), click **Open libraries folder**, put the file there and
   click **Refresh**.

## 3. Process the files

You are on the **Data Selection** tab.

1. Open the `centroided_mzML` folder in File Explorer, click one `.mzML` file, press **Ctrl+A** (selects all) and drag
   the 11 `.mzML` files onto the drop area of the page (*Drop mzML or Thermo .raw files, or click to browse*).
   Clicking the drop area and choosing the files works too. Do not drag `metadata.tsv` there.
2. Drag **metadata.tsv** onto the **Sample metadata** box of the same tab. It tells the app and the labs which file is
   which patient, the pool or a blank.
3. In the **Engine** dropdown next to **Find Features**, choose **v1 (classic)**. The default, v2, finds a different set
   of features, so your numbers would not match the worksheets.
4. Leave every other setting as it is and click **Find Features**.
5. Wait. Feature finding, then library search, then molecular networking run one after the other (a few minutes on a
   laptop). The tabs **Feature view**, **Library search** and **Molecular Networking** become clickable when their step has
   finished; wait until networking is done before you open a lab.

## 4. Open a lab

1. Click the **All plugins** tab (the plugin gallery).
2. Type `teaching` into the search box (*Search plugins — name, what it does, or category…*). The ten MN Labs appear;
   they are also listed under **Yours**.
3. Click the lab you want to open it.
4. The labs read the sample metadata from the app. If a lab shows **⚠ load sample metadata** at the top right, click it
   and choose `metadata.tsv` from the data folder.

Then follow the steps on the lab's start page. You can switch between the app's tabs and the labs at any time; the
results stay until you process new files.

## If something goes wrong

- **The browser shows nothing / cannot connect:** is the black window still open? Start it again with step 2.
- **A lab says there is no network:** molecular networking has not finished yet, or Find Features was not run.
- **Your numbers differ a lot from the worksheet:** check that Engine was **v1 (classic)** and all 11 files were loaded.
