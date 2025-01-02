# Clustering EEG time series of alcoholic subjects using Persistent Homology

## Introduction

This project aims to analyze and cluster EEG time series data of alcoholic and control subjects using techniques from persistent homology. Persistent homology is a method from topological data analysis that helps to capture the shape of data and identify significant features that persist across multiple scales.

## Dataset

The dataset used in this project is the [EEG-Alcohol](https://www.kaggle.com/nnair25/Alcoholics) dataset from Kaggle. It contains EEG data for two groups: Alcoholic and Control. The data was recorded using 64 electrodes placed on the subjects' scalps, measuring the electrical activity of the brain.

## Methodology

1. **Data Import and Preprocessing**: The EEG data is imported and preprocessed to filter noise using Empirical Mode Decomposition (EMD).
2. **Takens' Embedding**: The phase space of the time series is reconstructed using Takens' embedding theorem.
3. **Persistent Homology**: Persistence diagrams are computed using Rips complexes to capture the topological features of the embedded data.
4. **Feature Extraction**: Topological features are extracted from the persistence diagrams using Vietoris-Rips complex (or Witness complex) filtration.
5. **Clustering**: The extracted features are clustered using KMeans, and the results are evaluated against ground truth labels.

## Results

The clustering results are evaluated using various metrics such as accuracy, precision, recall, F1 score, and Matthews correlation coefficient. Confusion matrices and persistence diagrams are plotted to visualize the results.

## Conclusion

This project demonstrates the application of persistent homology in analyzing and clustering EEG time series data. The topological features extracted from the persistence diagrams provide valuable insights into the differences between alcoholic and control subjects.

## References

- [EEG Data Analysis](https://www.kaggle.com/code/ruslankl/eeg-data-analysis) by Ruslan Klymentiev
- [EEG-Alcohol Dataset](https://www.kaggle.com/nnair25/Alcoholics)
- [Persistent Homology](https://en.wikipedia.org/wiki/Persistent_homology)
- [Takens' Embedding Theorem](https://en.wikipedia.org/wiki/Takens%27s_theorem)

## Prerequisites

Before running the experiments, ensure you have the following software and libraries installed:

- Tested with Anaconda environment with Python 3.12.4 kernel
- Additional libraries: (install using `pip install -r requirements.txt`)
  - `numpy==1.26.4`
  - `pandas==2.2.2`
  - `gudhi==3.10.1`
  - `tqdm==4.66.4`
  - `scikit-learn==1.4.2`
  - `matplotlib==3.8.4`
  - `seaborn==0.13.2`
  - `EMD-signal==1.6.4`
  - `giotto-tda==0.6.2`

## Instructions to Run the Experiments

1. **Clone the Repository**: Clone the GitHub repository to your local machine using the following command:

  ```bash
  git clone https://github.com/corovcam/tda-time-series-clustering.git
  cd tda-time-series-clustering
  ```

2. **Download the Dataset**: Download the EEG-Alcohol dataset from Kaggle and place it in the `data` directory. (For convenience, the already preprocessed data is included in the `/data` directory)

3. **Run the Preprocessing Script**: Execute the preprocessing Jupyter Notebook `1-eeg-data-analysis.ipynb` to filter noise and prepare the data:
   
  ```bash
  jupyter notebook 1-eeg-data-analysis.ipynb
  ```

4. **Run the Main Experiment**: Execute the main notebook `2-homology-clustering.ipynb` to perform EDA, Takens' embedding, compute persistent homology, extract features, cluster the data, and evaluate the results against baseline KMeans clustering:

  ```bash
  jupyter notebook 2-homology-clustering.ipynb
  ```

  - Alternatively, you can run the `3-300-series-lazy-witness-clustering.ipynb` notebook to perform clustering using the lazy witness complex: (but this one has similar results to the main notebook)

  ```bash
  jupyter notebook 3-300-series-lazy-witness-clustering.ipynb
  ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.