# Student Performance Prediction Project

This repository contains a machine learning project to predict student exam scores (math, reading, writing, and total) using the "Students Performance in Exams" dataset from Kaggle. The project involves data preprocessing, model training, evaluation, and model persistence.

## Dataset
- **Source**: [Kaggle - Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- **Description**: The dataset includes 1000 rows with features such as gender, parental level of education, lunch type, test preparation course, and scores for math, reading, and writing.
- **Features**: `gender`, `parental level of education`, `lunch`, `test preparation course`, `math score`, `reading score`, `writing score`.
- **Target Variables**: `math score`, `reading score`, `writing score`, `total score` (calculated as the sum of the three scores).

## Project Workflow
1. **Checked Duplicated and Missing Values**
   - Verified no duplicates using `data.duplicated().sum()`.
   - Confirmed no missing values with `data.isna().sum()`.

2. **Detected and Handled Outliers**
   - Identified outliers using the Interquartile Range (IQR) method.
   - Replaced outliers with the median value for each numerical column (`math score`, `reading score`, `writing score`, `total score`).

3. **Used Label Encoding and One Hot Encoder**
   - Applied `LabelEncoder` to convert the binary `gender` column (male/female) to 0/1.
   - Used `OneHotEncoder` or `pd.get_dummies()` to encode multiclass columns (`parental level of education`, `lunch`, `test preparation course`) into binary variables.

4. **Splitted the Data**
   - Split the dataset into training (80%) and test (20%) sets using `train_test_split` with a fixed `random_state` for reproducibility.

5. **Used Linear Regression**
   - Trained a `LinearRegression` model on the training data to predict each target variable (`math score`, `reading score`, `writing score`, `total score`).

6. **Used RMSE and MAE**
   - Evaluated model performance using Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE) on the test set.
   - Example results (may vary): Math Score - MAE: 11.06, RMSE: 13.48.

7. **Saved the Models**
   - Saved each trained model using `joblib.dump` for future use (e.g., `linear_regression_math_model.joblib`).

## Setup Instructions
### Prerequisites
- Python 3.x
- Required packages (install via pip):
 
### Installation
1. Clone the repository:
2. Install dependencies:
3. Ensure the dataset is downloaded from Kaggle and placed in the project directory as `StudentsPerformance.csv`, or update the code to use the direct URL.

### Running the Project
1. Run the main script (e.g., `main.py`):
2. Check the console for duplicate/missing value checks, outlier handling output, and model evaluation metrics.
3. Find saved models in the project directory (e.g., `linear_regression_math_model.joblib`).

## Files
- `README.md`: This file.
- `requirements.txt`: List of required Python packages.
- `main.py`: Example script containing the workflow (to be created based on your code).
- `StudentsPerformance.csv`: The dataset (download from Kaggle).
- `*.joblib`: Saved model files.

## Results
- The model predicts exam scores with moderate accuracy. For example, the initial Linear Regression model for `math score` showed MAE: 11.06 and RMSE: 13.48.
- Coefficients (e.g., for `writing score`) indicate significant impacts from `test_preparation_course` (-9.96) and `parental_level_of_education` (e.g., bachelor's degree +4.74).

## Future Improvements
- **Model Tuning**: Experiment with Ridge or Lasso regression to reduce overfitting.
- **Feature Engineering**: Add interaction terms or polynomial features to capture non-linear relationships.
- **Visualization**: Add plots (e.g., box plots, coefficient plots) using `matplotlib`.

## Contributing
Feel free to fork this repository, make improvements, and submit pull requests. Suggestions for enhancing the model or documentation are welcome!

## License
[Add your preferred license here, e.g., MIT] - Default is no license unless specified.

## Acknowledgements
- Dataset provided by Kaggle user spscientist.
- Built with assistance from xAI's Grok 3 on August 05, 2025.
