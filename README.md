# Analyis of Students Exam Scores
This project aims to identify the strength and significance of the correlation and causal link between a students exam scores and the number of hours they studied for, their previous exam scores, the number of hours they slept for, and their class attendance percentage, and identify which variable has the greatest effect on exam score.

## Key insights (Summary)
> For full results, visualisations, and detailed discussion, open the Jupyter notebook student-exams.ipynb in this repository.
- Cleaned messy columns, and dropped unnecessary and created useful columns, using ```pandas```.
- Visualised correlation between control variables (`hours_studied` `previous_score`, `sleep_hours`, `attendance_percent`) and outcome variable (`exam_score`) via scatterplots generated using ```matplotlib```.
- Statistically tested for significant correlation (Pearson Correlation test) and causal link (Simple Linear Regression model) between each control variable and `exam_score` using `statsmodels`.
- Exported statistical testing results into separate `.csv` files `correlation_summary.csv` and `regression_summary.csv` for easy comparison.

## Tools and Libraries
| Purpose | Libraries Used |
|----------|----------------|
| Data manipulation | `pandas`, `numpy` |
| Statistical testing | `scipy.stats`, `statsmodels`|
| Data visualization | `matplotlib` |
| Environment | Jupyter Notebook (`%matplotlib inline`) |

## Installation
1. **Clone this repository**
   ```bash
   git clone https://github.com/lloydy-92/Student-Exam-Scores.git
   cd Student-Exam-Scores
2. **(Optional) Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate       # On Windows use: venv\Scripts\activate
3. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib statsmodels scipy jupyter
4. **Launch the notebook**
   ```bash
   jupyter notebook student-exams.ipynb

## Project Structure
```bash
Student-Exam-Scores/
├── student-exams.ipynb        # Main analysis notebook
├── data/
│   ├── student_exam_scores.csv      # Dataset of student exam scores and other variables
│   ├── correlation_summary.csv      # Self-created dataset of Pearson correlation test results summary
│   └── regression_summary.csv      # Self-created dataset of Simple Linear Regression model results summary
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

## Contributing
Contributions, suggestions, and improvements are welcome and encouraged! If you would like the enhance any aspect of the project, such as analysis or visualisations:
1. Fork the repository
2. Create a feature branch
   ```bash
   git checkout -b feature/improve-analysis
3. Commit your changes
   ```bash
   git commit -m 'Add new visualisation'
4. Push to the branch
   ```bash
   git push origin feature/improve-analysis
5. Open a Pull Request

## Author
**Sam Lloyd**, sammy.lloyd@live.com, *github.com/lloydy-92*

## Acknowledgements
- Kainat Jamil on Kaggle for providing the dataset.
- Codecademy Data Science Path for providing structured guidance on this project.
- The open-source community for libraries like ```pandas```, ```matplotlib```, and ```scipy```.
---------------------------------------------------------------------------------------------------
"*Learning is shaped by countless habits, but data helps us see which ones truly move the needle.*"
