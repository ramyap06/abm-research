# 🗂️ Detailed Layout (What Goes Where)

Here’s a recommended project directory & pipeline structure:

abscopal-abm-project/
│── README.md # Project overview & instructions
│── requirements.txt # Python dependencies
│── .env # Paths, environment configs
│
├── configs/ # Run configurations
│ ├── blockA.yaml # Base YAML template (Licensing ON)
│ ├── blockB.yaml # Base YAML template (Licensing OFF)
│ ├── blockA_highvar.yaml # Phase 2 configs (high variance)
│ ├── blockB_highvar.yaml
│ └── generated/ # Auto-generated JSON configs
│ ├── LN_ABM_BlockA_.json
│ └── LN_ABM_BlockB_.json
│
├── scripts/ # Core scripts
│ ├── sample_lhs.py # Latin Hypercube Sampling
│ ├── yaml_to_json.py # Convert YAML → JSON configs
│ ├── run_abm.py # Launch ABM runs from configs
│ ├── extract_features.py # Parse HDF5/CSV outputs → features
│ ├── detect_highvar.py # Compute variance, flag points
│ └── utils.py # Shared helpers (file paths, logging)
│
├── data/ # Raw + processed data
│ ├── raw/ # Raw outputs (HDF5, logs)
│ │ ├── blockA/
│ │ └── blockB/
│ ├── processed/ # Clean CSVs with extracted features
│ │ ├── features_blockA.csv
│ │ └── features_blockB.csv
│ ├── variance/ # Variance analysis results
│ │ ├── blockA_var.csv
│ │ └── blockB_var.csv
│ └── derived/ # Composite features
│ ├── amplification_index.csv
│ └── checkpoint_pressure.csv
│
├── analysis/ # Higher-level analysis
│ ├── pca_umap.ipynb # Dimensionality reduction
│ ├── clustering.ipynb # Phenotyping runs (k-means, DBSCAN)
│ ├── sensitivity.ipynb # Sobol / eFAST sensitivity
│ ├── boundary_mapping.ipynb# Identify bifurcation zones
│ └── predictive_modeling.ipynb # Random forest, NN, ROC curves
│
└── results/ # Final outputs
├── figures/ # Plots, heatmaps, PCA/UMAP
├── reports/ # Phase summaries
└── endpoints.csv # Final endpoints (success/failure, potency)