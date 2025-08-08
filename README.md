# Goodreads Review Analysis

## Overview
This project contains a Jupyter Notebook (`goodreads_review_analysis.ipynb`) designed to extract and analyze reviews for *The Secret History* from Goodreads using its GraphQL API. The notebook fetches reviews, saves them as JSON, and performs basic analysis, including sentiment analysis and visualization of rating distributions.

## Features
- **Data Extraction**: Scrapes reviews from Goodreads' GraphQL API with pagination (up to 500 pages, 30 reviews per page).
- **Data Storage**: Saves extracted reviews to `secret_history.json`.
- **Analysis**: Computes total reviews, average rating, text-based reviews, and identifies the most liked review.
- **Visualization**: Generates a bar plot showing the distribution of ratings.
- **Sentiment Analysis**: Uses VADER to analyze the sentiment of review texts.
- **Network Analysis**: Builds a reviewer network to identify influential users via PageRank and centrality metrics.

## Prerequisites
Install the required Python libraries listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

## Usage
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Set Up API Access**:
   - The notebook uses the Goodreads GraphQL API. Replace `API_KEY` in the notebook with a valid API key.
   - The `BOOK_RESOURCE_ID` is set for *The Secret History* (`kca://work/amzn1.gr.work.v1.UolPPkYqcwqjqVAWO5T0yQ`). Update it for a different book if needed.

3. **Run the Notebook**:
   - Open `goodreads_review_analysis.ipynb` in Jupyter Notebook or JupyterLab.
   - Execute the cells sequentially to:
     - Fetch reviews from the API.
     - Save reviews to `secret_history.json`.
     - Analyze and visualize the data.

4. **Outputs**:
   - A JSON file (`secret_history.json`) containing the scraped reviews.
   - Printed analysis results, including total reviews, average rating, and the most liked review.
   - A bar plot showing the distribution of ratings.

## Notebook Structure
- **Introduction**: Describes the purpose and workflow of the notebook.
- **API Documentation**: Details the Goodreads GraphQL API endpoint, query structure, and response format.
- **Code**:
  - Fetches reviews using the `requests` library with pagination and a 0.5-second delay to avoid rate limits.
  - Saves reviews to a JSON file using `pandas`.
  - Analyzes reviews to compute statistics (e.g., total reviews, average rating).
  - Visualizes rating distribution using `seaborn` and `matplotlib`.
- **Summary**: Highlights key findings, such as positive bias in reviews and influential reviewer communities.

## Notes
- The API key used in the notebook (`da2-xpgsdydkbregjhpr6ejzqdhuwy`) is for demonstration purposes. Obtain a valid API key from Goodreads for production use.
- The notebook is configured to scrape up to 500 pages of reviews (15,000 reviews max). Adjust `max_pages` to change this limit.
- Ensure compliance with Goodreads' API usage policies to avoid rate limiting or access restrictions.
- The sentiment analysis uses VADER, which is tuned for social media text but may require adjustments for nuanced literary reviews.

## Limitations
- The notebook only fetches reviews for a single book. To analyze multiple books, modify the `BOOK_RESOURCE_ID` and rerun.
- Network analysis assumes reviewer interactions are based on shared reviews, which may not fully capture influence dynamics.
- The API may have rate limits or require authentication updates, so monitor for errors during execution.

## Future Improvements
- Add support for multiple books or comparative analysis.
- Enhance sentiment analysis with custom lexicons for literary reviews.
- Expand network analysis to include additional metrics (e.g., betweenness centrality).
- Implement error handling for API downtime or invalid responses.
