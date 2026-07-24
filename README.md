# ECGMatcher

**ECGMatcher: Multi-Lead Morphological Matching for ECG Image Abnormality Screening**

ECGMatcher is a research software platform for morphological matching and abnormality screening of image-based or digitized multi-lead electrocardiograms. The system integrates standard-template construction, patient ECG signal reconstruction, curve-oriented semantic segmentation, contour-overlap analysis, key-waveform morphology comparison, similarity assessment, and abnormality localization within a unified graphical user interface, thereby providing quantitative, localized, and reviewable multi-lead morphological evidence.

> Important Notice: ECGMatcher is intended solely for scientific research, education, and non-commercial evaluation. It is not a medical device and must not be used as the sole basis for clinical diagnosis, emergency management, medication selection, or treatment decision-making.

<p align="center">
  <img
    src="./ECGMatcher%20GUI.jpg"
    alt="ECGMatcher graphical user interface showing patient input, standard-template configuration, multistage ECG analysis, quantitative metrics, and runtime progress"
    width="100%"
  >
</p>

<p align="center">
  <em>
    Figure 1. Graphical user interface of ECGMatcher, integrating patient data input,
    standard-template configuration, ECG signal reconstruction, waveform semantic
    segmentation, contour-overlap analysis, key-waveform morphology comparison,
    similarity assessment, and abnormality localization.
  </em>
</p>

## 1. Distribution Format
The current public release is a portable 64-bit Windows application:
```text
ECGMatcher_Windows_x64_Protected_v1.0.0.zip
└─ ECGMatcher/
   ├─ ECGMatcher.exe
   ├─ _internal/
   ├─ 10140238.csv
   ├─ standard img/
   ├─ standard waveform/
   ├─ standard waveform_masks/
   └─ ECG Datasets/
```

`ECGMatcher.exe` and the `_internal` directory must always remain in the same folder. Do not copy or distribute the executable file alone.
The core algorithms have been compiled into native Windows extension modules (`.pyd`). The complete source code is not currently publicly available because the methodology remains under active development and intellectual-property protection.

## 2. Principal Features
* Construction and reuse of standard 12-lead ECG templates
* Patient ECG waveform reconstruction with PNG and PDF output
* ECG waveform semantic segmentation
* Template-to-patient contour alignment and overlap analysis
* Morphological comparison of the P wave, QRS complex, T wave, and ST-T segment
* Lead-level and localized temporal abnormality detection
* Visualization of fused abnormality scores, fused similarity, and the most abnormal lead
* Reuse of existing results and on-demand processing of missing cases
* Graphical user interface available in Chinese, English, and Russian
* Support for LUDB, PTB-XL, and other standardized 12-lead ECG datasets in CSV format

## 3. System Requirements
* 64-bit Windows 10 or Windows 11
* Recommended memory: 16 GB or more
* Recommended available disk space: at least 20 GB
* GPU support is optional; a compatible NVIDIA GPU may improve segmentation-inference efficiency
* No separate Python installation is required on the target computer

## 4. Quick Start
1. Download `ECGMatcher_Windows_x64_Protected_v1.0.0.zip`.
2. Fully extract the archive. Do not run the application directly from within the compressed file.
3. Double-click `ECGMatcher/ECGMatcher.exe`.
4. Under **Patient Input Path**, select either a single 12-lead CSV file or a folder containing CSV files.
5. Under **Standard Template Path**, select a standard-template image folder, a standard-template CSV file, or a standard-mask folder.
6. Click **Run ECG Matcher** and wait for reconstruction, segmentation, morphological comparison, and abnormality localization to complete.
7. Use the **Current Case** and **Current Lead** selectors to review the results.
For complete operating instructions, see:
`docs/ECGMatcher User Manual v1.0.0.docx`

## 5. Input Data
A wide-format 12-lead CSV file is recommended, using the following canonical lead order:
`I, II, III, aVR, aVL, aVF, V1, V2, V3, V4, V5, V6`
An optional time column, such as `time`, `t`, or `sec`, may also be included. Each CSV file should preferably correspond to a single case and use a de-identified case identifier.

## 6. Output Results
The software primarily generates:
* Single-lead and complete 12-lead reconstructed ECG images
* Waveform foreground masks and semantic-segmentation results
* Difference heatmaps and contour-overlap maps
* Key-waveform abnormality overlays
* Deviation-fusion and localized abnormality results
* Lead-level similarity scores, abnormality scores, and waveform-segment summaries
* Runtime logs and stage-specific metric files

The principal interface outputs include:

```text
Raw Input
Segmentation
Difference Heatmap
Overlap Map
Deviation Fusion
Keywave Abnormal Overlay
Fusion Abnormal Score
Fusion Similarity
Mean Vertical Deviation
Most Abnormal Lead
```

## 7. Summary of Experimental Results
The current manuscript reports the following results:
| Task                  | Dataset        | Principal Results                                        |
| --------------------- | -------------- | -------------------------------------------------------- |
| Signal reconstruction | LUDB           | SSIM: 0.9196, PSNR: 28.0256, PCC: 0.9956                 |
| Signal reconstruction | PTB-XL         | SSIM: 0.9308, PSNR: 29.0478, PCC: 0.9955                 |
| Waveform segmentation | LUDB           | IoU: 0.8681, F1-score: 0.9294                            |
| Waveform segmentation | PTB-XL         | IoU: 0.8676, F1-score: 0.9291                            |
| Model efficiency      | PTB-XL setting | 0.03M parameters, 1.05G FLOPs, 9.48 ms/image, 105.46 FPS |

## 8. Datasets
The research evaluation primarily uses the following publicly available datasets:

* LUDB: 200 standard 12-lead ECG recordings
  Official dataset page: https://physionet.org/content/ludb/1.0.1/  
  Direct ZIP download: https://physionet.org/content/ludb/get-zip/1.0.1/
  
* PTB-XL: 2,203 recordings used for training and testing in the present study
  Official dataset page: https://physionet.org/content/ptb-xl/1.0.3/  
  Direct ZIP download: https://physionet.org/content/ptb-xl/get-zip/1.0.3/
  
The original datasets are not redistributed through this repository. Users should obtain them from their official sources and comply with the corresponding licensing and citation requirements.

## 9. License
The original ECGMatcher components are governed by a custom Research, Education, and Non-Commercial Evaluation License. See [LICENSE.txt].
Third-party components remain subject to their respective original licenses. See [THIRD_PARTY_NOTICES.md].

## 10. Clinical Use Limitations
ECGMatcher is intended for research analysis, algorithm validation, abnormality-screening support, and the reuse of historical image-based ECG records. Its outputs must not replace a physician’s comprehensive interpretation of the original electrocardiogram, clinical symptoms, medical history, and other examination findings. See [DISCLAIMER.md].

## 11. Contact Information
* Repository: [https://github.com/Intelligent-Imaging-Center/ecgmatcher]
* Contact email: [luzw999@stu.xidian.edu.cn]





