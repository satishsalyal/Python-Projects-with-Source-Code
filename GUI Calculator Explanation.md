# 📌 Simple GUI-Based Calculator (Tkinter)

---

## 📥 1. Importing Required Libraries

```python
import tkinter as tk
from tkinter import messagebox
```

✅ `import tkinter as tk` → Imports the Tkinter module and assigns it a shorter alias `tk` for ease of use.  
✅ `from tkinter import messagebox` → Imports the `messagebox` module from Tkinter, which is used to display error messages in a pop-up dialog.

---

## 🏗 2. Defining the `CalculatorApp` Class

```python
class CalculatorApp:
```

📌 This defines a class `CalculatorApp` that encapsulates the calculator's functionalities.

---

## ⚙️ 3. Initializing the `CalculatorApp`

```python
def __init__(self, root):
```
📌 `__init__` → Constructor method that initializes the calculator app.

```python
self.root = root
self.root.title("Simple Calculator")
self.root.geometry("300x400")
```
✅ `self.root = root` → Assigns the Tkinter root window to an instance variable.  
✅ `self.root.title("Simple Calculator")` → Sets the window title.  
✅ `self.root.geometry("300x400")` → Defines the initial window size.

```python
self.expression = ""
self.entry_text = tk.StringVar()
```
✅ `self.expression = ""` → Stores the current mathematical expression.  
✅ `self.entry_text = tk.StringVar()` → Holds the text that appears in the entry widget.

```python
self.create_widgets()
```
✅ Calls the `create_widgets` method to set up the calculator's UI.

---

## 🎨 4. Creating the UI Elements

```python
def create_widgets(self):
```
📌 This function creates all the UI components.

```python
entry = tk.Entry(self.root, textvariable=self.entry_text, font=("Arial", 18), justify='right', bd=10)
entry.grid(row=0, column=0, columnspan=4, ipadx=10, ipady=10)
```
✅ Creates an entry widget where users can see their input and results.  
✅ `.grid(...)` → Places the entry box at row `0`, spanning across `4` columns.

```python
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3),
    ('C', 5, 0), ('%', 5, 1), ('**', 5, 2), ('Exit', 5, 3)
]
```
📌 Defines a list of buttons where each tuple represents:
- 🔹 `text` → Button label
- 🔹 `row` → The row position in the grid
- 🔹 `col` → The column position in the grid

```python
for (text, row, col) in buttons:
    button = tk.Button(self.root, text=text, font=("Arial", 14), padx=20, pady=20,
                       command=lambda t=text: self.on_button_click(t))
    button.grid(row=row, column=col, sticky='nsew')
```
✅ Creates buttons dynamically using a loop.  
✅ `.grid(...)` → Places the button in the grid layout.  
✅ `sticky='nsew'` → Ensures buttons expand to fill available space.

---

## 🎯 5. Handling Button Clicks

```python
def on_button_click(self, button_text):
```
📌 Handles the logic for when a button is clicked.

```python
if button_text == "C":
    self.expression = ""
```
✅ If the "C" (clear) button is clicked, the expression is reset.

```python
elif button_text == "=":
    try:
        self.expression = str(eval(self.expression))
    except Exception as e:
        messagebox.showerror("Error", "Invalid Expression")
        self.expression = ""
```
✅ If `=` is clicked, evaluates the expression using `eval()`.  
✅ If an error occurs, displays an error message and clears the expression.

```python
elif button_text == "Exit":
    self.root.quit()
```
✅ If `Exit` is clicked, the application closes.

```python
else:
    self.expression += button_text
```
✅ If any other button is clicked, it is appended to `self.expression`.

```python
self.entry_text.set(self.expression)
```
✅ Updates the entry field to reflect the current expression.

---

## 🚀 6. Running the Application

```python
if __name__ == "__main__":
    root = tk.Tk()
    app = CalculatorApp(root)
    root.mainloop()
```

✅ `if __name__ == "__main__":` → Ensures the script runs only when executed directly.  
✅ `root = tk.Tk()` → Creates the main Tkinter window.  
✅ `app = CalculatorApp(root)` → Instantiates the calculator app.  
✅ `root.mainloop()` → Starts the Tkinter event loop, keeping the window open.

---

## 📊 Summary

| **Component** | **Purpose** |
|--------------|------------|
| `tk.Tk()` | Creates the main window |
| `self.root.title("Simple Calculator")` | Sets the window title |
| `self.root.geometry("300x400")` | Defines window size |
| `tk.Entry(...)` | Creates an input field for expressions |
| `buttons` list | Defines the layout for calculator buttons |
| `tk.Button(...)` | Creates buttons dynamically |
| `on_button_click()` | Handles button clicks and performs calculations |
| `eval()` | Evaluates the mathematical expression |
| `messagebox.showerror()` | Displays error messages if the expression is invalid |
| `root.mainloop()` | Runs the event loop to keep the application active |

---

🎉 **Congratulations! 🚀

