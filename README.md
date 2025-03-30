# Password Strength Checker

## Disclaimer
This project is intended for educational and ethical security improvement purposes only. Unauthorized use of password strength evaluation tools for malicious activities is illegal and punishable by law. Always ensure ethical and legal compliance when using this tool.

## Project Objective
Develop a Python-based password strength checker that evaluates password security using a point-based system. The evaluation follows NIST (National Institute of Standards and Technology) guidelines, which recommend:

- A minimum of 8 characters for passwords
- Encouraging the use of passphrases instead of complex character combinations
- Checking against common password lists to prevent weak choices
- Avoiding arbitrary complexity rules (e.g., requiring special characters)
- Allowing copy-paste and visibility toggles for usability

The goal is to help users create stronger, more secure passwords while adhering to industry standards.

## Skills Learned
- Python Programming
- Secure Authentication Practices
- Basic Cybersecurity Principles

## Tools Used
- Visual Studio Code

## Code
```python
import string

password = input("Enter your password: ")

# Initialize score
score = 0 

# Open and read the common password list
with open(r'C:\Users\Custom\Documents\Python\pwd checker\common.txt', 'r') as f:
    common = f.read().splitlines()

# Check if the password is in the common password list
if password in common:
    print("\nPassword was found in a common list. Change password immediately!!!")
    exit()

# Check if the password contains at least one lowercase, uppercase, special character, and digit
lower_case = any(c in string.ascii_lowercase for c in password)
upper_case = any(c in string.ascii_uppercase for c in password)
special = any(c in string.punctuation for c in password)
digits = any(c in string.digits for c in password)

# Length of the password
length = len(password)

# Check the length conditions
if length >= 12:
    score += 1  # Length of 12 or more
if length >= 16:
    score += 1  # Length of 16 or more

# Check if each character type is present and add 1 point for each
if lower_case:
    score += 1  # Lowercase character is present
if upper_case:
    score += 1  # Uppercase character is present
if special:
    score += 1  # Special character is present
if digits:
    score += 1  # Digit is present

# Output the results
print(f"\nPassword length is {length}. Adding {score} point(s)!")
print("----------------------------------------")

# Display the password strength based on the score
if score == 0:
    print(f"The password is Very Weak!! Score: {score}/6")
elif score == 1:
    print(f"The password is Weak! Score: {score}/6")
elif score == 2:
    print(f"The password is Fair! Score: {score}/6")
elif score == 3:
    print(f"The password is Moderate! Score: {score}/6")
elif score == 4:
    print(f"The password is Strong! Score: {score}/6")
elif score == 5:
    print(f"The password is Very Strong! Score: {score}/6")
elif score == 6:
    print(f"The password is Extremely Strong! Score: {score}/6")
```
