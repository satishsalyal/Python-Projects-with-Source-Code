🔐 Python Password Generator
A Password Generator is a simple program that creates strong and secure passwords. This program ensures security by including a mix of:

✅ Uppercase letters

✅ Lowercase letters

✅ Numbers

✅ Special characters


📌 Features

✔ Generates random passwords of user-defined length.

✔ Supports uppercase, lowercase, digits, and special characters.

✔ Ensures passwords are strong and difficult to guess.

✔ User input support for customization.

📜 Required Modules
We use the following built-in Python modules:

random → Selects random characters.
string → Provides character sets like letters, digits, and symbols.
python
Copy
Edit
import random  # Importing random module for generating random characters
import string  # Importing string module for predefined character sets
📝 Code Implementation
🚀 Python Script: Password Generator
python
Copy
Edit
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

    # Defining character sets
    letters = string.ascii_letters  # Includes both uppercase and lowercase letters
    digits = string.digits if use_digits else ""  # 0-9 if enabled
    special_chars = string.punctuation if use_special_chars else ""  # Special symbols if enabled

    # Ensure at least one of each selected character type is included
    password_characters = letters + digits + special_chars
    if not password_characters:
        raise ValueError("At least one character set (letters, digits, special) must be enabled.")

    # Create password ensuring at least one uppercase, one lowercase, one digit, and one special character
    password = [
        random.choice(string.ascii_uppercase),  # At least one uppercase letter
        random.choice(string.ascii_lowercase),  # At least one lowercase letter
    ]

    if use_digits:
        password.append(random.choice(string.digits))  # At least one digit
    
    if use_special_chars:
        password.append(random.choice(string.punctuation))  # At least one special character

    # Fill the remaining password length with random choices from the selected character set
    password += [random.choice(password_characters) for _ in range(length - len(password))]

    # Shuffle the password to remove predictable patterns
    random.shuffle(password)

    return "".join(password)  # Convert list to string and return

# User Input & Execution
if __name__ == "__main__":
    password_length = int(input("Enter password length: "))
    include_digits = input("Include numbers? (yes/no): ").strip().lower() == "yes"
    include_special_chars = input("Include special characters? (yes/no): ").strip().lower() == "yes"

    generated_password = generate_password(password_length, include_digits, include_special_chars)
    print(f"Generated Password: {generated_password}")
📌 Explanation of Code
🔹 Import Required Modules
python
Copy
Edit
import random
import string
random is used for generating random characters.
string provides pre-defined character sets like letters, digits, and symbols.
🔹 Define the Function
python
Copy
Edit
def generate_password(length=12, use_digits=True, use_special_chars=True):
length: Sets password length (default = 12).
use_digits: If True, includes numbers (default = True).
use_special_chars: If True, includes special characters (default = True).
🔹 Character Set Definitions
python
Copy
Edit
letters = string.ascii_letters  # Includes uppercase and lowercase letters
digits = string.digits if use_digits else ""  # Adds digits if enabled
special_chars = string.punctuation if use_special_chars else ""  # Adds symbols if enabled
string.ascii_letters → A-Z, a-z
string.digits → 0-9 (if enabled)
string.punctuation → !@#$%^&*() (if enabled)
🔹 Ensure Strong Password Composition
python
Copy
Edit
password = [
    random.choice(string.ascii_uppercase),  # Ensures at least one uppercase letter
    random.choice(string.ascii_lowercase),  # Ensures at least one lowercase letter
]
if use_digits:
    password.append(random.choice(string.digits))  # Ensures at least one number
if use_special_chars:
    password.append(random.choice(string.punctuation))  # Ensures at least one special character
This guarantees that the password contains at least:
✅ 1 uppercase letter
✅ 1 lowercase letter
✅ 1 digit (if enabled)
✅ 1 special character (if enabled)

🔹 Randomly Fill Remaining Characters
python
Copy
Edit
password += [random.choice(password_characters) for _ in range(length - len(password))]
Fills the rest of the password with randomly chosen characters from the allowed sets.
🔹 Shuffle the Password to Increase Security
python
Copy
Edit
random.shuffle(password)
This removes predictable patterns (e.g., first character always uppercase).
🔹 Convert List to String & Return
python
Copy
Edit
return "".join(password)
Joins the list into a single string and returns the final password.
🖥 User Input & Execution
python
Copy
Edit
if __name__ == "__main__":
    password_length = int(input("Enter password length: "))
    include_digits = input("Include numbers? (yes/no): ").strip().lower() == "yes"
    include_special_chars = input("Include special characters? (yes/no): ").strip().lower() == "yes"

    generated_password = generate_password(password_length, include_digits, include_special_chars)
    print(f"Generated Password: {generated_password}")
Takes user input for password length, numbers, and special characters.
Calls generate_password() with the user’s preferences.
Prints the final password.
🛠 Sample Output
nginx
Copy
Edit
Enter password length: 12
Include numbers? (yes/no): yes
Include special characters? (yes/no): yes
Generated Password: G3#dM9!zXp2a
