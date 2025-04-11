### 🧼 Data Cleaning & Preprocessing for Tableau

This script takes the raw `layer2.csv` dataset and performs the following steps:

1. **Unpivots (melts)** the wide-format price data into a long format with `Token`, `Date`, and `Price` columns.
2. **Cleans** and flattens the `Platform` column by removing newlines and extra spaces.
3. **Sorts** tokens chronologically based on their original order and date.
4. **Calculates** key metrics:
   - `Daily Return` (percentage price change day-over-day)
   - `Indexed Price` (normalized to 100 at the token's starting date)
5. **Generates** summary statistics per token:
   - `Avg Return` (mean daily return)
   - `Volatility` (standard deviation of returns)
   - `Total Return` (change from first to last price)
6. **Exports** the final flat file `layer2_tableau_ready.csv` for Tableau visualisation.

📁 Output:
- A CSV containing enriched, normalized token data over time, ready for Tableau exploration.

### 📊 Generating Token Correlation Data for Heatmap

This script loads the `layer2_tableau_ready.csv` file and performs the following:

1. **Pivots** the dataset so each row represents a date, and each column contains the `Daily Return` for a single token.
2. **Computes** a **Pearson correlation matrix** to assess how similarly tokens move in relation to each other.
3. **Converts** the matrix to long format, resulting in a list of `[Token1, Token2, Correlation]` rows — ideal for use in a Tableau heatmap.
4. **Exports** the correlation matrix as `layer2_correlations.csv`.

📁 Output:
- A long-format correlation table used to create a heatmap visual in Tableau Public.
