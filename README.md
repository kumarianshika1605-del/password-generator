import random
import secrets
import string

def generate_password(length):
    """ Generates a random password of the specified length."""
    if length < 5:
        raise ValueError("Password length should be at least 5 character for better security.")
    
    

    pools = [
        random.choice(string.ascii_uppercase),
        random.choice(string.ascii_lowercase),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ] 

    password_chars = [secrets.choice(pool)for pool in pools]

    all_chars = ''.join(pools)
    remaining = length - len(password_chars)
    for _ in range(remaining):
        password_chars.append(secrets.choice(all_chars))

    secrets.SystemRandom().shuffle(password_chars)
    return ''.join(password_chars)


if  __name__== "__main__":
     try:
         user_length = int(input("Enter desired password length:" ))
         generated_password = generate_password(user_length)
         print("Generated password:", generated_password)
     except ValueError:
         print("inva;lid input. Please enter a numeric value.")


