# 🍽️ Atlanta Food Finder: Full-Stack Dining Discovery & Recommendation Web App

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-Full--Stack-092E20.svg?logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Google Cloud](https://img.shields.io/badge/Google%20Maps-Geocoding%20API-4285F4.svg?logo=googlemaps&logoColor=white)](https://developers.google.com/maps)
[![Course](https://img.shields.io/badge/Georgia%20Tech-CS%202340%20Objects%20%26%20Design-B3A369.svg)](https://www.gatech.edu/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> A full-stack web application designed for students and Atlanta residents to discover, review, search, and bookmark local restaurants. Built with **Django**, **SQLite**, and the **Google Maps Geocoding API** to automatically resolve spatial coordinates, support granular multi-criteria filtering, and provide personalized user dining collections.

---

## 📌 Features

- 🔍 **Dynamic Discovery & Search**: Filter Atlanta eateries by cuisine type, minimum customer ratings, location, and keywords.
- 🗺️ **Automated Spatial Geocoding**: Integrated with the **Google Maps Geocoding & Places API** to automatically translate street addresses into latitude and longitude coordinates upon entry.
- 👤 **Secure User Authentication**: Complete account management system with user registration, authentication guards, session management, and password validation.
- ❤️ **Personalized Bookmarks & Favorites**: Dynamic one-click restaurant saving and removal tied to authenticated user profiles.
- 📱 **Responsive UI**: Custom styled templates engineered for intuitive browsing across desktop and mobile form factors.

---

## 🏗️ Architecture & Database Schema

```
┌─────────────────────────────────────────────────────────────┐
│                       Client Browser                        │
└──────────────────────────────┬──────────────────────────────┘
                               │ HTTP / Django Templates
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                    Django Application Layer                 │
│  - User Auth & Session Management                           │
│  - Restaurant Filtering & Search Views                      │
│  - Favorites Controller                                     │
└──────────────┬──────────────────────────────┬───────────────┘
               │                              │
               ▼                              ▼
 ┌───────────────────────────┐  ┌───────────────────────────┐
 │   Google Geocoding API    │  │       SQLite Database     │
 │   - Address to Coordinates│  │  - User Table             │
 │   - Place ID Resolution   │  │  - Restaurant Table       │
 └───────────────────────────┘  │  - Favorite Relationship  │
                                └───────────────────────────┘
```

### Relational Model Structure
- **`Restaurant`**:
  - `name`, `cuisine_type`, `location`, `rating`, `description`, `place_id`
  - `latitude`, `longitude` (auto-populated via Google Geocoding API upon model save)
- **`Favorite`**:
  - Many-to-one relationship bridging `User` and `Restaurant` models.

---

## 🛠️ Tech Stack

- **Backend**: Python 3.10+, Django MVC framework
- **Database**: SQLite (Development / Testing)
- **APIs**: Google Maps Platform (Geocoding API, Places API)
- **Frontend**: Django Template Language (DTL), HTML5, CSS3, JavaScript

---

## 📂 Repository Structure

```
atlanta-food-finder/
├── atlanta_food_finder/     # Core Django project settings and routing
│   ├── settings.py          # Configuration and installed apps
│   ├── urls.py              # Root URL dispatcher
│   └── wsgi.py              # WSGI entry point
├── restaurants/             # Primary dining application
│   ├── models.py            # Restaurant and Favorite relational models
│   ├── views.py             # Controller logic for search, auth, and favorites
│   ├── utils.py             # Google Geocoding API integration helpers
│   ├── urls.py              # Restaurant application routes
│   └── templates/           # Custom HTML templates (home, search, favorites, auth)
├── static/                  # Stylesheets, images, and front-end assets
├── manage.py                # Django CLI utility
└── db.sqlite3               # Local database
```

---

## 🚀 Getting Started

### 1. Prerequisites
- Python 3.10+
- `pip` package manager

### 2. Installation
```bash
# Clone the repository
git clone https://github.com/byohros6/atlanta-food-finder.git
cd atlanta-food-finder

# (Optional) Create and activate virtual environment
python -m venv venv
# On Windows:
.\venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install Django
pip install django requests
```

### 3. Google API Configuration
Set your Google Maps API key in your environment or Django settings:
```bash
# Windows PowerShell
$env:GOOGLE_API_KEY="your-google-api-key-here"

# Linux / macOS
export GOOGLE_API_KEY="your-google-api-key-here"
```

### 4. Database Setup & Run Server
```bash
# Apply migrations
python manage.py migrate

# Start the local development server
python manage.py runserver
```
Visit `http://127.0.0.1:8000` in your web browser.

---

## 👥 Credits & Academic Context

- **Course**: CS 2340 (Objects and Design) at the **Georgia Institute of Technology**.
- **Contributors**:
  - **Benjamin Yohros** ([@byohros6](https://github.com/byohros6)) - Full-stack architecture, restaurant detail views, geocoding integration, and database management.
  - **Jad Bardawil** ([@jmb245](https://github.com/jmb245)) - Core feature logic, favorites management, and contact flows.
  - **Natalie Burstein** ([@natalieburstein08](https://github.com/natalieburstein08)) - User authentication UI and frontend styling.
  - **Emily Prieto** ([@emilyprietob](https://github.com/emilyprietob)) - UI/UX styling, favorites layout, and responsive design.
  - **Heeyoon Shin** - Design and feature planning.

*This repository serves as an academic and engineering portfolio showcase of object-oriented design and full-stack web development.*
