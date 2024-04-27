
import random

def generate_password(length, has_uppercase=True, has_lowercase=True, has_numbers=True, has_symbols=True):
  """
  Generates a random password based on user-specified criteria.

  Args:
      length (int): The desired length of the password.
      has_uppercase (bool, optional): Include uppercase letters. Defaults to True.
      has_lowercase (bool, optional): Include lowercase letters. Defaults to True.
      has_numbers (bool, optional): Include numbers. Defaults to True.
      has_symbols (bool, optional): Include symbols. Defaults to True.

  Returns:
      str: The generated password.
  """

  # Define character sets
  char_sets = []
  if has_uppercase:
    char_sets.append("ABCDEFGHIJKLMNOPQRSTUVWXYZ")
  if has_lowercase:
    char_sets.append("abcdefghijklmnopqrstuvwxyz")
  if has_numbers:
    char_sets.append("0123456789")
  if has_symbols:
    char_sets.append("!@#$%^&*()_-+=~`{[]}|\\:;'<,>.?/ ")

  # Validate at least 3 character types
  if len(char_sets) < 3:
    print("Password must include at least 3 character types (uppercase, lowercase, numbers, or symbols).")
    return

  # Combine all character sets
  all_chars = ''.join(char_sets)

  # Generate password with random characters
  password = ''.join(random.sample(all_chars, length))

  return password

# Get user input for password length
while True:
  try:
    length = int(input("Enter desired password length (minimum 8 characters): "))
    if length < 8:
      print("Password length must be at least 8 characters.")
    else:
      break
  except ValueError:
    print("Invalid input. Please enter a number.")

# Generate password
password = generate_password(length)
print("Generated password:", password)


output:  

Enter desired password length (minimum 8 characters): 10
Generated password: Fq$2N3&Jbk
