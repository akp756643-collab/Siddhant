# Siddhant
Secure login 
Registration Example (bcrypt)
Python
import bcrypt

password = "SecurePassword123!"

hashed_password = bcrypt.hashpw(
    password.encode('utf-8'),
    bcrypt.gensalt()
)

print(hashed_password)
Login Verification Example
Python
import bcrypt

entered_password = input("Enter Password: ")

if bcrypt.checkpw(
        entered_password.encode('utf-8'),
        stored_hash):
    print("Login Successful")
else:
    print("Invalid Credentials")
Flask Registration Route
Python
from flask import Flask, request

app = Flask(__name__)

@app.route('/register', methods=['POST'])
def register():

    username = request.form['username']
    password = request.form['password']

    hashed = bcrypt.hashpw(
        password.encode('utf-8'),
        bcrypt.gensalt()
    )

    # Store in database

    return "User Registered Successfully"
Session Management Example
Python
from flask import session

session['user_id'] = user.id

# Check session
if 'user_id' in session:
    print("User Logged In")
Logout Function
Python
from flask import session

@app.route('/logout')
def logout():

    session.clear()

    return "Logged Out Successfully"
SQL Injection Prevention
Unsafe Query
Python
query = "SELECT * FROM users WHERE username = '" + username + "'"
Safe Query (Parameterized)
Python
cursor.execute(
    "SELECT * FROM users WHERE username=?",
    (username,)
