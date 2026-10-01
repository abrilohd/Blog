# Tech Pulse Blog

A modern Flask-powered blog application for publishing articles, managing user accounts, and enabling reader interaction through comments and contact messaging.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Flask](https://img.shields.io/badge/Flask-3.x-000000)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.x-red)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3)
![Render](https://img.shields.io/badge/Deployed-Render-46E3B7)

Live demo: https://blog-1dlm.onrender.com/

---

## Overview

Tech Pulse Blog is a full-featured personal blog built with Flask. It allows an admin to create, edit, and delete blog posts, while registered users can sign up, log in, leave comments, and browse posts. The project includes a contact page and a simple email delivery system for inquiries.

---

## Features

- Admin-only blog post creation, editing, and deletion
- User registration and login
- Secure password hashing with Werkzeug
- Blog post comments with user attribution
- Rich-text post writing using Flask-CKEditor
- Responsive Bootstrap-based UI
- Gravatar support for user avatars
- Contact form with email sending via SMTP
- SQLite by default, PostgreSQL-ready via DATABASE_URL
- Ready for deployment with Gunicorn and Render

---

## Tech Stack

- Python
- Flask
- Flask-Login
- Flask-SQLAlchemy
- Flask-WTF
- Flask-CKEditor
- Bootstrap 5
- PostgreSQL / SQLite
- Gunicorn
- Python-dotenv

---

## Project Structure

```text
Blog/
├── main.py                  # Flask application and routes
├── forms.py                 # WTForms for login, register, post, and comment
├── requirements.txt         # Python dependencies
├── Procfile                 # Render/Gunicorn deployment config
├── .gitignore
├── .env.example            # Example environment variables (if present)
├── static/                 # Static assets (CSS, JS, images)
├── templates/              # HTML templates for the blog UI
│   ├── index.html
│   ├── post.html
│   ├── about.html
│   ├── contact.html
│   ├── login.html
│   ├── register.html
│   ├── make-post.html
│   ├── header.html
│   ├── footer.html
│   └── ...
└── posts.db                # SQLite database (created locally)
```

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/abrilohd/Blog.git
cd Blog
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the project root and add the required environment variables:

```env
SECRET_KEY=your_secret_key
DATABASE_URL=sqlite:///posts.db
MY_EMAIL=your_email@gmail.com
MY_PASSWORD=your_app_password
```

If you are using PostgreSQL in production, set `DATABASE_URL` to your Postgres connection string.

5. Run the app:

```bash
python main.py
```

The application will run at:

```text
http://localhost:5000
```

---

## Main Routes

- `/` - Homepage with all published blog posts
- `/register` - User registration
- `/login` - Login page
- `/logout` - Log out current user
- `/about` - About page
- `/contact` - Contact form page
- `/new-post` - Create a new blog post (admin only)
- `/edit-post/<post_id>` - Edit an existing post (admin only)
- `/delete/<post_id>` - Delete a post (admin only)
- `/post/<post_id>` - View a single post and its comments

---

## Database Models

The app uses SQLAlchemy models for:

- `User` - stores user email, password hash, and name
- `BlogPost` - stores the post title, subtitle, date, image URL, and content
- `Comment` - stores comments tied to a post and author

---

## Deployment

This project is configured for Render deployment using Gunicorn.

`Procfile`:

```procfile
web: gunicorn main:app
```

Deployment steps:

1. Push the project to GitHub
2. Connect the repository to Render
3. Set the environment variables in Render
4. Deploy the web service

---

## Environment Variables

Required values:

- `SECRET_KEY` - Flask secret key
- `DATABASE_URL` - SQLite or PostgreSQL database URI
- `MY_EMAIL` - Email used for the contact form
- `MY_PASSWORD` - App password or SMTP password

---

## Notes

This project is designed as a personal tech blog and is easy to extend with:

- category filtering
- tags
- admin dashboard improvements
- user profile pages
- richer commenting and moderation tools
- markdown support for post content

---

## Author

Abrham Gebremedhin

GitHub: https://github.com/abrilohd
Email: abrsh067@gmail.com

---

## License

This project is open for personal and educational use. Add a license file if you plan to publish it publicly under a formal open-source license.
