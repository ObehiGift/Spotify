# Spotify - Exploratory Data Analysis

# 📃Introduction
This project analyzes my Spotify spotify listening data to uncover patterns in my music habits. Using Python, I explored my top artistes, tracks, and how my listening behaviour varies over time.

# 🧵Background
Spotify provides a detailed record of listening activity, which can be used to analyze personal music references. I used this dataset to gain insights into how, when, and what i listen to the most.

# 🛠Tools Used
- Python
- Pandas for data manipulation
- Matplotlib and Seaborn for data visualization
- Jupyter Notebook for running and documenting the analysis

# 📍Analysis
This project dives into my spotify streaming history from August 2024 to July 2025 to uncover meaningful patterns in my listening habits. The dataset didn't require any cleaning aside the conversion of the endTime column fron an object to a datetime, so i jumoed straight to Exploratory Data Analysis (EDA) using Python and Visualizations.

Here's a breakdown of what I explored
- **Listening Volume:** I calculated the **total listening time in hours** to understand how much time I've spent on Spotify overall, I also determined the **average listening time per session**, providing a sense of hoe long I typically stream music at a time.
- **Session Extremes:** To identify standout sessions, I found the **longest and shortest listening sessions** based on duration.
- **Unique Content:** I analyzed how many **individual tracks and distinct artists** I've listened to, showing the diversity in my mustic artistes.
- **Top Content:** I uncovered the **most played artistes and most played tracks** across all sessions. Then, using horizontal bar charts, I visualized my **top 10 mosst played tracks** and **top 10 artists**, offering a clear view of my music perferences.

```
python
# how has my listening habit changed over the month?
df['month_str'] = df['endTime'].dt.strftime('%b')
df['month_int'] = df['endTime'].dt.strftime('%m')
m = df.groupby(['month_str','month_int'])['seconds_played'].sum().reset_index().sort_values('month_int')

plt.figure(figsize=(12,5))
plt.plot('month_str','seconds_played', data=m, marker = 'o')

for i,value in enumerate(m['seconds_played']):
    plt.text(m['month_str'].iloc[i],m['seconds_played'].iloc[i],f'{value:.0f}', ha='left', va = 'bottom', fontsize=10)
ax=plt.gca()
plt.ylabel('Total Seconds Played')
plt.title('Monthly Spotify Listening Time')
sns.despine()
plt.savefig('monthly_spotify_listening_time',dpi=300)
plt.show()
```
