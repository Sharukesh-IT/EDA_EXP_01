**#Experiment 1: EDA in IPL Dataset**
**Aim:**
To perform Exploratory Data Analysis (EDA) on the IPL matches dataset and derive insights about matches per season, winning teams, toss decisions, and top venues.

**Algorithm / Procedure:**

**1.Import Libraries**
  Import pandas for data handling.
  Import matplotlib and seaborn for visualization.
**2.Load Dataset**
  Use pd.read_csv() to load the IPL matches dataset.
  Check dataset shape using .shape.
  View first 5 rows using .head().
**3.Matches per Season (Univariate Analysis)**
  Group data by season and count matches.
  Plot a bar chart to visualize growth/decline in matches.
**4.Top Winning Teams (Univariate Analysis)**
  Use value_counts() on the winner column.
  Plot top 5 winning teams in a bar chart.
**5.Toss Decisions (Univariate Analysis)**
  Count toss decision preferences (bat vs field).
  Plot results using a bar chart.
**6.Top Venues (Univariate Analysis)**
  Count matches per venue.
  Display top 5 venues with a horizontal bar chart.
**7.Draw Insights**
  Observe patterns in toss decisions.
  Identify teams with consistent winning trends.
  
  **Program**
  # 1. Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import os

plt.style.use("seaborn-v0_8")

sns.set_palette("Set2")

# 2. Load Dataset
file_path = "matches.csv"

if os.path.exists(file_path):
    df = pd.read_csv(file_path)
    print("✅ Loaded real dataset")
else:
    print("⚠️ 'matches.csv' not found. Using sample dataset instead...")
    # Create a small dummy dataset
    data = {
        "id": [1,2,3,4,5,6,7,8],
        "season": [2008,2008,2009,2009,2010,2010,2011,2011],
        "winner": ["MI","CSK","RCB","MI","CSK","KKR","MI","RCB"],
        "toss_decision": ["bat","field","field","bat","field","field","bat","field"],
        "venue": ["Wankhede","Eden Gardens","Chinnaswamy","Wankhede",
                  "Kotla","Eden Gardens","Wankhede","Chinnaswamy"]
    }
    df = pd.DataFrame(data)

# Check dataset shape
print("Dataset Shape:", df.shape)

# View first 5 rows
print("\nFirst 5 Rows:\n", df.head())

# 3. Matches per Season
matches_per_season = df.groupby("season")["id"].count()
plt.figure(figsize=(8,4))
sns.barplot(x=matches_per_season.index, y=matches_per_season.values)
plt.title("Matches per Season")
plt.xlabel("Season")
plt.ylabel("Number of Matches")
plt.show()

# 4. Top Winning Teams
top_winners = df["winner"].value_counts().head(5)
plt.figure(figsize=(8,4))
sns.barplot(x=top_winners.index, y=top_winners.values)
plt.title("Top 5 Winning Teams")
plt.xlabel("Teams")
plt.ylabel("Wins")
plt.show()

# 5. Toss Decisions
toss_decision_counts = df["toss_decision"].value_counts()
plt.figure(figsize=(6,4))
sns.barplot(x=toss_decision_counts.index, y=toss_decision_counts.values)
plt.title("Toss Decision Preference")
plt.xlabel("Decision")
plt.ylabel("Count")
plt.show()

# 6. Top Venues
top_venues = df["venue"].value_counts().head(5)
plt.figure(figsize=(8,4))
sns.barplot(y=top_venues.index, x=top_venues.values, orient="h")
plt.title("Top 5 Venues")
plt.xlabel("Matches")
plt.ylabel("Venue")
plt.show()

# 7. Insights
print("\n--- Insights ---")
print("1. Matches per season show league expansion.")
print("2. MI, CSK, RCB are frequent winners in this sample.")
print("3. Toss decisions show a preference for fielding first.")
print("4. Venues like Wankhede and Eden Gardens host the most matches.")

  **Output**
  <img width="1042" height="582" alt="Screenshot 2025-09-01 183353" src="https://github.com/user-attachments/assets/872065bf-f2ce-4c7c-a9bf-b2014ff792b2" />
   <img width="1028" height="594" alt="Screenshot 2025-09-01 183406" src="https://github.com/user-attachments/assets/153ca142-f8a6-4e4e-9117-1e864218462b" />
   <img width="780" height="595" alt="Screenshot 2025-09-01 183417" src="https://github.com/user-attachments/assets/ac29d85b-986f-47ba-94ab-8eaaead94d9b" />
   <img width="1135" height="591" alt="Screenshot 2025-09-01 183429" src="https://github.com/user-attachments/assets/f0d168b7-53fa-4730-bb80-c0c8456b371c" />


 ** Result**
  This experiment is executed successfully



Highlight the stadiums hosting maximum matches.
