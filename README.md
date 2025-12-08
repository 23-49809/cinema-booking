# Cinema Booking System – Flask + MySQL

This is a cinema ticket booking system built using Flask and MySQL. It includes interfaces for both the cashier and the manager, handling movie scheduling, pricing, seat availability, and ticket generation. The application uses Flask routes for server-side rendering and executes SQL queries to manage movies, shows, halls, bookings, and pricing.

---

## Features

### Cashier
- View movies scheduled on a selected date  
- View available showtimes  
- Select available seats  
- Book tickets and generate ticket numbers  
- View real-time seat availability (gold and standard)

### Manager
- Add new movies  
- Schedule shows  
- View and modify pricing  
- View booked tickets per show  
- Check hall availability based on schedule and movie duration  

### Backend
- Flask-based routing  
- MySQL database integration  
- Query wrapper for handling SQL operations  
- Random ticket number generation  
- Automatic removal of old bookings using stored procedures  

---

## Running the Application Locally

### 1. Install dependencies
```
pip install -r requirements.txt
```

### 2. Start the Flask development server
```
python app.py
```

When running locally, Flask displays:
```
WARNING: This is a development server. Do not use it in a production deployment.
```

This warning is normal. Flask's built-in server is intended only for local testing.  
In production, a WSGI server such as **Gunicorn** must be used (see deployment section).

### 3. Access the application
Open the URL shown in your console:

```
http://127.0.0.1:5000
```
or  
```
http://localhost:5000
```

---

## Deployment (Render)

This project is deployable using **Render Web Services**.

### Required Additional Files

#### `requirements.txt`
```
Flask
mysql-connector-python
gunicorn
```

#### `Procfile`
```
web: gunicorn app:app
```

### Steps to Deploy

1. Push your project to a GitHub repository.  
2. Go to https://render.com and create a new account or sign in using GitHub.  
3. Select **New > Web Service**.  
4. Connect your GitHub repository.  
5. Configure the service:
   - Environment: Python 3
   - Build Command:
     ```
     pip install -r requirements.txt
     ```
   - Start Command:
     ```
     gunicorn app:app
     ```

6. Add environment variables for your MySQL connection:
   - `DB_HOST`  
   - `DB_USER`  
   - `DB_PASS`  
   - `DB_NAME`  

7. Click **Create Web Service**.

Render will deploy the project using **Gunicorn**, which replaces the Flask development server shown locally.

---

## Project Structure

```
cinema-booking/
│── app.py
│── requirements.txt
│── Procfile
│── templates/
│      ├── login.html
│      ├── cashier.html
│      ├── manager.html
│      ├── movies.html
│      ├── timings.html
│      ├── seating.html
│      ├── bookedtickets.html
│      ├── movieform.html
│      ├── validmovies.html
│      └── availablehalls.html
│── static/
│      ├── css/
│      ├── js/
│      └── images/
└── README.md
```

---

## Notes

- The built-in Flask server shown during local testing is expected and safe during development.  
- For production, always use a WSGI server such as **Gunicorn**, which is already configured for Render.  
- MySQL must be hosted on an external service; local MySQL cannot be used on Render.

---

## License

This project is for educational and demonstration purposes.  
