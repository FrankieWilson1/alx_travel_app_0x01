# ALX Travel App

## 📝 Description
This project is a foundational backend application for a travel booking platform. It is developed as part of an ALX program and focuses on defining a robust database schema, setting up data serialization for API interactions, and creating a custom management command to seed the database with sample data.

## 🎯 Objective
The primary objective of this project was to:
- Define the database models for **Listing**, **Booking**, and **Review**.
- Create serializers for API data representation of the **Listing** and **Booking** models.
- Implement a Django management command to populate the database with sample data.

## ✨ Features
- **Database Models**: Three core models—**Listing**, **Booking**, and **Review**—are defined to represent travel listings, user bookings, and user reviews.
- **Django REST Framework Serializers**: Serializers are implemented to convert model instances into JSON format, providing a structured way to interact with the data via an API.
- **Database Seeder**: A custom management command (`seed`) is available to quickly populate the database with a large amount of realistic, fake data for development and testing purposes.
- **Environment Variables**: Sensitive configurations are managed using a `.env` file, following best practices for production-ready applications.

## 🛠️ Technologies Used
- **Python 3**
- **Django**
- **Django REST Framework**
- **MySQL** (or a compatible database)
- **Faker** (for generating fake data)
- **python-decouple** (for managing environment variables)
- **mysqlclient** (MySQL database connector)

## 🚀 Setup and Installation
Follow these steps to get the project up and running on your local machine.

### Clone the Repository:
```bash
git clone https://github.com/your-username/alx_travel_app_0x00.git
cd alx_travel_app_0x00
```

### Create a Virtual Environment:
```bash
python3 -m venv env
source env/bin/activate  # On Windows, use: env\Scripts\activate
```

### Install Dependencies:
Install all required Python packages, including `python-decouple` to read your environment variables.
```bash
pip install django djangorestframework faker mysqlclient python-decouple
```

### Configure Environment Variables:
Create a file named `.env` in the root directory of your project and add your database configuration.
```dotenv
# Django SECRET_KEY
SECRET_KEY=your_secret_key_here

# MySQL Database Configuration
DATABASE_URL=mysql://alx_user:12345@localhost:3306/alxtravelapp_db
DATABASE_NAME=alxtravelapp_db
DATABASE_USER=alx_user
DATABASE_PASSWORD=12345
DATABASE_HOST=localhost
DATABASE_PORT=3306
```

### Update settings.py:
Open `alx_travel_app/settings.py` and modify your database configuration to read from the `.env` file using decouple.
```python
# settings.py
from decouple import config

# Use config() to read your SECRET_KEY and other variables
SECRET_KEY = config('SECRET_KEY')

# ... (rest of your settings)

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': config('DATABASE_NAME'),
        'USER': config('DATABASE_USER'),
        'PASSWORD': config('DATABASE_PASSWORD'),
        'HOST': config('DATABASE_HOST'),
        'PORT': config('DATABASE_PORT'),
    }
}
```

### Run Migrations:
Apply the database schema to your MySQL database.
```bash
python manage.py makemigrations
python manage.py migrate
```

## 📋 Usage
### Seeding the Database
After setting up the project, you can use the custom seed command to populate your database.

To seed the database with default values:
```bash
python manage.py seed
```

To clear existing data and seed with custom values:
```bash
python manage.py seed --clear --num_listings 50 --num_users 10
```
- `--clear`: Deletes all existing listings, bookings, and reviews before seeding.
- `--num_listings`: Specifies the number of fake listings to create (default is 20).
- `--num_users`: Specifies the number of fake users to create (default is 5).

## 🧑‍💻 Author
Frank Williams Ugwu - [GitHub Profile](https://github.com/FrankieWilson1)
