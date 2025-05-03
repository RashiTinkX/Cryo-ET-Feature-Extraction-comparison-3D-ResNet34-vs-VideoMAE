# Cryo-ET Feature Comparison using 3D-ResNet34 and VideoMAE

This project compares the feature extraction and clustering capabilities of two deep learning models—3D-ResNet34 and VideoMAE—on Cryo-Electron Tomography (.mrc) data. The extracted features are visualized using t-SNE and clustered using K-Means, with performance evaluated through clustering metrics.

## Project Structure

```
project/
│
├── models/                     # Contains ResNet34 implementation (from Kensho Hara)
│   └── resnet.py
├── resnet-34-kinetics-cpu.pth  # Pretrained checkpoint for ResNet34
├── videomae_checkpoint.pth     # Pretrained checkpoint for VideoMAE
├── main.py                     # Main script to run the pipeline
├── README.md                   # This file
└── cryo-ET-sample/             # Folder with Cryo-ET .mrc files
```

## Features

- Loads 3D Cryo-ET .mrc volumes
- Preprocesses data for ResNet and VideoMAE
- Extracts features using:
  - 3D-ResNet34 (Kensho Hara)
  - VideoMAE (Hugging Face)
- Visualizes features using t-SNE
- Clusters features using K-Means
- Evaluates clusters using:
  - Silhouette Score
  - Davies-Bouldin Index
  - Cosine Similarity

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/cryo-et-feature-comparison.git
cd cryo-et-feature-comparison
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Place Your Cryo-ET .mrc Files

Put your .mrc volumes in the folder:
```
cryo-ET-sample/
```

## How to Run

Simply execute:

```bash
python app.py
```

This will:
- Load .mrc files
- Preprocess for both models
- Extract features
- Visualize t-SNE embeddings
- Cluster with K-Means
- Evaluate with Silhouette, DBI, and Cosine Similarity

## Output

- t-SNE Plots comparing ResNet34 vs. VideoMAE
- K-Means Clustering Visualizations for both models
- Quantitative metrics printed in terminal:
  - Silhouette Score
  - Davies-Bouldin Index
  - Cosine Similarity between feature spaces

## Models Used

- **3D-ResNet34** from Kensho Hara's Kinetics implementation
- **VideoMAE** from Hugging Face (MCG-NJU/videomae-base)

## Example Result

A scatter plot showing t-SNE projections of Cryo-ET features extracted by both models, with annotations of tomotarget IDs.

## Notes

- Make sure your .mrc files have sufficient depth (≥16 slices) for VideoMAE.
- For best reproducibility, seeds are fixed across NumPy, PyTorch, and Python.

## References

- [3D-ResNet34 by Kensho Hara](https://github.com/kenshohara/3D-ResNets-PyTorch)
- [VideoMAE](https://huggingface.co/docs/transformers/model_doc/videomae)

## License

[MIT](LICENSE)
