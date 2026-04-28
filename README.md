# TranslocNC

**TranslocNC** is a tool and workflow for segmenting nuclei and quantifying the activity of Cdk2 and Cdk4/6 fluorescence reporters at the single-cell level in fluorescence microscopy images. 

Although the initial focus and provided examples deal with cells expressing Cdk2 and Cdk4/6 reporters (e.g., DHB-Venus and mCherry-KTR), this workflow is broadly applicable. It can assess the nucleus-cytoplasm translocation of any protein that displays homogeneous labeling across the nucleus and cytoplasm, including various Kinase Translocation Reporters (KTR) and similar sensors.

## Features

- **Automated Quantification:** Extracts mean fluorescence intensity in the cytoplasm and nucleus using single-cell segmentation masks.
- **Activity Calculation:** Calculates the cytoplasm-to-nucleus ratio to measure kinase activity.
- **Cross-Reactivity Correction:** Applies an automated correction factor to Cdk4 activity to account for reporter cross-reactivity with Cdk2.
- **Data Export:** Outputs structured results (e.g., nuclear properties and calculated activities) into easy-to-use CSV files.
- **Data Visualization:** Built-in support for generating detailed Swarm plots and Violin plots to analyze the distribution of activities across various experimental conditions.

## How it Works

The workflow measures kinase activity by calculating the ratio of mean fluorescence intensity in the cytoplasm versus the nucleus (**cytoplasm/nucleus ratio**) for each individual cell.

**Reporter Translocation Mechanism:**
The translocation of these reporters is mediated by phosphorylation:
- DHB-Venus is phosphorylated by Cdk2.
- mCherry-KTR is phosphorylated by Cdk4.

**Interpretation:**
- **Higher ratio (> 1):** Indicates more kinase activity (predominantly in the cytoplasm).
- **Lower ratio (< 1):** Indicates less kinase activity (predominantly in the nucleus).

*Note: The CDK4 reporter (mCherry-KTR) responds partially to CDK2 activity. The notebook automatically applies a correction factor (`CDK4 activity = cdk4_cyto_nuc_ratio - 0.35 × cdk2_cyto_nuc_ratio`) to isolate Cdk4 activity accurately.*

## Getting Started

1. Clone the repository.
2. Ensure you have the required dependencies installed (see requirements.txt).
3. Open `cdk2-cdk4-activity-quantification.ipynb` in Jupyter Notebook or JupyterLab.
4. Run the cells sequentially to process your images, calculate ratios, and generate visualizations.

## References

- [1] Cambuim, L. O., & Bruni-Cardoso, A. Microscopy image dataset of Cdk2 and Cdk4 activity reporters, phase contrast and histone H2B paired with nuclear masks of EpH4 mammary epithelial cells across variable cell densities and Cdk inhibition treatments. 10.5281/zenodo.19500864
- [2] Spencer, S. L., Cappell, S. D., Tsai, F. C., Overton, K. W., Wang, C. L., & Meyer, T. (2013). The proliferation-quiescence decision is controlled by a bifurcation in CDK2 activity at mitotic exit. *Cell*, 155(2), 369-383. https://doi.org/10.1016/j.cell.2013.08.062 
- [3] Yang, H. W., Cappell, S. D., Jaimovich, A., Liu, C., Chung, M., Daigh, L. H., Pack, L. R., Fan, Y., Regot, S., Covert, M., & Meyer, T. (2020). Stress-mediated exit to quiescence restricted by increasing persistence in CDK4/6 activation. *eLife*, 9, e44571. https://doi.org/10.7554/eLife.44571

## Funding
**this work is funded by FAPESP 2025/07672-1 and 2024/16814-1**
