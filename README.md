#quize-score
import pandas as pd
import matplotlib.pyplot as plt

# 1. Initialize empty list to collect user data
data = []

print("Welcome to the Quiz Score Collector!\n")

# 2. Collect data for n users using for-loop
n=int(input("Enter the number of Users: "))
for i in range(n):
    name = input("Enter your name: ")
    score = int(input("Enter your quiz score (0 to 100): "))

    # 3. Use dictionary to store individual record
    user_record = {
        "Name": name,
        "Score": score
    }
    #Adding the dictionary to a data structure(list)
    data.append(user_record)


# 4. Convert list of dictionaries to DataFrame
df = pd.DataFrame(data)

# 5. Export data as CSV and Excel
df.to_csv("quiz_scores.csv", index=False)
df.to_excel("quiz_scores.xlsx", index=False)

print("\nData saved to 'quiz_scores.csv' and 'quiz_scores.xlsx'.")

# 6. Data Visualization
plt.figure(figsize=(8, 5))
plt.bar(df['Name'], df['Score'], color='skyblue')
plt.title("Quiz Scores by User")
plt.xlabel("User")
plt.ylabel("Score")
plt.ylim(0, 100)
plt.tight_layout()
plt.savefig("quiz_scores_plot.png")
plt.show()
