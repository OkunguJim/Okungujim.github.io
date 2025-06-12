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
