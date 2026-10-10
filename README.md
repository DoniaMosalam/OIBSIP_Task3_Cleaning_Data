# Level 1, Task 3: Cleaning Data (US Election 2020 Tweets)

**Notebook:** `Cleaning_Data_Election_Tweets.ipynb`

## Data
The raw files are about 860 MB, too large for GitHub, so they are not included. Download the Kaggle dataset **"US Election 2020 Tweets"** (`hashtag_donaldtrump.csv` and `hashtag_joebiden.csv`) and place both files next to the notebook. Running the notebook writes `cleaned_election_tweets.csv`.
The notebook cleans a 1-in-5 sample of the tweets; set `SAMPLE_EVERY = 1` in the first code cell to clean everything.

## Problems found and fixed
- 12.9% of rows were repeated copies of the same tweet (never identical rows, so a plain `drop_duplicates()` finds nothing).
- IDs were stored in scientific notation (rounded in the source file); converted to plain-digit text.
- Numbers and dates stored as text; 4 pairs of inconsistent country names; HTML codes in tweet text.
- Vague coordinates (e.g. "Europe", "North Pole") blanked.
- Outliers (viral tweets, huge accounts) kept deliberately, with log-scaled columns added.

## Result
304,403 unique tweets, 28 columns, 100% correct data types (from 52%), null cells reduced by about 80% (the rest is `lat`/`long`, left empty on purpose). A before-vs-after table and a log of every cleaning action are in the notebook.
