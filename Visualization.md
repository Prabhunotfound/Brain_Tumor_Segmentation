# Brain Tumor Image Segmentation — Model Comparison

> A comprehensive visual comparison of **UNet**, **WaveUNet v1**, **WaveUNet v2**, and **TransUNet** across training, evaluation, and interpretability metrics.

---

## Table of Contents

- [Brain Tumor Image Segmentation — Model Comparison](#brain-tumor-image-segmentation--model-comparison)
  - [Table of Contents](#table-of-contents)
  - [Model Architectures](#model-architectures)
  - [Dataset Overview (EDA)](#dataset-overview-eda)
    - [Sample Grid](#sample-grid)
    - [Class Imbalance \& Boundary Analysis](#class-imbalance--boundary-analysis)
  - [Preprocessing](#preprocessing)
  - [Training History](#training-history)
  - [Training Metrics](#training-metrics)
  - [Quantitative Evaluation — HD95 vs Dice](#quantitative-evaluation--hd95-vs-dice)
  - [Random Prediction Samples](#random-prediction-samples)
  - [Failure Cases](#failure-cases)
  - [Interpretability — GradCAM](#interpretability--gradcam)
  - [Occlusion Sensitivity](#occlusion-sensitivity)
  - [WaveUNet Architecture Analysis](#waveunet-architecture-analysis)

---
 
## Model Architectures
 
> High-level architecture diagrams for the two novel models proposed in this work.
 
<p align="center">
  <b> WaveUNet</b><br><br>
  <img src="Visualization/model/waveunet.png" width="75%" alt="WaveUNet Architecture"/>
  <br><br><br>
  <b> TransUNet</b><br><br>
  <img src="Visualization/model/transunet.png" width="75%" alt="TransUNet Architecture"/>
</p>


---

## Dataset Overview (EDA)

> Exploratory analysis of the dataset before training — class distribution, boundary characteristics, intensity profiles, and sample diversity.

<br>

### Sample Grid

<p align="center">
  <img src="Visualization/EDA/eda_sample_grid.png" width="80%" alt="EDA Sample Grid"/>
</p>

<br>

### Class Imbalance & Boundary Analysis

<p align="center">
  <img src="Visualization/EDA/eda_class_imbalance.png" width="70%" alt="Class Imbalance"/>
  <br><br>
  <img src="Visualization/EDA/eda_boundary_samples.png" width="70%" alt="Boundary Samples"/>
  <br><br>
  <img src="Visualization/EDA/eda_intensity_distribution.png" width="70%" alt="Intensity Distribution"/>
</p>

---

## Preprocessing

> Input normalization and augmentation pipeline applied before feeding data to all models.

<p align="center">
  <img src="Visualization/Preprocessing/sample.png" width="75%" alt="Preprocessing Sample"/>
</p>

---

## Training History

> Loss and metric curves over epochs for each model. Useful for diagnosing convergence, overfitting, or instability.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/train_hist/unet.png" width="100%" alt="UNet Training History"/>
    </td>
    <td align="center">
      <img src="Visualization/train_hist/wave1.png" width="100%" alt="WaveUNet v1 Training History"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/train_hist/wave2.png" width="100%" alt="WaveUNet v2 Training History"/>
    </td>
    <td align="center">
      <img src="Visualization/train_hist/trans.png" width="100%" alt="TransUNet Training History"/>
    </td>
  </tr>
</table>

---

## Training Metrics

> Final training metric comparisons across WaveUNet variants and TransUNet. Covers Dice, loss, and other tracked indicators.

<table>
  <tr>
    <th align="center"> WaveUNet v1</th>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/training_metrics/wave1.png" width="100%" alt="WaveUNet v1 Metrics"/>
    </td>
    <td align="center">
      <img src="Visualization/training_metrics/wave2.png" width="100%" alt="WaveUNet v2 Metrics"/>
    </td>
    <td align="center">
      <img src="Visualization/training_metrics/trans.png" width="100%" alt="TransUNet Metrics"/>
    </td>
  </tr>
</table>

---

## Quantitative Evaluation — HD95 vs Dice

> Scatter/curve plots comparing **Hausdorff Distance (95th percentile)** against **Dice Coefficient** for each model. Lower HD95 + Higher Dice = better boundary and overlap performance.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/hd95vsdice/unet.png" width="100%" alt="UNet HD95 vs Dice"/>
    </td>
    <td align="center">
      <img src="Visualization/hd95vsdice/wave1.png" width="100%" alt="WaveUNet v1 HD95 vs Dice"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/hd95vsdice/wave2.png" width="100%" alt="WaveUNet v2 HD95 vs Dice"/>
    </td>
    <td align="center">
      <img src="Visualization/hd95vsdice/trans.png" width="100%" alt="TransUNet HD95 vs Dice"/>
    </td>
  </tr>
</table>

---

## Random Prediction Samples

> Randomly selected test-set predictions — showing input image, ground truth mask, and predicted segmentation side-by-side for each model.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/random_samples/unet.png" width="100%" alt="UNet Predictions"/>
    </td>
    <td align="center">
      <img src="Visualization/random_samples/wave1.png" width="100%" alt="WaveUNet v1 Predictions"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/random_samples/wave2.png" width="100%" alt="WaveUNet v2 Predictions"/>
    </td>
    <td align="center">
      <img src="Visualization/random_samples/transunet.png" width="100%" alt="TransUNet Predictions"/>
    </td>
  </tr>
</table>

---

## Failure Cases

> Worst-performing predictions per model — highlights common failure modes such as boundary leakage, false positives, or missed small regions.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/fail/unet.png" width="100%" alt="UNet Failures"/>
    </td>
    <td align="center">
      <img src="Visualization/fail/wave1.png" width="100%" alt="WaveUNet v1 Failures"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/fail/wave2.png" width="100%" alt="WaveUNet v2 Failures"/>
    </td>
    <td align="center">
      <img src="Visualization/fail/tranunet.png" width="100%" alt="TransUNet Failures"/>
    </td>
  </tr>
</table>

---

## Interpretability — GradCAM

> Gradient-weighted Class Activation Maps showing **which regions** each model focuses on during prediction. Brighter areas = higher activation.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/gradcam/unet.png" width="100%" alt="UNet GradCAM"/>
    </td>
    <td align="center">
      <img src="Visualization/gradcam/wave1.png" width="100%" alt="WaveUNet v1 GradCAM"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/gradcam/wave2.png" width="100%" alt="WaveUNet v2 GradCAM"/>
    </td>
    <td align="center">
      <img src="Visualization/gradcam/trans.png" width="100%" alt="TransUNet GradCAM"/>
    </td>
  </tr>
</table>

---

## Occlusion Sensitivity

> Occlusion maps reveal model robustness — patches of input are systematically masked and the drop in prediction confidence is measured. High sensitivity = model relies heavily on that region.

<table>
  <tr>
    <th align="center"> UNet</th>
    <th align="center"> WaveUNet v1</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/occulsion/unet.png" width="100%" alt="UNet Occlusion"/>
    </td>
    <td align="center">
      <img src="Visualization/occulsion/wave1.png" width="100%" alt="WaveUNet v1 Occlusion"/>
    </td>
  </tr>
  <tr>
    <th align="center"> WaveUNet v2</th>
    <th align="center"> TransUNet</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/occulsion/wave2.png" width="100%" alt="WaveUNet v2 Occlusion"/>
    </td>
    <td align="center">
      <img src="Visualization/occulsion/trans.png" width="100%" alt="TransUNet Occlusion"/>
    </td>
  </tr>
</table>

---

## WaveUNet Architecture Analysis

> Detailed internal analysis specific to the WaveUNet variants — comparing how v1 and v2 differ in feature extraction and wavelet decomposition behavior.

<table>
  <tr>
    <th align="center"> WaveUNet v1</th>
    <th align="center"> WaveUNet v2</th>
  </tr>
  <tr>
    <td align="center">
      <img src="Visualization/wave_unet/wave1.png" width="100%" alt="WaveUNet v1 Analysis"/>
    </td>
    <td align="center">
      <img src="Visualization/wave_unet/wave2.png" width="100%" alt="WaveUNet v2 Analysis"/>
    </td>
  </tr>
</table>
