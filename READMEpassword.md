import random
import string

def generate_password(length, uppercase=True, lowercase=True, numbers=True, symbols=True):
    characters = ''
    if uppercase:
        characters += string.ascii_uppercase
    if lowercase:
        characters += string.ascii_lowercase
    if numbers:
        characters += string.digits
    if symbols:
        characters += string.punctuation
    
    if not characters:
        return "Error: No character types selected for password generation."
    
    password = ''.join(random.choice(characters) for _ in range(length))
    
    # Ensure that the generated password meets requested criteria
    while (uppercase and not any(char.isupper() for char in password)) \
            or (lowercase and not any(char.islower() for char in password)) \
            or (numbers and not any(char.isdigit() for char in password)) \
            or (symbols and not any(char in string.punctuation for char in password)):
        password = ''.join(random.choice(characters) for _ in range(length))
    
    return password

def generate_multiple_passwords(count, length, uppercase=True, lowercase=True, numbers=True, symbols=True):
    passwords = []
    for _ in range(count):
        password = generate_password(length, uppercase, lowercase, numbers, symbols)
        passwords.append(password)
    return passwords

# Example usage:
password_length = 12
password_count = 5
generated_passwords = generate_multiple_passwords(password_count, password_length)

for i, password in enumerate(generated_passwords):
    print(f"Password {i+1}: {password}")