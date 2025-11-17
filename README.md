# indian-team-data-analysis
#this is the analysis of indian cricket team performence in last few years
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
data = pd.read_csv("india_team_performance.csv")

# Display basic info
print(data.head())

# 1️ Player Performance Rankings
plt.figure(figsize=(10,5))
sns.barplot(x='Top_Batsman', y='Avg_Run', data=data, palette='Blues_r')
plt.title('Top Batsmen Average Runs by Year')
plt.xlabel('Player')
plt.ylabel('Average Runs')
plt.show()

# 2️ Team Performance Trend
plt.figure(figsize=(10,5))
sns.lineplot(x='Year', y='Win%', data=data, marker='o', color='green')
plt.title('India Team Win Percentage Over Years')
plt.xlabel('Year')
plt.ylabel('Win Percentage')
plt.show()

# 3️ Opponent Analysis
plt.figure(figsize=(8,5))
sns.barplot(x='Opponent', y='Win%', data=data, hue='Year')
plt.title('Performance vs Different Opponents')
plt.xlabel('Opponent')
plt.ylabel('Win Percentage')
plt.show()

# 4️ Best Bowler Average Wickets
plt.figure(figsize=(10,5))
sns.barplot(x='Top_Bowler', y='Avg_Wickets', data=data, palette='Oranges')
plt.title('Top Bowlers Average Wickets')
plt.xlabel('Bowler')
plt.ylabel('Average Wickets per Match')
plt.show()

# 5️ Performance Recommendation
mean_win = data['Win%'].mean()
print(f"📈 Average Win Percentage of India: {mean_win:.2f}%")

if mean_win < 60:
    print(" Recommendation: Focus on bowling strategy and middle-order consistency.")
elif mean_win < 70:
    print("Good performance, but can improve fielding and death bowling.")
else:
    print(" Excellent performance trend. Maintain top order batting consistency.")
