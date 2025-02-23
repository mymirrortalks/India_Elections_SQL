# India_Elections_SQL
# India General Election Result Analysis 2024

## 📌 Overview
This project provides a comprehensive SQL-based analysis of the **India General Election Results 2024**. It includes queries to explore constituency-wise details, party performance, voter turnout statistics, and state-wise trends. The dataset enables data analysts to derive meaningful insights and trends from the election results.

## 🏛 Database Schema & Structure
The database consists of multiple normalized tables:

### **1️⃣ constituencywise_details**
- Stores detailed information about each candidate and the number of votes received.
- **Columns:** `S_No`, `Candidate`, `Party`, `EVM_Votes`, `Postal_Votes`, `Total_Votes`, `%_of_Votes`, `Constituency_ID`

### **2️⃣ constituencywise_results**
- Contains consolidated results for each constituency.
- **Columns:** `S_No`, `Parliament_Constituency`, `Constituency_Name`, `Winning_Candidate`, `Total_Votes`, `Margin`, `Constituency_ID`, `Party_ID`

### **3️⃣ partywise_results**
- Displays party-wise seat count.
- **Columns:** `Party`, `Won`, `Party_ID`

### **4️⃣ states**
- Maps constituencies to states.
- **Columns:** `State_ID`, `State`

## 🔍 Key SQL Queries for Analysis
### 🏆 Winning Trends
#### 1️⃣ Find the party that won the most seats:
```sql
SELECT Party, COUNT(Won) AS SeatsWon FROM partywise_results GROUP BY Party ORDER BY SeatsWon DESC;
```
#### 2️⃣ Highest margin victories:
```sql
SELECT Constituency_Name, Winning_Candidate, Margin FROM constituencywise_results ORDER BY Margin DESC LIMIT 10;
```

### 📊 Voter Turnout & Participation
#### 3️⃣ Constituencies with highest voter turnout:
```sql
SELECT Constituency_Name, SUM(Total_Votes) AS TotalVotes FROM constituencywise_results GROUP BY Constituency_Name ORDER BY TotalVotes DESC LIMIT 10;
```
#### 4️⃣ Party-wise total votes received:
```sql
SELECT Party, SUM(Total_Votes) AS TotalVotes FROM constituencywise_details GROUP BY Party ORDER BY TotalVotes DESC;
```

### 🌍 State-Wise Analysis
#### 5️⃣ State with the highest average winning margin:
```sql
SELECT s.State, AVG(Margin) AS AvgWinningMargin FROM constituencywise_results c JOIN states s ON c.Constituency_ID = s.State_ID GROUP BY s.State ORDER BY AvgWinningMargin DESC LIMIT 5;
```
#### 6️⃣ Leading and trailing candidates in each state:
```sql
SELECT s.State, c.Constituency_Name, c.Leading_Candidate, c.Trailing_Candidate FROM statewise_results c JOIN states s ON c.State_ID = s.State_ID ORDER BY s.State;
```

## 🚀 Installation & Setup
1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/india-election-analysis.git
   ```
2. **Import the SQL database** into MySQL or PostgreSQL.
3. **Run queries** to analyze election results using the provided scripts.

## 📢 Contribution Guidelines
We welcome contributions! Feel free to:
- Add more complex analytical queries.
- Optimize query performance.
- Build interactive data visualizations using Python, Tableau, or Power BI.


📊 **Stay tuned for more data-driven election insights!**

