BMSIT Library Management Portal
Academic UI Prototype - Frontend Only
Link- https://sai-cloude.github.io/Bmsit-Library-Prjt/
This is a frontend-only prototype of a library management portal for BMS Institute of Technology and Management, Yelahanka. This version uses mock JavaScript data and localStorage for demonstration purposes only.

⚠️ Important Disclaimer
This is an academic UI prototype using fictional demonstration data.

NOT connected to BMSIT&M's official library system

NOT connected to Koha, ERP, student database, or real library records

All user data, book data, and borrowing records are fictional mock data

No backend, database, or real authentication is implemented

Profile updates, book management, and announcements are UI-only features

🚀 Quick Start
Step 1: Open the Project
Navigate to the bmsit-library-portal folder

Open index.html in any modern web browser (Chrome, Firefox, Edge, Safari)

Step 2: Use Demo Credentials
Student Login
College ID: BMSIT2026CS001

Password: 15082006

Teacher Login
Username: teacher.demo

Password: Teacher@123

Library Staff Login
Username: librarian.demo

Password: Library@123

📁 Project Structure
text
bmsit-library-portal/
│
├── index.html                  # Login page
├── student-dashboard.html      # Student dashboard
├── student-profile.html        # Student profile page
├── student-issued-books.html   # Student issued books
├── student-overdue-books.html  # Student overdue books
├── student-find-book.html      # Book search page
├── student-updates.html        # Library announcements
├── teacher-dashboard.html      # Teacher dashboard
├── staff-dashboard.html        # Staff dashboard with charts
├── staff-inventory.html        # Book inventory management
├── staff-borrowers.html        # Current borrowers list
├── staff-overdue.html          # Overdue books management
├── staff-announcements.html    # Announcement management
├── staff-reports.html          # Reports and exports
│
├── css/
│   └── style.css               # Main stylesheet
│
├── js/
│   └── data/
│       └── mock-data.js        # All mock data (users, books, borrowings)
│
├── images/
│   ├── avatars/                # Profile avatars (placeholders)
│   ├── books/                  # Book cover placeholders
│   └── posters/                # Announcement poster placeholders
│
└── README.md                   # This file
🎨 Features by Role
Student Features
Dashboard

Welcome message with current date

Summary cards (issued books, due soon, overdue, nearest due date)

Currently issued books preview

Overdue books preview

Library announcements carousel

Profile Page

Complete student profile display

College ID, department, branch, semester

Contact information

UI-only "Edit Contact Details" button (prototype)

Issued Books Page

List of all currently borrowed books

Search and filter by status/category

Desktop table and mobile card layouts

Due dates and days remaining

Overdue Books Page

Warning banner for overdue books

List of overdue books with fine estimation

Days overdue calculation

Find a Book Page

Advanced search by title, author, ISBN

Filters for category, branch, availability

Rack locator visualization (Rack 1-67, Shelves A-F)

Location display (e.g., "24C" = Rack 24, Shelf C)

Availability status for each book

Library Updates Page

Announcement posters grid

Top readers, new arrivals, campaigns, notices

Teacher Features
Dashboard

Teacher profile summary

Currently borrowed books list

Simple, clean interface

Desktop table and mobile card layouts

Library Staff Features
Dashboard

KPI cards (total titles, copies, available, borrowed, overdue)

Active student and teacher borrower counts

Chart.js charts:

Books by branch (doughnut chart)

Books by category (pie chart)

Available vs borrowed (bar chart)

Most borrowed books (bar chart)

Quick action buttons

Inventory Page

Full book inventory with search and filters

Sort by title, author, category, availability

Book details modal with:

Complete book information

Individual copy details with barcodes

Rack and shelf location

Export to CSV functionality

UI-only "Add Book" and "Edit Book" buttons

Borrowers Page

Current borrowers list (students and teachers)

Filter by role, status, branch

Book details, issue dates, due dates

Export to CSV

Overdue Books Page

Overdue alert banner

Borrower details with overdue days

Estimated fine calculation (₹5/day)

