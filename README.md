
# Register Project(JWT and Refresh Tokens)

This is a Django project for user registration, authentication, and API documentation using Django REST Framework and drf-yasg.


## Installation

1. Clone the repository:

```bash
  git clone https://github.com/Vikasreddyofficial/Registration_Django.git
  cd Registration_Django
```
2. Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate 

```
3. Set up the PostgreSQL database:

```bash
pip install -r requirements.txt

```
4. Set up the PostgreSQL database:

- Ensure you have PostgreSQL installed and running.
- Create a database named Testing and a user postgres with password 8519.

5. Apply the migrations:

```bash
python manage.py migrate

```
6. Run the development server:

```bash
python manage.py runserver

```

## Configuration

The main configuration settings are located in Register/settings.py. Make sure the database settings align with your local PostgreSQL setup.

```bash
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'Testing',
        'USER': 'postgres',
        'PASSWORD': '8519',
        'HOST': 'localhost'
    }
}


```

Security Note:
- The SECRET_KEY in settings.py should be kept secret in a production environment.
- Always set DEBUG = False in production.

## Usage

1. Access the admin panel:

- create a superuser if you haven't already:
```bash
python manage.py createsuperuser
```

- Visit http://127.0.0.1:8000/admin and log in with your superuser credentials.

2. API Documentation:

- Swagger UI: http://127.0.0.1:8000/swagger/
- ReDoc UI: http://127.0.0.1:8000/redoc/

## Refresh Token
A refresh token is a long-lived token used to obtain a new JWT when the original JWT expires. It provides a mechanism for maintaining user sessions without requiring the user to log in again, enhancing security and user experience.
## JWT Token
A JWT (JSON Web Token) is a compact, URL-safe token used for securely transmitting information between parties as a JSON object. JWTs are commonly used in authentication and authorization protocols to verify the identity of users and exchange information between a client (such as a web application) and a server.
## JWT and Refresh Token Flow
``` bash
+--------+                               +-----------+
|        |--(1) Login with credentials-->|           |
|        |                               |           |
|        |<-(2) JWT & Refresh Token------|           |
| Client |                               |  Server   |
|        |--(3) Access resource with JWT>|           |
|        |                               |           |
|        |<-(4) Protected Resource-------|           |
|        |                               |           |
|        |--(5) Request new JWT using -->|           |
|        |     Refresh Token             |           |
|        |                               |           |
|        |<-(6) New JWT (and Refresh)----|           |
+--------+                               +-----------+


```
## API Endpoints
Here's a list of available API endpoints in the project:

1. User Registration:

- URL: /api/register/
- Method: POST
- Description: Register a new user.
- User Login:
2. User Login
- URL: /api/login/
- Method: POST
- Description: Authenticate and obtain JWT tokens.
- Token Refresh:

3. Token Refresh:
- URL: /api/token/refresh/
- Method: POST
- Description: Refresh the access token.

4. User Details:
- URL: /api/user/
- Method: GET, PATCH, DELETE
- Description: Retrieve, update, or delete the authenticated user's details.

5. Welcome Message:
- URL: /api/welcome/
- Method: GET
- Description: Get a welcome message for the authenticated user.

## Dependencies
The project requires the following packages:
- Django: 4.2.13
- djangorestframework: 3.15.2
- djangorestframework-simplejwt: 5.3.1
- drf-yasg: 1.21.7
- psycopg2: 2.9.9
For the full list of dependencies, refer to the requirements.txt file.

## Contributing
Contributions are welcome! Fork the repository, make your changes, and submit a pull request.

## License
This project is licensed under the MIT License - see the LICENSE file for details