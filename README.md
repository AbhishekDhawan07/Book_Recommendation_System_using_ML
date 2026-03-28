# 📚 Book_Recommendation_AI

> A Machine Learning-powered book recommendation engine combining **Popularity-Based Filtering** and **Collaborative Filtering with Cosine Similarity** — built with Python & Tkinter.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Tkinter-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white"/>
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

🔗 **GitHub Repository:** https://github.com/AbhishekDhawan07/Book_Recommendation_AI

---

## 🎬 Demo

### Tab 1 — Top 50 Popular Books

Browse the **Top 50 most-rated books** ranked by total number of community ratings. Each card shows:

- 📖 Book cover image  
- 📝 Title & Author  
- ⭐ Average star rating  
- 🔢 Total number of ratings  

> Minimum threshold of **250 ratings** ensures only well-reviewed books appear.

### 📸 Screenshots

#### First 10 Books Recommendation
![First 10 Books Recommendation](./First%2010%20Books%20Recommendation.png)

#### Second 10 Books Recommendation
![Second 10 Books Recommendation](./Second%2010%20Books%20Recommendation%20.png)

#### Third 10 Books Recommendation
![Third 10 Books Recommendation](./Third%2010%20Books%20Recommendation.png)

#### Fourth 10 Books Recommendation
![Fourth 10 Books Recommendation](./Fourth%2010%20Books%20Recommendation.png)

#### Fifth 10 Books Recommendation
![Fifth 10 Books Recommendation](./Fifth%2010%20Books%20Recommendation.png)

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
| `Books.csv` | Book metadata — ISBN, title, author, year, publisher, cover image URLs | https://drive.google.com/file/d/1mXqu043n8fk1iR-7an9Z1KEklmGhHgie/view |
| `Ratings.csv` | User–book ratings on a scale of 0–10 | https://drive.google.com/file/d/1m8RnTeECO7gxv7rubGYBbPTnql2VhI1M/view |
| `Users.csv` | User demographics — user ID, location, age | https://drive.google.com/file/d/15mPKzKETpTMcvEsCFPB5IYM3FfvVRFYi/view |

> ⚠️ **Note:** Place all three CSV files in the root project directory before running the notebook or Streamlit app.

---

## ⚙️ How It Works

### 1. Popularity-Based Filtering
- Merge `Books.csv` and `Ratings.csv`  
- Group by book title and count ratings  
- Filter books with ≥ 250 ratings  
- Compute average rating  
- Sort and select Top 50  

### 2. Collaborative Filtering (Cosine Similarity)
- Filter users who rated ≥ 200 books  
- Filter books with ≥ 50 ratings  
- Build User-Item matrix  
- Compute cosine similarity  
- Recommend top 5 similar books  

---

## 🗂️ Project Structure
```text
├── README.md                                 # You are here!!
|
├── Book_Recommendation_AI/                   # Main project folder
│   ├── Books Recommendation System using ML.ipynb
│   ├── app.py
│
│   ├── popular.pkl
│   ├── pt.pkl
│   ├── similarity_scores.pkl
│
│   ├── Books.csv
│   ├── Ratings.csv
│   ├── Users.csv
│
│   ├── First 10 Books Recommendation.png
│   ├── Second 10 Books Recommendation.png
│   ├── Third 10 Books Recommendation.png
│   ├── Fourth 10 Books Recommendation.png
│   └── Fifth 10 Books Recommendation.png
---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/AbhishekDhawan07/Book_Recommendation_AI.git
cd Book_Recommendation_AI

### Run the App
```bash
streamlit run app.py
```

---

## 🤝 Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.