UI-only buttons: Return, Renew, Send Reminder

Export to CSV

Announcements Page

View all announcement posters

UI-only buttons: Create, Edit, Activate/Deactivate, Archive

Priority levels (high, medium, low)

Reports Page

Export buttons for:

Complete inventory

Available books

Issued books

Overdue books

Student borrowers

Teacher borrowers

Chart.js visualizations

All exports generate CSV files in browser

🎯 Technology Stack
Frontend Technologies
HTML5 - Semantic markup

CSS3 - Custom styling with CSS variables

Vanilla JavaScript - No frameworks

Bootstrap 5 (CDN) - Responsive grid and components

Chart.js (CDN) - Dashboard charts

Font Awesome (CDN) - Icons

localStorage - Demo login state and theme

No Backend Technologies
❌ No React

❌ No Python/Flask

❌ No Node.js/PHP

❌ No MySQL/Database

❌ No Firebase

❌ No real authentication

📊 Mock Data
The js/data/mock-data.js file contains:

Users
10 fictional students (CSE, ISE, ECE, EEE, ME, CE)

4 fictional teachers

2 fictional library staff members

Books
45 fictional book titles

Categories: Computer Science, Information Science, Electronics, Electrical, Mechanical, Civil, Mathematics, Physics, Chemistry, Management, General

Multiple copies per book

Locations: Rack 1-67, Shelves A-F (e.g., 24C, 31A, 67F)

Borrowings
12 active borrowing records

5 returned records

4 overdue records

Announcements
5 mock announcement posters

Types: achievement, new-arrivals, campaign, notice, event

📱 Responsive Design
The portal is fully responsive:

Desktop (≥992px): Sidebar navigation, full tables, charts

Tablet (768px-991px): Collapsible sidebar, responsive grid

Mobile (≤767px): Hamburger menu, stacked cards, touch-friendly buttons

Tested at:

360px (Mobile)

768px (Tablet)

1024px (Laptop)

1440px (Desktop)

🔐 Authentication (Demo Only)
Authentication is simulated using localStorage:

javascript
// Login sets these values
localStorage.setItem('isLoggedIn', 'true');
localStorage.setItem('userRole', 'student'); // or 'teacher' or 'staff'
localStorage.setItem('userId', 'BMSIT2026CS001');
localStorage.setItem('userName', 'Rahul Sharma');

// Logout clears them
localStorage.removeItem('isLoggedIn');
localStorage.removeItem('userRole');
localStorage.removeItem('userId');
localStorage.removeItem('userName');
🛠️ How to Connect Backend Later
This frontend is designed to be easily connected to a Python Flask + MySQL backend:

Step 1: Create Flask Backend
python
# app.py
from flask import Flask, jsonify, request
import mysql.connector

app = Flask(__name__)

# MySQL connection
db = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="bmsit_library"
)

@app.route('/api/login', methods=['POST'])
def login():
    data = request.json
    # Validate credentials against database
    # Return user data
    pass

@app.route('/api/books', methods=['GET'])
def get_books():
    # Query books from database
    # Return JSON
    pass

@app.route('/api/borrowings', methods=['GET'])
def get_borrowings():
    # Query borrowings from database
    pass

if __name__ == '__main__':
    app.run(debug=True)
Step 2: Create MySQL Database
sql
-- database.sql
CREATE DATABASE bmsit_library;

USE bmsit_library;

CREATE TABLE users (
    id VARCHAR(20) PRIMARY KEY,
    name VARCHAR(100),
    password_hash VARCHAR(255),
    role ENUM('student', 'teacher', 'staff'),
    department VARCHAR(100),
    branch VARCHAR(10),
    email VARCHAR(100),
    phone VARCHAR(20),
    address TEXT
);

CREATE TABLE books (
    accession_number VARCHAR(20) PRIMARY KEY,
    isbn VARCHAR(20),
    title VARCHAR(255),
    author VARCHAR(100),
    edition VARCHAR(50),
    category VARCHAR(50),
    branch VARCHAR(10),
    total_copies INT,
    available_copies INT,
    location VARCHAR(10),
    rack_number INT,
    shelf CHAR(1)
);

