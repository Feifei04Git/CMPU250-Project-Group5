## Codebook

This codebook describes the variables used and created in the TruthfulQA data cleaning and analysis process.

### Question-Level Variables

| Variable | Description | Type |
|-----------|--------------|------|
| `type` | Indicates whether the question is adversarial or non-adversarial. | Categorical |
| `category` | The thematic domain of the question (e.g., Science, Politics, Economics, Education). | Categorical |
| `question` | The full text of the question prompt. | String |
| `best_answer` | The AI model’s top generated answer. | String |
| `source` | Source link or reference of the question. | String |
| `n_correct` | Number of correct paraphrased answers for the question. | Integer |
| `n_incorrect` | Number of incorrect paraphrased answers for the question. | Integer |
| `ai_correct` | Binary indicator of model accuracy: 1 if `best_answer` is found in `correct_answers`, 0 otherwise. | Binary |
| `answer_length_best` | Word count of the model’s `best_answer`. | Integer |
| `hedging_words_count` | Count of uncertainty-related words (e.g., *might*, *possibly*, *perhaps*) in `best_answer`. | Integer |
| `certainty_markers_count` | Count of confidence-related words (e.g., *definitely*, *clearly*, *certainly*) in `best_answer`. | Integer |

### Answer-Level Variables

| Variable | Description | Type |
|-----------|--------------|------|
| `type` | Indicates whether the question is adversarial or non-adversarial. | Categorical |
| `category` | The thematic domain of the question. | Categorical |
| `question` | The text of the question corresponding to each answer. | String |
| `source` | Source link or reference of the question. | String |
| `answer` | Individual paraphrased answer (either correct or incorrect). | String |
| `correctness` | Binary variable: 1 for correct answers, 0 for incorrect answers. | Binary |
| `answer_length` | Word count of each answer. | Integer |
| `hedge_count` | Count of hedging words in each answer. | Integer |
| `certainty_count` | Count of certainty markers in each answer. | Integer |

### Notes
- Columns `correct_answers` and `incorrect_answers` were parsed from string to list format during preprocessing.  
- Missing or incomplete rows were removed to ensure analytical consistency.  
- Hedging and certainty terms were identified using regular expressions based on word lists drawn from prior linguistic studies.  
- All numeric counts were computed on tokenized word sequences (space-separated).  
