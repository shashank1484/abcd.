import mysql.connector

# Connect to the database
cnx = mysql.connector.connect(
    host="localhost",
    user="username",
    password="password",
    database="database"
)
cursor = cnx.cursor()

# Prompt the user for a username
username = input("Enter a username: ")

# Construct and execute the SQL query
query = f"SELECT password FROM users WHERE username = '{username}'"
cursor.execute(query)

# Print the results
result = cursor.fetchone()
if result:
    print(f"The password for user '{username}' is: {result[0]}")
else:
    print(f"No user with the username '{username}' was found.")

# Close the connection
cnx.close()