# Okungujim.github.io
<h1><b>🎬 IMDb Movie Ratings Analysis</b></h1>
<h2>📌 Project Overview</h2>

<p>This project explores IMDb's top-rated movies to uncover patterns and insights about genres, viewer preferences, and rating trends over time. Using Python and Pandas, we analyze and visualize key aspects of the dataset, culminating in data-driven conclusions.</p>
<h1>📁 Dataset</h1>
<p>We use the IMDb Top 1000 Movies dataset from Kaggle, which includes:
<ul>
<li>Movie titles, release year</li>
<li>IMDb ratings, number of votes</li>
<li>Genre, duration, and more</li>
 </ul>
</p>
<p>🔍 Goals</p>
<ol>
</li>Identify genres with the highest average ratings</li>
<li> Visualize trends in ratings over time</li>
<li>Analyze the relationship between number of votes and ratings</li>
</ol>
<h1><b>🧹 Step 1: Data Cleaning</b></h1>
<p>
 import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("imdb_top_1000.csv")

# Clean Runtime
df['Runtime'] = df['Runtime'].str.extract('(\d+)').astype(float)

# Convert Year
df['Year'] = df['Year'].astype(int)

# Handle genres (use primary genre)
df['Primary_Genre'] = df['Genre'].str.split(',').str[0]

# Drop rows with critical missing values
df = df.dropna(subset=['IMDB_Rating', 'No_of_Votes'])
</p>
<h1><b> 📊 Step 2: Exploratory Data Analysis (EDA)</b></h1>
<h2>🎭 Genre vs. Average IMDb Rating</h2>
<p>
 genre_rating = df.groupby('Primary_Genre')['IMDB_Rating'].mean().sort_values(ascending=False)

plt.figure(figsize=(10,6))
sns.barplot(x=genre_rating.values, y=genre_rating.index, palette='coolwarm')
plt.title('Average IMDb Rating by Genre')
plt.xlabel('Average Rating')
plt.ylabel('Genre')
plt.show()
</p>
<p><b>Insight: </b>Drama and Biography genres tend to have the highest average ratings, suggesting that audiences value storytelling and depth.</p>
<h1><b> ⏳ Ratings Over the Years</b></h1>
<p>
 yearly_rating = df.groupby('Year')['IMDB_Rating'].mean()

plt.figure(figsize=(12,6))
sns.lineplot(x=yearly_rating.index, y=yearly_rating.values)
plt.title('Average IMDb Rating Over Time')
plt.xlabel('Year')
plt.ylabel('Rating')
plt.grid(True)
plt.show()
</p>
<p> <b>Insight:</b> There is a notable dip in average ratings post-2010, possibly due to more mass-market releases or increased voting diversity.</p>
<h1><b>💬 Votes vs Ratings</b></h1>
<p>
 plt.figure(figsize=(8,6))
sns.scatterplot(data=df, x='No_of_Votes', y='IMDB_Rating', alpha=0.6)
plt.title('Votes vs IMDb Rating')
plt.xscale('log')
plt.xlabel('Number of Votes (log scale)')
plt.ylabel('Rating')
plt.grid(True)
plt.show()
</p>
<p>Insight: Highly voted movies tend to cluster around ratings between 7.5 and 8.5, suggesting popularity doesn't always mean extreme ratings.</p>
<p>
<h1><b> 🧠 Key Takeaways</b></h1>
<ul>
<li>Top genres: Drama and Biography dominate high-rated films.</li>
<li>Rating trend: Older films have more consistent high ratings.</li>
<li>Popularity vs rating: A high number of votes doesn't guarantee a higher score—audience volume and preference can vary.</li>
</ul>
</p>
<p>
<h1>Tools Used</h1>
Languages: Python
Libraries: Pandas, Matplotlib, Seaborn
Dataset: IMDb Top 1000 Movies (Kaggle)
</p>
