
![FHIRPAD Logo](static/fhirepad.png)

FHIRPAD - FHIR App Platform
FHIRPAD is a web application built to facilitate the discovery and sharing of FHIR-based applications, enhancing healthcare interoperability. Users can register, browse, and manage FHIR apps, with features tailored for both general users and administrators.
Table of Contents

Features
Prerequisites
Installation
Usage
Admin Features
Contributing
License

Features

App Registration and Management: Users can submit, edit, and delete their FHIR apps with details like name, description, logo, launch URL, and more.
App Gallery: Browse and filter apps by categories, OS support, FHIR compatibility, pricing, and designed-for audiences.
Multiple Image Uploads: Upload multiple images for apps to showcase features.
OAuth Authentication: Log in via Google or GitHub, or use local credentials.
Admin Controls:
Manage categories for app filtering.
Edit or delete any app.
Edit user details (username, email, admin status, password reset).


Responsive Design: Works seamlessly on desktop and mobile devices.
Dark Mode: Toggle between light and dark themes.
External Links in New Tabs: Website and Try App buttons open in new windows for better usability.

Prerequisites

Docker and Docker Compose: For containerized deployment.
Python 3.11: If running locally without Docker.
SQLite: Used as the default database (can be swapped for another SQL database).
OAuth Credentials (optional): Google and GitHub client IDs and secrets for OAuth login.

Installation
Using Docker (Recommended)

Clone the Repository:
git clone <repository-url>
cd fhirpad


Set Up Environment Variables:

Copy the .env.example to .env and fill in your OAuth credentials (if using OAuth):cp .env.example .env

Edit .env:FHIRPAD_SECRET_KEY=your-secure-secret-key
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GITHUB_CLIENT_ID=your-github-client-id
GITHUB_CLIENT_SECRET=your-github-client-secret
FLASK_RUN_PORT=5009




Build and Run with Docker Compose:
docker-compose up --build


The app will be available at http://localhost:5009.


Initialize the Database:

Seed the database with initial data, including a default admin user (username: admin, password: admin123):docker-compose exec fhirpad python seed.py





Local Installation (Without Docker)

Clone the Repository:
git clone <repository-url>
cd fhirpad


Set Up a Virtual Environment:
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install Dependencies:
pip install -r requirements.txt


Set Up Environment Variables:

Copy .env.example to .env and configure as above.


Initialize the Database:
export FLASK_APP=app  # On Windows: set FLASK_APP=app
flask db init
flask db migrate -m "Initial schema"
flask db upgrade
python seed.py


Run the Application:
flask run --host=0.0.0.0 --port=5009


Access the app at http://localhost:5009.



Usage

Access the App:

Open http://localhost:5009 in your browser.


Log In:

Use the default admin account: username admin, password admin123 (you’ll be prompted to change the password on first login).
Alternatively, register a new account or log in via Google/GitHub (if OAuth is configured).


Register an App:

Navigate to Register App from the navbar.
Fill in app details (name, description, launch URL, etc.) and upload a logo or app images.


Browse Apps:

Visit the Gallery page to filter and explore apps.
Click Website or Try App to visit external links (opens in a new tab).


Admin Actions (for admin users):

Access Manage Categories, Manage Apps, and Manage Users from the navbar.
Edit or delete categories, apps, or user accounts as needed.



Admin Features

Default Admin Account: Created during seeding (username: admin, password: admin123).
Manage Categories: Add or delete categories for app filtering.
Manage Apps: View, edit, or delete any app in the system.
Manage Users: Edit user details, toggle admin status, force password changes, or reset passwords.

Contributing

Fork the repository.
Create a new branch (git checkout -b feature/your-feature).
Make your changes and commit (git commit -am 'Add your feature').
Push to the branch (git push origin feature/your-feature).
Create a pull request.

Please ensure your code follows the project’s style guidelines and includes appropriate tests.
License
This project is licensed under the MIT License. See the LICENSE file for details.
