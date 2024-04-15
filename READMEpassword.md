import random
import string

def generate_password(length, uppercase=True, lowercase=True, numbers=True, symbols=True):
    # Define character sets based on user's choices
    chars = ''
    if uppercase:
        chars += string.ascii_uppercase
    if lowercase:
        chars += string.ascii_lowercase
    if numbers:
        chars += string.digits
    if symbols:
        chars += string.punctuation
    
    # Ensure at least one character type is chosen
    if not chars:
        raise ValueError("At least one character type must be selected")
    
    # Generate the password
    password = ''.join(random.choice(chars) for _ in range(length))
    return password

def main():
    try:
        length = int(input("Enter the length of the password: "))
        uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
        lowercase = input("Include lowercase letters? (y/n): ").lower() == 'y'
        numbers = input("Include numbers? (y/n): ").lower() == 'y'
        symbols = input("Include symbols? (y/n): ").lower() == 'y'
        num_passwords = int(input("How many passwords to generate? "))
        
        # Generate and display passwords
        for _ in range(num_passwords):
            password = generate_password(length, uppercase, lowercase, numbers, symbols)
            print("Generated password:", password)
    
    except ValueError as e:
        print("Error:", e)
        print("Please enter valid input.")

if __name__ == "__main__":
    main()
