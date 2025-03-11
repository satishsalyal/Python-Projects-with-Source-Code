# 🔐 Python Password Generator

A **Password Generator** is a simple program that creates **strong and secure passwords**. This program ensures security by including a mix of:

✅ **Uppercase letters**  
✅ **Lowercase letters**  
✅ **Numbers**  
✅ **Special characters**  

---

## 📌 Features

✔ Generates **random passwords** of user-defined length.  
✔ Supports **uppercase, lowercase, digits, and special characters**.  
✔ Ensures passwords are **strong and difficult to guess**.  
✔ **User input** support for customization.  

---

## 🌟 Required Modules

This program uses built-in Python modules:

- `random` → Selects random characters.
- `string` → Provides character sets like letters, digits, and symbols.


---

## 🗋 Code Implementation

### ✨ **Python Script: Password Generator**

```python
import random
import string

def generate_password(length=12, use_digits=True, use_special_chars=True):
    """
    Generates a random password based on user preferences.
    
    Parameters:
    length (int): Length of the password (default is 12)
    use_digits (bool): Whether to include numbers
    use_special_chars (bool): Whether to include special characters
    
    Returns:
    str: The generated password
    """
    if length < 4:
        raise ValueError("Password length must be at least 4 characters.")
    
    letters = string.ascii_letters  # Includes uppercase and lowercase letters
    digits = string.digits if use_digits else ""  # Numbers 0-9 if enabled
    special_chars = string.punctuation if use_special_chars else ""  # Special symbols if enabled
    
    password_characters = letters + digits + special_chars
    if not password_characters:
        raise ValueError("At least one character set (letters, digits, special) must be enabled.")
    
    password = [
        random.choice(string.ascii_uppercase),  # At least one uppercase letter
        random.choice(string.ascii_lowercase),  # At least one lowercase letter
    ]
    
    if use_digits:
        password.append(random.choice(string.digits))  # At least one digit
    
    if use_special_chars:
        password.append(random.choice(string.punctuation))  # At least one special character
    
    password += [random.choice(password_characters) for _ in range(length - len(password))]
    
    random.shuffle(password)  # Shuffle to ensure randomness
    
    return "".join(password)  # Convert list to string

# User Input & Execution
if __name__ == "__main__":
    password_length = int(input("Enter password length: "))
    include_digits = input("Include numbers? (yes/no): ").strip().lower() == "yes"
    include_special_chars = input("Include special characters? (yes/no): ").strip().lower() == "yes"
    
    generated_password = generate_password(password_length, include_digits, include_special_chars)
    print(f"Generated Password: {generated_password}")
```

---

## 📉 Explanation of Code

### 🔹 Import Required Modules

```python
import random
import string
```

- `random` → Used for generating **random characters**.
- `string` → Provides **pre-defined character sets** (letters, digits, symbols).

### 🔹 Define the Function

```python
def generate_password(length=12, use_digits=True, use_special_chars=True):
```

- `length`: Defines **password length** *(default = 12)*.
- `use_digits`: If **True**, includes **numbers** *(default = True)*.
- `use_special_chars`: If **True**, includes **special characters** *(default = True)*.

### 🔹 Define Character Sets

```python
letters = string.ascii_letters  # A-Z, a-z
```

- `string.ascii_letters` → Includes **uppercase & lowercase** letters.
- `string.digits` → Includes **0-9** *(if enabled)*.
- `string.punctuation` → Includes **special characters** *(if enabled)*.

### 🔹 Ensure Strong Password Composition

```python
password = [
    random.choice(string.ascii_uppercase),  # At least one uppercase letter
    random.choice(string.ascii_lowercase),  # At least one lowercase letter
]
```

This ensures **password strength** by including:

✅ **1 Uppercase Letter**  
✅ **1 Lowercase Letter**  
✅ **1 Digit (if enabled)**  
✅ **1 Special Character (if enabled)**  

### 🔹 Fill Remaining Characters & Shuffle

```python
password += [random.choice(password_characters) for _ in range(length - len(password))]
random.shuffle(password)
```

- **Fills** the password with **random choices** from the allowed character set.
- Uses `random.shuffle()` to **remove predictable patterns**.

### 🔹 Convert List to String & Return

```python
return "".join(password)
```

Converts the **list** into a **string** and returns the **final password**.

---

## 🖥 User Input & Execution

```python
if __name__ == "__main__":
    password_length = int(input("Enter password length: "))
    include_digits = input("Include numbers? (yes/no): ").strip().lower() == "yes"
    include_special_chars = input("Include special characters? (yes/no): ").strip().lower() == "yes"
    
    generated_password = generate_password(password_length, include_digits, include_special_chars)
    print(f"Generated Password: {generated_password}")
```

- **Takes user input** for password length, numbers, and special characters.
- Calls `generate_password()` with the user’s **preferences**.
- Prints the **final password**.

---

## 💻 Sample Output

```sh
Enter password length: 12
Include numbers? (yes/no): yes
Include special characters? (yes/no): yes
Generated Password: G3#dM9!zXp2a
```

---

🚀 **Happy Coding!** 🚀

