# 📩 Spam SMS Detector

A machine learning–powered web application that classifies SMS and email messages as **Spam** or **Not Spam** in real time. Built with Python, scikit-learn, and Streamlit, and deployed on Render.

🔗 **Live Demo:** [https://spam-sms-detector-f7i0.onrender.com](https://spam-sms-detector-f7i0.onrender.com)

---

## 🚀 Features

- 🔍 **Real-time Spam Detection** — Paste any SMS or email message and instantly get a prediction.
- 🧹 **Text Preprocessing Pipeline** — Lowercasing, tokenization, stopword removal, punctuation filtering, and Porter Stemming.
- 📊 **TF-IDF Vectorization** — Converts raw text into numerical features for the ML model.
- 🤖 **Trained ML Model** — A classification model trained on a labeled SMS spam dataset (`spam.csv`).
- ☁️ **Cloud Deployed** — Hosted on [Render](https://render.com) with a one-click accessible URL.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3 |
| Web Framework | Streamlit |
| ML / NLP | scikit-learn, NLTK |
| Vectorizer | TF-IDF (`TfidfVectorizer`) |
| Model | Trained classifier saved as `model.pkl` |
| Deployment | Render |

---

## 📁 Project Structure

```
SpamSMSDetector/
│
├── app.py                    # Main Streamlit application
├── model.pkl                 # Pre-trained ML classification model
├── vectorizer.pkl            # Pre-fitted TF-IDF vectorizer
├── spam.csv                  # Raw dataset used for training
├── spam-SMS-detector.ipynb   # Jupyter notebook: EDA, training & evaluation
├── requirements.txt          # Python dependencies
├── Procfile                  # Render deployment command
├── setup.sh                  # NLTK data download script for deployment
└── .gitignore
```

---

## ⚙️ How It Works

1. **Input** — User enters an SMS or email message in the text box.
2. **Preprocessing** — The text is:
   - Converted to lowercase
   - Tokenized using NLTK
   - Filtered to remove non-alphanumeric tokens
   - Stripped of English stopwords and punctuation
   - Stemmed using Porter Stemmer
3. **Vectorization** — The cleaned text is transformed using the pre-fitted TF-IDF vectorizer (`vectorizer.pkl`).
4. **Prediction** — The trained model (`model.pkl`) predicts whether the message is **Spam (1)** or **Not Spam (0)**.
5. **Output** — The result is displayed prominently on the screen.

---

## 🏃 Run Locally

### Prerequisites
- Python 3.8+
- pip

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/Sonu-ABC/spam_SMS_Detector.git
cd spam_SMS_Detector

# 2. (Optional) Create and activate a virtual environment
python -m venv myenv
myenv\Scripts\activate        # Windows
# source myenv/bin/activate   # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Download required NLTK data
python -m nltk.downloader stopwords punkt punkt_tab

# 5. Run the app
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

---

## 📦 Dependencies

```
streamlit==1.45.1
nltk
scikit-learn
```

---

## ☁️ Deployment (Render)

The app is deployed on **Render** using the following configuration:

**`setup.sh`** — Downloads NLTK corpora required at runtime:
```bash
mkdir -p ~/.nltk_data
python -m nltk.downloader stopwords punkt punkt_tab
```

**`Procfile`** — Tells Render how to start the app:
```
web: sh setup.sh && streamlit run app.py --server.port $PORT --server.address 0.0.0.0
```

---

## 📓 Model Training

The model was trained and evaluated in the Jupyter notebook [`spam-SMS-detector.ipynb`](./spam-SMS-detector.ipynb).

Training steps covered in the notebook:
- Exploratory Data Analysis (EDA) on `spam.csv`
- Text preprocessing and feature engineering
- TF-IDF vectorization
- Training and comparing multiple classifiers
- Saving the best model and vectorizer as `.pkl` files

---

## 📊 Dataset

- **Source:** [SMS Spam Collection Dataset](https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset)
- **Size:** ~5,572 labeled SMS messages
- **Labels:** `ham` (not spam) / `spam`

---

## 🙋‍♀️ Author

**Chandrima Biswas**  
[GitHub](https://github.com/Sonu-ABC)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
