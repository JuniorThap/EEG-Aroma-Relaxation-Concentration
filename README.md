# EEG Analysis
## How to use
* Collect data from the EEG headset and store it in the following structure:
  ``` bash
  EEG Data/
  ├── SubjectName1/
  │   ├── fif/
  │   │   ├── 0.fif
  │   │   ├── 1.fif
  │   │   ├── 2.fif
  │   │   └── ...
  │   └── other_data_files/
  ├── SubjectName2/
  │   ├── fif/
  │   │   ├── 0.fif
  │   │   ├── 1.fif
  │   │   ├── 2.fif
  │   │   └── ...
  │   └── other_data_files/
  └── ...
  ```
* Run `analysis.ipynb` in "MainPipeline" part. In the main pipeline, the following methods are performed:
  * Map files and store them in `map_data.csv` file.
  * Read the EEG files using `mne.io.Raw(fname)` to convert them into MNE Raw objects.
  * Divide the EEG data into chunks with a fixed `window_size` and `stride`, and pad the chunks to the same size.
  * Filter the chunks into activity bands, such as `Delta (0.5-4 Hz)`, `Theta (4-8 Hz)`, `Alpha (8-13 Hz)`, and `Beta (13-30 Hz)`
  * Calculate GFP (Global Field Power) for each activity band.
  * Calculate the mean of each aroma across all subjects and save the result.

  **Note:** Only the Alpha and Beta bands are used to analyze relaxation and concentration in the final results.
