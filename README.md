# CS:GO Round Winner Prediction

This project uses historical Counter-Strike: Global Offensive round snapshots to predict whether the `CT` team or `T` team will win a round.

The current implementation lives in a Jupyter notebook and walks through:

- data loading
- data cleaning
- label encoding
- train/test split
- feature scaling
- model training
- model comparison

## Problem Statement

Given the state of a CS:GO round at a particular moment, predict which side will win the round:

- `CT` for Counter-Terrorists
- `T` for Terrorists

## Project Structure

```text
CSgo-Project/
├── Data/
│   └── csgo_round_snapshots.csv
├── Notebook/
│   └── CSgo.ipynb
└── README.md
```

## Dataset

The dataset used in this project is:

- `Data/csgo_round_snapshots.csv`

It contains round-state information such as:

- time left in the round
- current team scores
- map name
- bomb planted status
- team health, armor, money, and helmets
- alive players on each side
- weapon counts
- grenade counts
- round winner

From the notebook analysis:

- original shape: `122410` rows and `97` columns
- duplicate rows found: `4962`
- shape after removing duplicates: `117448` rows and `97` columns
- missing values: `0`

## Workflow

The notebook follows this pipeline:

1. Load the dataset.
2. Inspect columns, shape, duplicates, and missing values.
3. Remove duplicate rows.
4. Encode categorical columns:
   - `map`
   - `round_winner`
   - `bomb_planted`
5. Split the data into features and target.
6. Create training and testing sets.
7. Scale the features using `StandardScaler`.
8. Train multiple classification models.
9. Compare model accuracy.

## Models Used

The following models are trained in the notebook:

- Logistic Regression
- Linear Discriminant Analysis
- Decision Tree Classifier
- Random Forest Classifier

The notebook also uses LDA coefficients to select the top 20 features before training later models.

## Results

The notebook reports these test accuracies:

- Logistic Regression: `0.7592`
- Logistic Regression with selected features: `0.7589`
- Decision Tree Classifier: `0.8094`
- Random Forest Classifier: `0.8578`

Based on the current notebook, the Random Forest model performs best.

## Requirements

To run the notebook, install Python 3 and the following libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

## How To Run

1. Clone the repository.
2. Open the project folder.
3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open `Notebook/CSgo.ipynb`.
5. Run the cells in order.

## Important Note

The notebook currently reads the dataset using an absolute local path. If you run this project on another machine, update the dataset path in the notebook to a relative path such as:

```python
df = pd.read_csv('../Data/csgo_round_snapshots.csv')
```


**Anurag Panchal**

🔗 LinkedIn: https://www.linkedin.com/in/panchalanurag/  
📧 Email: anuragpanchal002@gmail.com

Created as a machine learning project using CS:GO round snapshot data.
