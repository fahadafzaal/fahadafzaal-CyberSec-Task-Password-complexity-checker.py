scrit file for password checker
import re

# Function to assess password strength
def check_password_strength(password):
    # Criteria definitions
    length_criteria = len(password) >= 8
    uppercase_criteria = bool(re.search(r'[A-Z]', password))
    lowercase_criteria = bool(re.search(r'[a-z]', password))
    digit_criteria = bool(re.search(r'[0-9]', password))
    special_char_criteria = bool(re.search(r'[@$!%*?&#]', password))

    # Initialize strength score
    strength_score = 0
    feedback = []

    # Check each criteria and provide feedback
    if length_criteria:
        strength_score += 1
    else:
        feedback.append("Password must be at least 8 characters long.")
    
    if uppercase_criteria:
        strength_score += 1
    else:
        feedback.append("Password should contain at least one uppercase letter.")
    
    if lowercase_criteria:
        strength_score += 1
    else:
        feedback.append("Password should contain at least one lowercase letter.")
    
    if digit_criteria:
        strength_score += 1
    else:
        feedback.append("Password should contain at least one digit.")
    
    if special_char_criteria:
        strength_score += 1
    else:
        feedback.append("Password should contain at least one special character (e.g., @, $, !, etc.).")

    # Assign strength based on score
    if strength_score == 5:
        strength = "Strong"
    elif strength_score >= 3:
        strength = "Moderate"
    else:
        strength = "Weak"

    # Provide feedback
    return strength, feedback

# Example usage
if __name__ == "__main__":
    password = input("Enter your password: ")
    strength, feedback = check_password_strength(password)

    # Output the password strength and feedback
    print(f"Password Strength: {strength}")
    if feedback:
        print("Feedback:")
        for item in feedback:
            print(f"- {item}")

