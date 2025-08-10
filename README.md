# Share-of-Voice-and-Sentiment-Analysis-for-the-Smart-Fan-Market
This project provides a comprehensive analysis of the market position and consumer perception of the **Atomberg** brand within the "smart fan" category. The analysis is conducted by scraping and processing data from YouTube, quantifying brand visibility through various Share of Voice (SoV) metrics, and evaluating public sentiment through comment analysis.

You can open this look to look at python colab notebook for clear understanding of project 
```
https://colab.research.google.com/drive/1foE4xF16GHXiIFUBp3I1qHfBKSw-q8JB?usp=sharing

```
The core of this project is to move beyond simple mention counts and create more nuanced metrics that reflect the true impact of a brand's online presence.

## Key Analyses & Metrics

The notebook performs several layers of analysis to generate a holistic view of the market landscape:

* **Data Scraping**: Fetches data from the **top 200 YouTube videos** for the search query "smart fan," collecting video titles, descriptions, comments, likes, and views.

* **Mention-Based Share of Voice (SoV)**: Calculates the basic share of voice by counting the percentage of videos that mention Atomberg versus its competitors.

* **Engagement-Weighted Share of Voice (SoV)**: A more advanced metric that weights brand mentions by their audience interaction. This provides a more accurate picture of impact by valuing mentions in popular content more highly. The engagement score is calculated using the formula:
    ```
    Engagement Score = (4 * Likes) + Views
    ```
    This formula assigns a **4x higher value to a "like"** than a "view," as a like represents a more active and deliberate form of user approval.

* **Share of Positive Voice (SoPV)**:
    * Applies the **VADER sentiment analyzer** to user comments to classify them as positive, neutral, or negative.
    * Calculates the "Share of Positive Voice" to determine a brand's portion of positive consumer feedback online.

* **Feature Keyword Analysis**: Identifies the frequency of key product features (e.g., "bldc", "smart", "remote") discussed in relation to each brand to understand brand-feature association.

* **Semantic Search**: Implements a **Qdrant vector database** to perform semantic searches on the comment data. This allows for nuanced, meaning-based queries (e.g., "Best BLDC Fan") to find the most relevant consumer feedback.

## Tech Stack

* **Language**: Python 3
* **Environment**: Jupyter Notebook
* **Data Analysis**: Pandas
* **Sentiment Analysis**: VaderSentiment
* **Vector Database & Search**: Qdrant Client, Sentence-Transformers
* **Data Scraping**: `google-api-python-client` (for YouTube Data API)
* **Data Visualization**: Matplotlib

## Setup and Installation

Follow these steps to set up and run the project locally.

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git)
    cd your-repository-name
    ```

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```
  Then run:
    ```bash
    pip install -r requirements.txt
    ```
    download the requirement.txt 

4.  **Set Up API Keys:**
    * **YouTube Data API:** This project requires a YouTube Data API v3 key. Obtain one from the [Google Cloud Console](https://console.cloud.google.com/).
    * **Qdrant Cloud:** A running instance of a Qdrant vector database is needed. The script is pre-configured with a public URL and an API key which should be replaced with your own credentials from [cloud.qdrant.io](https://cloud.qdrant.io/).
    * Update the API keys and URLs in the respective cells within the Jupyter Notebook.



## Summary of Findings

| Metric | Atomberg's Performance | Key Competitors |
| :--- | :--- | :--- |
| **Share of Voice (Mention-based)** | **29.25%** | Dreo (23.81%) |
| **Engagement-Weighted SoV** | **25.90%** | Havells (15.35%), Orient (14.68%)|
| **Share of Positive Voice (SoPV)** | **13.58%** | Dreo (19.75%), Havells (17.28%)|

### Example Semantic Search Result

A semantic search for **"Best BLDC Fan"** returns the following top comment, showcasing the model's ability to understand query intent:

-   **Score**: 0.724
-   **Title**: Orient BLDC remote celling fan amazing speed...
-   **Comment**: Best BLDC fan under 3000...
-   **URL**: `https://youtube.com/watch?v=...`
