# Nested-list
This project demonstrates the use of nested if-else statements in Python to evaluate how alphabetical letters were used to identify the top and lowest scored students.The information was used to to plot bar, pie-chart, and histogram.

students = [
    ["Alice", 85],
    ["Bob", 92],
    ["Charlie", 78],
    ["David", 92],
    ["Eve", 78]
]

scores = [s[1] for s in students]
highest = max(scores)
lowest = min(scores)
highest_students = [s[0] for s in students if s[1] == highest]
lowest_students = [s[0] for s in students if s[1] == lowest]

print("Highest scorer(s):")
for name in highest_students:
    print(name)

print("\nLowest scorer(s):")
for name in lowest_students:
    print(name)

from collections import defaultdict

score_dict = defaultdict(list)
for name, score in students:
    score_dict[score].append(name)

print("\nStudents with same scores:")
for score, names in score_dict.items():
    if len(names) > 1:
        names.sort()
        for i, name in enumerate(names):
            label = chr(65 + i)  # A, B, C...
            print(f"{label}. {name} (Score: {score})")


import matplotlib.pyplot as plt
from collections import defaultdict

# Extract scores
scores = [s[1] for s in students]
names = [s[0] for s in students]

# ---------- Histogram ----------
plt.figure()
plt.hist(scores, bins=5, color='skyblue', edgecolor='black')
plt.title("Histogram of Scores")
plt.xlabel("Scores")
plt.ylabel("Number of Students")
plt.show()

# ---------- Bar Chart ----------
plt.figure()
plt.bar(names, scores, color='orange')
plt.title("Bar Chart of Student Scores")
plt.xlabel("Students")
plt.ylabel("Scores")
plt.show()

#   Pie Chart 
count frequency of scores
score_count = defaultdict(int)
for score in scores:
    score_count[score] += 1

labels = [str(score) for score in score_count.keys()]
sizes = score_count.values()

plt.figure()
plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.title("Pie Chart of Score Distribution")
plt.show()
