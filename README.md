# Theatre Ticket Booking System

This project is a complete Theatre Ticket Booking System built using Python (Flask) and MySQL. It includes separate login portals for managers and cashiers, show scheduling, dynamic seat availability, movie management, pricing control, and automated ticket booking. All backend logic, including querying, seat allocation, and ticket generation, is handled through Flask and MySQL queries.

Core project information, including database name and default credentials, is defined in **01 LOGIN DETAILS & PROJECT INFO.txt** :contentReference[oaicite:0]{index=0}.  
All application logic, routing, SQL queries, and booking workflows are implemented in **app.py** :contentReference[oaicite:1]{index=1}.

---

## Features

### Authentication
- Manager and Cashier login pages  
- Credential verification through Flask routes  
- Redirects to respective dashboards upon successful login

### Cashier Functions
- Search movies showing on a selected date  
- View available time slots for each movie  
- Retrieve show ID  
- Display available seats (gold and standard)  
- Dynamic seat disabling for booked seats  
- Calculate ticket price based on seat class  
- Confirm seat bookings and generate ticket numbers

### Manager Functions
- View all shows scheduled for a selected date  
- Retrieve booked tickets per show  
- Insert new movies with validation to avoid duplicates  
- Assign movie types (up to 3 types)  
- Validate movies available for a specific date  
- Check hall availability based on duration and schedule  
- Insert new shows into the database  
- View and modify pricing structure

### Database Integration
- Uses MySQL with stored procedures (example: `delete_old()`)  
- Automated cleanup of outdated data  
- Real-time query execution through `runQuery()` wrapper

### Ticket Handling
- Generates unique ticket numbers  
- Books seats by inserting into `booked_tickets`  
- Supports gold and standard seat numbering formats

### Technology Stack
- Python 3.x  
- Flask  
- MySQL  
- HTML Templates (Jinja2)  
- Stored Procedures and SQL Queries

---

## Project Structure

```
/project
│── app.py
│── templates/
│     ├── login.html
│     ├── cashier.html
│     ├── manager.html
│     ├── movies.html
│     ├── timings.html
│     ├── seating.html
│     ├── shows.html
│     ├── bookedtickets.html
│     ├── movieform.html
│     ├── validmovies.html
│     ├── availablehalls.html
│     └── other HTML templates
│── static/
│── 01 LOGIN DETAILS & PROJECT INFO.txt
└── README.md
```

---

## Default Login Credentials

From **01 LOGIN DETAILS & PROJECT INFO.txt** :contentReference[oaicite:2]{index=2}:

**Manager Login**  
- Username: `manager`  
- Password: `Password@123`  

**Cashier Login**  
- Username: `cashier`  
- Password: `cashier123`  

Database name: **dbtheatre**

---

## Prerequisites

- Python 3.x  
- MySQL Server  
- pip package manager  

Install required libraries:

```bash
pip install flask mysql-connector-python
```

---

## Running the Application

1. Import the database structure into MySQL (db name: `dbtheatre`).  
2. Ensure MySQL is running locally.  
3. Update MySQL username/password inside `runQuery()` in `app.py` if needed.  
4. Start the Flask server:

```bash
python app.py
```

5. Open the application in your browser:

```
http://localhost:5000
```

---

## How the System Works

### Seat Allocation Logic
- Gold seats use seat numbers above 1000  
- Standard seats use normal numbering  
- Booked seats populate dynamically into the seating layout via template rendering

### Show Scheduling Logic
- Calculates movie end times using duration  
- Checks hall availability by comparing overlapping schedules  
- Rejects conflicting showtimes

### Price Management
- Prices defined in `price_listing` table  
- Manager can update prices dynamically  
- Gold seat price is automatically set to 1.5× the standard rate

---

## Future Improvements

- Admin dashboard UI improvements  
- Exportable booking reports  
- Email or SMS ticket confirmation  
- WebSocket real-time seat updates  
- Role-based user accounts in database rather than hardcoded

---

## Credits

This project is based on the structure described in **01 LOGIN DETAILS & PROJECT INFO.txt** :contentReference[oaicite:3]{index=3} and implemented through Flask using the logic contained in **app.py** :contentReference[oaicite:4]{index=4}.

