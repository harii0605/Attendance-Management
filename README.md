import numpy as np
import pandas as pd
import matplotlib.pyplot as plt


students = ["Amit", "Neha", "Rahul", "Pooja", "Karan"]

days = ["Day1", "Day2", "Day3", "Day4", "Day5"]

attendance = np.array([
    [1, 1, 1, 0, 1],
    [1, 0, 1, 1, 1],
    [0, 1, 1, 1, 0],
    [1, 1, 1, 1, 1],
    [0, 1, 0, 1, 1]
])

attendance_df = pd.DataFrame(attendance, index=students, columns=days)

print("Attendance Record:\n")
print(attendance_df)


attendance_df["Total Present"] = attendance_df.sum(axis=1)
attendance_df["Total Absent"] = len(days) - attendance_df["Total Present"]
attendance_df["Attendance %"] = (attendance_df["Total Present"] / len(days)) * 100

print("\nAttendance Summary:\n")
print(attendance_df)



daily_present = attendance_df[days].sum()

plt.figure(figsize=(8,4))
plt.plot(days, daily_present, marker='o')
plt.title("Daily Attendance")
plt.xlabel("Days")
plt.ylabel("Students Present")
plt.grid(True)
plt.show()



plt.figure(figsize=(8,4))
plt.bar(students, attendance_df["Attendance %"])
plt.title("Student Attendance Percentage")
plt.xlabel("Students")
plt.ylabel("Attendance %")
plt.show()
