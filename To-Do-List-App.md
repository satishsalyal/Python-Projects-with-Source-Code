# 📝 To-Do List App (Python + Tkinter)

A simple **Task Manager App** built with **Python Tkinter GUI**.  
It allows users to **Add, Update, Delete, and Clear tasks** with a clean and user-friendly interface.  

---

## ✨ Features
✅ Add new tasks  
✅ Update existing tasks  
✅ Delete selected tasks  
✅ Clear all tasks at once  
✅ Scrollable task list  

---

## 🚀 Demo (UI Preview)

> *(Replace the below image link with your actual screenshot)*  

![App Screenshot](https://via.placeholder.com/400x500.png?text=To-Do+List+App)

---

## 🛠️ Technologies Used
- ![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)  
- ![Tkinter](https://img.shields.io/badge/Tkinter-GUI-orange)  

---

## 📂 Project Structure
```bash
📦 ToDoListApp
 ┣ 📜 todo.py        # Main application script
 ┣ 📜 README.md      # Project documentation
 ┗ 📜 requirements.txt (optional)
# 💻 Code Overview

```python
import tkinter as tk
from tkinter import messagebox

class ToDoApp:
    def __init__(self, root):
        self.root = root
        self.root.title("📝 To-Do List App")
        self.root.geometry("400x500")

        # UI Components
        self.task_entry = tk.Entry(self.root, font=("Arial", 14))
        self.task_entry.pack(pady=10, fill=tk.X, padx=20)

        self.task_listbox = tk.Listbox(self.root, width=45, height=15)
        self.task_listbox.pack(pady=10)

        tk.Button(self.root, text="Add Task", command=self.add_task).pack()
        tk.Button(self.root, text="Update Task", command=self.update_task).pack()
        tk.Button(self.root, text="Delete Task", command=self.delete_task).pack()
        tk.Button(self.root, text="Clear All", command=self.clear_all).pack()
    
    # Functions for Add, Update, Delete, Clear
    def add_task(self): ...
    def update_task(self): ...
    def delete_task(self): ...
    def clear_all(self): ...

if __name__ == "__main__":
    root = tk.Tk()
    app = ToDoApp(root)
    root.mainloop()
```
