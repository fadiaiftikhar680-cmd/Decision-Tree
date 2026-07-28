# Decision Tree Regression — Position Salaries

Interactive Python/Jupyter notebook that trains a **Decision Tree Regressor** on the `Position_Salaries.csv` dataset, taking key choices (target/feature columns, hyperparameters) as user input at runtime.

## Files

| File | Description |
|---|---|
| `model.ipynb` | Notebook — one step per cell (markdown headings + code) |
| `model_single_cell.ipynb` | Same logic, but all code in a single cell |
| `Position_Salaries.csv` | Dataset (Position, Level, Salary) |
| `decision tree promt.docx` | Original task prompt/requirements |

## Requirements

- Python 3.8+
- Libraries: `pandas`, `numpy`, `matplotlib`, `scikit-learn`

Install with:
```bash
pip install pandas numpy matplotlib scikit-learn
```

## How to Run

1. Keep the notebook (`model.ipynb` or `model_single_cell.ipynb`) and `Position_Salaries.csv` in the same folder.
2. Launch Jupyter:
   ```bash
   jupyter notebook model.ipynb
   ```
3. Run the cell(s) in order (**Run → Run All Cells**, or `Shift+Enter`).
4. When prompted, answer the input questions (see below).

## What the Code Does (Step by Step)

1. **Import Libraries** — pandas, numpy, matplotlib, scikit-learn.
2. **Load Dataset** — reads `Position_Salaries.csv` into a DataFrame and shows a preview.
3. **Categorical Check** — asks:
   ```
   Does the dataset contain categorical variables? (yes/no):
   ```
   If `yes`, applies one-hot encoding via `pd.get_dummies()`.
4. **Column Selection** — asks for:
   ```
   Enter the target column name:
   Enter feature column name(s) separated by commas:
   ```
   Example: target = `Salary`, feature = `Level`
5. **Feature/Target Split** — builds `X` (features) and `y` (target) from your answers.
6. **Train/Test Split** — 80% training, 20% testing (`random_state=42`).
7. **Hyperparameters (optional)** — asks for:
   ```
   Enter max_depth (press Enter for default):
   Enter min_samples_split (press Enter for default):
   Enter min_samples_leaf (press Enter for default):
   ```
   Leave blank to use scikit-learn defaults.
8. **Train Model** — fits `DecisionTreeRegressor` on the training data.
9. **Predict** — predicts on the test set and prints actual vs. predicted values.
10. **Evaluate** — prints the **R² Score** only.
11. **Plot (conditional)** — if there is exactly **one** feature column, shows a scatter plot of actual data plus the regression curve.

## Example Run

```
Does the dataset contain categorical variables? (yes/no): no
Enter the target column name: Salary
Enter feature column name(s) separated by commas: Level
Enter max_depth (press Enter for default):
Enter min_samples_split (press Enter for default):
Enter min_samples_leaf (press Enter for default):

R² Score: 0.60
```
(Score varies with the train/test split and any hyperparameters you set.)

## Notes

- Feature column names must be typed exactly as they appear in the CSV header (case-sensitive).
- For multiple features, separate names with commas: `Level,Position`.
- The plot only appears when there is a single feature — this is by design since a regression curve can't be visualized in more than 2D on a simple chart.