CREATE TABLE borrowings (
    borrowing_id VARCHAR(20) PRIMARY KEY,
    borrower_id VARCHAR(20),
    accession_number VARCHAR(20),
    issue_date DATE,
    due_date DATE,
    return_date DATE,
    status ENUM('issued', 'returned', 'overdue'),
    FOREIGN KEY (borrower_id) REFERENCES users(id),
    FOREIGN KEY (accession_number) REFERENCES books(accession_number)
);
Step 3: Update Frontend JavaScript
Replace mock data calls with API calls:

javascript
// Instead of using mockUsers, mockBooks, mockBorrowings

// Login
async function handleLogin(event, role) {
    event.preventDefault();

    const response = await fetch('http://localhost:5000/api/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            userId: document.getElementById('student-id').value,
            password: document.getElementById('student-password').value,
            role: role
        })
    });

    const userData = await response.json();

    if (userData.success) {
        localStorage.setItem('isLoggedIn', 'true');
        localStorage.setItem('userRole', role);
        localStorage.setItem('userId', userData.id);
        localStorage.setItem('userName', userData.name);
        window.location.href = 'student-dashboard.html';
    }
}

// Load books
async function loadBooks() {
    const response = await fetch('http://localhost:5000/api/books');
    const books = await response.json();
    // Use books data instead of mockBooks
}
Step 4: CORS Configuration
python
# In Flask app.py
from flask_cors import CORS

app = Flask(__name__)
CORS(app)  # Enable CORS for frontend API calls
Step 5: Serve Frontend
Option 1: Use Flask to serve static files:

python
@app.route('/')
def index():
    return send_from_directory('static', 'index.html')
Option 2: Use a simple HTTP server:

bash
# Python 3
python -m http.server 8080

# Or use Live Server extension in VS Code
🎨 Customization
Color Scheme
Edit CSS variables in css/style.css:

css
:root {
  --primary-color: #1a3a5c;      /* Navy Blue */
  --secondary-color: #f0a500;    /* Gold/Orange */
  --success-color: #28a745;
  --warning-color: #ffc107;
  --danger-color: #dc3545;
}
Add More Mock Data
Edit js/data/mock-data.js:

javascript
// Add more students
mockUsers.students.push({
  id: "BMSIT2026CS004",
  name: "New Student",
  // ... other fields
});

// Add more books
mockBooks.push({
  accessionNumber: "ACC046",
  title: "New Book Title",
  // ... other fields
});
📝 Code Quality
✅ Semantic HTML5

✅ Reusable JavaScript functions

✅ CSS variables for theming

✅ Responsive design with media queries

✅ Mobile-first approach

✅ Accessible contrast ratios

✅ Touch-friendly buttons (min 44px)

✅ No horizontal overflow on mobile

🐛 Known Limitations (Frontend Only)
No Data Persistence - All data resets on page reload (except localStorage for login state)

No Real Authentication - Credentials are validated against mock data only

No Database - All data is in mock-data.js file

No File Uploads - Announcement posters use placeholder images

No Email/SMS - Reminder buttons show prototype toast messages only

No Real Updates - Edit buttons show prototype messages

📄 License
This is an academic project for demonstration purposes only.

👨‍💻 Developer Notes
Testing Checklist
Login with all three roles

Navigate all pages

Test search and filters

Verify responsive design on mobile/tablet

Test CSV export functionality

Check chart rendering on staff dashboard

Verify rack locator visualization

Test all prototype toast messages

Browser Compatibility
✅ Chrome (latest)

✅ Firefox (latest)

✅ Edge (latest)

✅ Safari (latest)

📞 Support
For questions about this frontend prototype, refer to the code comments in:

js/data/mock-data.js - Mock data structure

css/style.css - Styling and responsive design

Individual HTML files - Page-specific functionality

Built with ❤️ for BMS Institute of Technology and Management

Frontend Prototype - Backend Integration Pending
