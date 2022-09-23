# google-client-app

Flask, Flask-Login, Login with Google, App setup as Google Client

```
pip install -r requirements.txt
```

Initalize the database by running app.py for the first time:

```
python app.py
```

Should see "Initialized the database."

Run the command again to start the Flask web server locally:

```
python app.py
```

## Set up OIDC for Gmail SSO in GCP

- Navigate to Google Cloud "APIs & Services"
- Go to "Credentials"
  - Click "Create Credentials"
    - This is for a "Web Application"
    - Give it a name like "flask-test"
    - Add "https://127.0.0.1:5000" to "Authorized JavaScript Origins"
    - Add "https://127.0.0.1:5000/login/callback" to "Authorized redirect URIs"
    - Save
  - Open the Client ID you just created
    - Copy the "Client ID" and "Client secret" into a `.env` file in the project directory
- Navigate to Google Cloud "Identity Platform"
  - Click "Add a Provider"
    - Select "OpenID Connect" as a provider
    - Choose "Code Flow"
    - Give it a name like "flask-test"
    - Paste in the "Client ID" from the Client created previously
    - The "Issuer (URL)" is "https://accounts.google.com"
    - Paste in the "Client Secret" from the Client created previously
    - Click "Add Domain"
      - Add "127.0.0.1"
      - Add "localhost"
    - Save
