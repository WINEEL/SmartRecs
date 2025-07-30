# SmartRecs
*A Hybrid Movie Recommendation System using Machine Learning*

## Overview
SmartRecs is a personalized media recommendation engine built using a **hybrid approach** that combines **content-based filtering** and **collaborative filtering**. It leverages large-scale IMDb datasets and machine learning techniques such as **TF-IDF**, **Cosine Similarity**, and **Singular Value Decomposition (SVD)** to suggest movies tailored to user preferences.

## Features
- Hybrid Recommendation: Combines genre similarity and collaborative ratings
- Fuzzy matching for flexible title inputs
- Genre-safe filtering (e.g., Horror is excluded unless requested)
- Large-scale compatibility using Kaggle Notebooks
- Easily extendable architecture for future work

## Dataset
This project uses official IMDb datasets:

- `title.basics.tsv` (~1.01 GB)
- `title.ratings.tsv` (~27 MB)

Note: The dataset files are not included in this repository because of their large size (over 1 GB), which exceeds GitHub's file size limits and is impractical for version control.  
Instead, we provide direct download links to the IMDb dataset source so users can fetch the latest and official data themselves.

**Download Links:**
- https://datasets.imdbws.com/title.basics.tsv.gz
- https://datasets.imdbws.com/title.ratings.tsv.gz

After downloading, unzip the `.gz` files before using them in the notebook.

## Methodology

### Content-Based Filtering
- Extracted genre vectors using **TF-IDF**
- Computed **cosine similarity** between genre vectors

### Collaborative Filtering
- Used **IMDb average rating** as implicit feedback
- Applied **SVD** from the `Surprise` library

### Hybrid Score Calculation
`final_score = 0.6 * svd_score + 0.4 * genre_similarity`

Recommendations are sorted by this hybrid score and filtered for genre relevance.

## Development Environment
This project was developed using **Kaggle Notebooks**, which offer up to **30 GB of RAM** — necessary for handling large matrices and high-dimensional TF-IDF vectors. Local systems and free Colab instances did not have sufficient memory for end-to-end execution.

## How to Run
1. Download the IMDb dataset from the links above.
2. Upload the unzipped `.tsv` files to your working directory or Kaggle Notebook.
3. Open the `smartrecs.ipynb` notebook.
4. Run the notebook and follow the prompt:
   - Input a movie title
   - Select the correct match
   - View top-N hybrid recommendations

## Example Results

### Input: `Inception`
Returns top Action/Sci-Fi recommendations like *Rogue One*, *Avengers: Endgame*

### Input: `Cars 2`
Returns animated family-friendly films like *Cars 3*, *Finding Dory*

## Documentation
Only the final PDF versions of the project documents are included in this repository under the `docs/` folder:

- [Report.pdf](docs/Report.pdf)
- [Presentation Slides.pdf](docs/Presentation%20Slides.pdf)

Drafts, `.docx`, and `.pptx` files are excluded to keep the repository clean and lightweight.

## Future Work
- Add filtering by actor/director/runtime
- UI deployment using Streamlit or Flask
- User-based personalization via login
- Model enhancement with embeddings or transformers

## License
This project is licensed under the [MIT License](LICENSE).  
You are free to use, modify, and distribute this project with attribution.

## Author
**Wineel Wilson Dasari**  
MS in Computer Science – Santa Clara University  
Project under CSEN 240: Machine Learning

## References
- IMDb Datasets: https://datasets.imdbws.com/
- Surprise Library: https://surpriselib.com/
- Scikit-Learn, Pandas, NumPy
- Kaggle Notebook: https://www.kaggle.com/code/wineelscu/smartrecs
