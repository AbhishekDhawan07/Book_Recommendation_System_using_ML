# 📚 Book_Recommendation_AI

> A Machine Learning-powered book recommendation engine combining **Popularity-Based Filtering** and **Collaborative Filtering with Cosine Similarity** — built with Python & Streamlit.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white"/>
  <img src="https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
</p>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Demo](#-demo)
- [Tech Stack](#-tech-stack)
- [Features](#-features)
- [Dataset](#-dataset)
- [How It Works](#-how-it-works)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🧠 About the Project

The **Book Recommender System** helps users discover books tailored to their reading preferences using two distinct ML strategies:

1. **Popularity-Based Filtering** — Surfaces the Top 50 most-rated books (minimum 250 ratings required), ranked by community engagement.
2. **Collaborative Filtering (CF) with Cosine Similarity** — Generates personalized recommendations by finding books liked by users with similar tastes, powered by a User-Item matrix and cosine similarity.

The system runs on the **Book-Crossing dataset** — a rich open dataset with 270,000+ users, 1M+ ratings, and 271,000+ books.

🔗 **GitHub Repository:** [https://github.com/AbhishekDhawan07/Book_Recommendation_AI](https://github.com/AbhishekDhawan07/Book_Recommendation_AI)

---

## 🎬 Demo

### Tab 1 — Top 50 Popular Books

Browse the **Top 50 most-rated books** ranked by total number of community ratings. Each card shows:

- 📖 Book cover image
- 📝 Title & Author
- ⭐ Average star rating
- 🔢 Total number of ratings

> Minimum threshold of **250 ratings** ensures only well-reviewed books appear.

Screenshots of the app:

- [Books 1–10](https://raw.githubusercontent.com/AbhishekDhawan07/Book_Recommendation_AI/main/First_10_Books_Recommendation.png)
- [Books 11–20](https://raw.githubusercontent.com/AbhishekDhawan07/Book_Recommendation_AI/main/Second_10_Books_Recommendation_.png)
- [Books 21–30](https://raw.githubusercontent.com/AbhishekDhawan07/Book_Recommendation_AI/main/Third_10_Books_Recommendation.png)
- [Books 31–40](https://raw.githubusercontent.com/AbhishekDhawan07/Book_Recommendation_AI/main/Fourth_10_Books_Recommendation.png)
- [Books 41–50](https://raw.githubusercontent.com/AbhishekDhawan07/Book_Recommendation_AI/main/Fifth_10_Books_Recommendation.png)

---

### Tab 2 — Recommend Books

Enter any book title into the search box and instantly receive **5 personalized recommendations** powered by Collaborative Filtering and Cosine Similarity.

**How to use:**
1. Click the **🔍 Recommend Books** tab
2. Type or select a book title from the dropdown
3. Hit **Show Recommendations**
4. Get 5 similar books with covers, titles, and authors

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.x |
| Data Manipulation | Pandas, NumPy |
| Machine Learning | Scikit-learn (Cosine Similarity) |
| Web Framework | Streamlit |
| Model Persistence | Pickle (`.pkl`) |
| Notebook | Jupyter Notebook (`.ipynb`) |

---

## ✨ Features

- 🔥 **Top 50 Popular Books** — Browse the most-loved books ranked by number of ratings, with cover images, author names, average star ratings, and total rating counts
- 🔍 **Collaborative Filtering Recommendations** — Enter any book title to get 5 personalized recommendations computed via cosine similarity
- 🖼️ **Book Cover Thumbnails** — Each card displays the actual book cover fetched from the dataset
- ⭐ **Ratings Display** — Shows both average star rating and total number of ratings for transparency
- 📊 **CF Recommendation Pool** — 706 books eligible for collaborative filtering (sufficient rating density)
- 🌗 **Dark-Themed UI** — Clean, modern dark interface with green accents for comfortable reading
- 📱 **Responsive Grid Layout** — Books displayed in a 5-column card grid
- ⚡ **Pre-computed Pickle Files** — Models saved as `.pkl` files for instant loading without retraining

---

## 📂 Dataset

The project uses the **Book-Crossing Dataset**, split into three CSV files. Download them from the links below:

| File | Description | Download |
|---|---|---|
| `Books.csv` | Book metadata — ISBN, title, author, year, publisher, cover image URLs | [📥 Download Books.csv](https://drive.google.com/file/d/1mXqu043n8fk1iR-7an9Z1KEklmGhHgie/view?usp=sharing) |
| `Ratings.csv` | User–book ratings on a scale of 0–10 | [📥 Download Ratings.csv](https://drive.google.com/file/d/1m8RnTeECO7gxv7rubGYBbPTnql2VhI1M/view?usp=sharing) |
| `Users.csv` | User demographics — user ID, location, age | [📥 Download Users.csv](https://drive.google.com/file/d/15mPKzKETpTMcvEsCFPB5IYM3FfvVRFYi/view?usp=sharing) |

> ⚠️ **Note:** Place all three CSV files in the root project directory before running the notebook or Streamlit app.

---

## ⚙️ How It Works

### 1. Popularity-Based Filtering
```
Books.csv ──► Merge with Ratings.csv ──► Group by book title
                                                │
                                     Count number of ratings
                                                │
                                   Filter: ratings_count ≥ 250
                                                │
                                   Calculate average rating
                                                │
                                   Sort by ratings_count DESC
                                                │
                                   Take Top 50  ──►  Saved as popular.pkl
```

- Merges `Books.csv` and `Ratings.csv` on ISBN
- Groups by book title and counts ratings per book
- Applies a **250-rating minimum threshold** to ensure statistical credibility
- Computes average rating and sorts descending by total rating count
- Result saved to `popular.pkl` for fast Streamlit loading

### 2. Collaborative Filtering (Cosine Similarity)
```
Users  ──► Filter power users (rated ≥ 200 books)
Books  ──► Filter popular books (received ≥ 50 ratings)
                        │
           Build Pivot Table (User-Item Matrix)
           rows = books │ columns = users │ values = ratings
                        │
           Compute Cosine Similarity Matrix (book × book)
                        │
           Saved as: pt.pkl + similarity_scores.pkl
                        │
           Input Book ──► Lookup Index ──► Fetch similarity row
                                                  │
                                       Sort DESC, Top 5 results
                                                  │
                                       Return Recommended Books
```

- Filters users who rated at least **200 books** to reduce noise from casual users
- Filters books with at least **50 ratings** to ensure meaningful comparison
- Builds a **Pivot Table** (Book × User matrix with rating values)
- Applies `cosine_similarity` from Scikit-learn across all books
- Pivot table saved as `pt.pkl`; similarity matrix saved as `similarity_scores.pkl`
- On query: looks up book index → fetches similarity vector → returns top 5 matches

---

## 🗂️ Project Structure
```
Book_Recommendation_AI/
│
├── Books Recommendation System using ML.ipynb  # Full ML pipeline & EDA notebook
├── app.py                                       # Streamlit web application
│
├── popular.pkl                                  # Pre-computed top 50 popular books
├── pt.pkl                                       # Pre-computed User-Item pivot table
├── similarity_scores.pkl                        # Pre-computed cosine similarity matrix
│
├── Books.csv                                    # Book metadata       (download required)
├── Ratings.csv                                  # User ratings        (download required)
├── Users.csv                                    # User demographics   (download required)
│
├── First_10_Books_Recommendation.png            # App screenshot — books 1–10
├── Second_10_Books_Recommendation_.png          # App screenshot — books 11–20
├── Third_10_Books_Recommendation.png            # App screenshot — books 21–30
├── Fourth_10_Books_Recommendation.png           # App screenshot — books 31–40
├── Fifth_10_Books_Recommendation.png            # App screenshot — books 41–50
│
└── README.md                                    # Project documentation
```

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/AbhishekDhawan07/Book_Recommendation_AI.git
cd Book_Recommendation_AI
```

### 2. Install Dependencies
```bash
pip install pandas numpy scikit-learn streamlit jupyter
```

### 3. Download the Dataset

Download all three CSV files and place them in the project root:

- 📥 [Books.csv](https://drive.google.com/file/d/1mXqu043n8fk1iR-7an9Z1KEklmGhHgie/view?usp=sharing)
- 📥 [Ratings.csv](https://drive.google.com/file/d/1m8RnTeECO7gxv7rubGYBbPTnql2VhI1M/view?usp=sharing)
- 📥 [Users.csv](https://drive.google.com/file/d/15mPKzKETpTMcvEsCFPB5IYM3FfvVRFYi/view?usp=sharing)

### 4. Run the Jupyter Notebook *(optional — pkl files already included)*
```bash
jupyter notebook "Books Recommendation System using ML.ipynb"
```

Execute all cells to regenerate `popular.pkl`, `pt.pkl`, and `similarity_scores.pkl` if needed.

### 5. Launch the Streamlit App
```bash
streamlit run app.py
```

Open your browser at **`http://localhost:8501`** and start exploring!

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests for:

- Adding new algorithms (content-based filtering, hybrid recommender)
- Improving the Streamlit UI/UX
- Adding user login and personalized rating history
- Deploying to Streamlit Cloud or Hugging Face Spaces
- Extending the dataset with newer book data

### Steps to Contribute
```bash
# Fork the repository
# Create your feature branch
git checkout -b feature/your-feature-name

# Commit your changes
git commit -m "Add: your feature description"

# Push and open a Pull Request
git push origin feature/your-feature-name
```

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

<p align="center">
  Built with ❤️ by <a href="https://github.com/AbhishekDhawan07">Abhishek Dhawan</a> · Powered by Python, Scikit-learn & Streamlit
</p>
