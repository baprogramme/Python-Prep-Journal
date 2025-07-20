**A simple user login system that checks the username and password.**
```python
# User login system

# Predefined username and password
stored_username = "admin"
stored_password = "password123"

# Take user input
username = input("Enter username: ")
password = input("Enter password: ")

# Check login credentials
if username == stored_username:
    if password == stored_password:
        print("Login successful!")
    else:
        print("Incorrect password.")
else:
    print("Username not found.")
