# image-retrieval-project
# 🚀 Image Retrieval with CLIP and Deep Metric Learning

## Abstract  
This repository presents a modular, end-to-end implementation of an image retrieval system based on a pre-trained CLIP ViT-L/14 backbone, fine-tuned via Deep Metric Learning (DML). Our multi-task training strategy combines ProxyAnchorLoss, TripletMarginLoss with hard-negative mining, and CrossEntropyLoss to learn highly discriminative embeddings. The code supports both the default Food101 dataset and any custom, user-supplied dataset in an ImageFolder format.

---

## 📂 Project Structure  
```text
.
├── main.py             # Entrypoint: training & evaluation
├── project_config.py   # Central hyperparameters & paths
├── requirements.txt    # Python dependencies
└── src/
    ├── data/           # Data preparation
    │   └── datasets.py
    ├── transforms/     # Data augmentations
    │   └── transforms.py
    ├── samplers/       # Metric-learning samplers
    │   └── samplers.py
    ├── loader/         # Data loaders
    │   └── loader.py
    ├── models/         # Model definitions
    │   └── model.py
    ├── training/       # Training loop & utilities
    │   └── trainer.py
    └── inference/      # Embedding extraction & evaluation
        └── evaluate.py
```
⚙️ Installation
1. Prerequisites
  - Python 3.8 or higher
  - Git
2. Clone & Virtual Environment
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
```
3. Dependencies
```bash
pip install -r requirements.txt
```
▶️ Usage
1. Default Dataset (Food101)
On first execution, the script will download and preprocess Food101 automatically.
```bash
python main.py --mode train
python main.py --mode eval
```
2. Custom Dataset
Your dataset must follow an ImageFolder-style hierarchy:
```bash
your_dataset/
├── training/
│   ├── class1/
│   └── class2/
└── test/
    ├── query/
    └── gallery/
```
Invoke with:
```bash
python main.py --mode train --data_dir /path/to/your_dataset
python main.py --mode eval  --data_dir /path/to/your_dataset
```
🔧 Configuration
All major hyperparameters are centralized in the config.py file for easy experimentation.

[!NOTE]
Modifying config.py is the recommended way to test different settings without altering the core logic. You can easily tweak parameters such as:

LEARNING_RATE, BATCH_SIZE, EPOCHS
EMBED_DIM, UNFREEZE_LAYERS
PROXY_MARGIN, TRIPLET_MARGIN
