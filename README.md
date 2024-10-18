# BBC_Bias

Project Overview
This project focuses on analysing potential biases in the news reporting of the Israeli-Palestinian conflict from Al Jazeera and BBC News. The analysis is based on Word2Vec models trained weekly from news articles published between October 2023 and March 2024. Key terms like 'Israeli', 'Palestinian', 'murder', 'killed', etc., are tracked, and cosine similarity between these terms is computed over time. The project also visualises how the relationship between these terms evolves using PCA (Principal Component Analysis).

Files
Al Jazeera Bias Word2Vec.ipynb: Jupyter notebook performing data collection, cleaning, and Word2Vec model training for Al Jazeera articles.
BBC News Bias Word2Vec.ipynb: Jupyter notebook performing similar analysis on BBC News articles.
models/: Contains the trained Word2Vec models for each week.
Installation
Requirements:
torch
datasets
beautifulsoup4
gensim
nltk
pandas
scikit-learn
You can install the required libraries with:

bash
Copy code
pip install torch datasets beautifulsoup4 gensim nltk pandas scikit-learn
Additionally, the project requires stopwords and tokenizers from nltk:

python
Copy code
import nltk
nltk.download('stopwords')
nltk.download('punkt')
Data Sources
Al Jazeera: Data collected for weekly news articles published between 7 October 2023 and 28 March 2024.
BBC News: Data collected similarly for BBC News articles for the same period.
The dataset for each week is stored in a Pandas DataFrame and tokenised into sentences and words.

How to Run
Train Word2Vec Models: The Word2Vec models are trained weekly, with learning rates decaying over time. You can train new models or load pre-trained ones from the models/ directory.

Example:

python
Copy code
from gensim.models import Word2Vec
model = Word2Vec(sentences, vector_size=300, window=10, min_count=5, workers=4, sg=1)
model.save("models/word2vec_aljazeera_week_1.model")
Cosine Similarity Analysis: For each week, cosine similarities between key term pairs are calculated and visualised.

python
Copy code
from scipy.spatial.distance import cosine
cos_sim = 1 - cosine(model.wv['israeli'], model.wv['palestinian'])
PCA Visualisation: After training, vectors are reduced to 2D and 3D representations using PCA for visualisation purposes.

Results
The project generates weekly cosine similarity matrices and PCA visualisations to track potential biases in reporting. These metrics can highlight how the relationship between terms like 'Israeli' and 'Palestinian' changes in the news over time.

Future Work
Extend analysis to other major news outlets.
Automate data collection with APIs for continuous real-time updates.
Explore additional NLP techniques like topic modelling to capture deeper semantic insights.
License
This project is licensed under the MIT License.

Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss your proposed changes.
