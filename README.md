# Cinema Booking System – Flask and MySQL

This project is a functional cinema ticket booking system built using Flask for the backend and MySQL as the database. It provides separate interfaces for cashiers and managers, supporting movie scheduling, seat management, ticket booking, pricing configuration, and real-time seat availability tracking.

The application uses Flask server-side rendering, SQL queries for data operations, and HTML templates for the user interface.

---

## Live Deployment

The system is publicly accessible at the following URL:

**https://cinema-booking-2-2pqo.onrender.com/**

---

## Features

### Cashier Dashboard
- View movies available on a specific date  
- Display showtimes and formats (Standard / Gold)  
- Real-time seating layout with disabled booked seats  
- Automatic ticket number generation  
- Ticket confirmation and booking

### Manager Dashboard
- Add new movies with duration, language, and show date range  
- Manage movie types and formats  
- Schedule movie shows and ensure hall availability  
- Edit pricing for Standard and Gold seats  
- View all bookings made for any show

### Backend Capabilities
- Flask-based endpoints serving cashier and manager operations  
- MySQL database handling movie, show, hall, and booking data  
- Query wrapper (`runQuery`) used for executing and committing SQL commands  
- Server-side seat classification (Standard vs. Gold)  
- Auto-cleanup of old records via stored procedure calls

---

## Technology Stack

- **Backend Framework:** Flask  
- **Database:** MySQL  
- **Frontend:** HTML templates (Jinja2), CSS, basic JavaScript  
- **Server:** Render Web Service  
- **WSGI Server:** Gunicorn  
- **Language:** Python 3.x  

---

## Project Structure

```
cinema-booking/
│── app.py                     # Main Flask application
│── requirements.txt           # Python dependencies
│── Procfile                   # Render process configuration
│── templates/                 # Jinja2 HTML templates
│     ├── login.html
│     ├── cashier.html
│     ├── manager.html
│     ├── movies.html
│     ├── seating.html
│     ├── timings.html
│     ├── shows.html
│     ├── bookedtickets.html
│     ├── movieform.html
│     ├── validmovies.html
│     └── availablehalls.html
│── static/                    # CSS, JS, and images (if applicable)
└── README.md
```

---

## Running Locally

### 1. Install Dependencies
```
pip install -r requirements.txt
```

### 2. Configure MySQL Database
Ensure a MySQL database is running and update the connection details inside `app.py`:

```
db = mysql.connector.connect(
    host='your-db-host',
    database='dbtheatre',
    user='your-db-user',
    password='your-db-password'
)
```

### 3. Start the Flask Development Server
```
python app.py
```

The server will open at:

```
http://127.0.0.1:5000
```

Note: The local Flask development server is only for testing.  
In production (Render), the application runs using Gunicorn as configured in the `Procfile`.

---

## Deployment Instructions (Render)

This project is deployed using Render Web Services.

### Important Deployment Files

#### `requirements.txt`
Contains all dependencies, including:
```
Flask
gunicorn
mysql-connector-python
```

#### `Procfile`
Specifies the production WSGI entry point:
```
web: gunicorn app:app
```

### Deployment Overview
1. Push the project to GitHub  
2. Create a new Web Service on Render  
3. Set build and start commands  
4. Add environment variables for MySQL credentials  
5. Deploy service

---

## Notes

- The MySQL connection must point to a cloud-hosted database for Render deployments.  
- The application does not work with localhost MySQL on remote servers.  
- Templates must be located inside the `/templates` directory for Flask to render correctly.

---

## License

This project is provided for academic and demonstration purposes.


