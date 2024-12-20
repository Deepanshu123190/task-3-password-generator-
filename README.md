import random
import string

def generate_password(length):
    if length < 4:
        print("Password length should be at least 4 for a secure password.")
        return None

    # Characters to include in the password
    all_characters = string.ascii_letters + string.digits + string.punctuation

    # Ensure the password has at least one letter, digit, and special character
    password = [
        random.choice(string.ascii_lowercase),
        random.choice(string.ascii_uppercase),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ]

    # Fill the rest of the password length with random characters
    password += random.choices(all_characters, k=length - 4)

    # Shuffle to ensure randomness
    random.shuffle(password)

    return ''.join(password)

# Prompt user for password length
try:
    length = int(input("Enter the desired length of your password: "))
    generated_password = generate_password(length)
    if generated_password:
        print(f"Your generated password is: {generated_password}")
except ValueError:
    print("Invalid input. Please enter a numeric value.")
