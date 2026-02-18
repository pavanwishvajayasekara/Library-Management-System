# 📚 Library Management System

A comprehensive full-stack library management system built with React and Spring Boot, featuring book reservation, borrowing, and automated fine calculation for overdue books.

## 🎯 Overview

This Library Management System provides a complete solution for managing library operations including book catalog management, member registration, book reservations, borrowing, returns, and automated fine calculation for overdue books. The system is designed with a modern, responsive user interface and a robust RESTful API backend.

## ✨ Key Features

### 📖 Book Management
- **CRUD Operations**: Create, read, update, and delete books
- **Book Catalog**: Comprehensive book information including title, author, ISBN, genre, publication year
- **Availability Tracking**: Real-time tracking of available copies
- **Book Search & Filtering**: Search books by title, author, genre, and more
- **Book Statistics**: Dashboard with visual statistics and analytics

### 🔐 User & Member Management
- **User Authentication**: Secure login and registration system
- **Member Registration**: Library member registration with unique member IDs (LIB prefix)
- **Role-Based Access Control**: Admin and Member roles with different permissions
- **Member Profiles**: Comprehensive member profile management

### 📅 Book Reservation System
- **Reservation Management**: Members can reserve books that are currently unavailable
- **Reservation Status Tracking**: PENDING, RECEIVED, CANCELLED status management
- **Auto-Conversion**: Reservations automatically convert to borrowings when books become available
- **Duplicate Prevention**: System prevents duplicate reservations for the same member and book

### 📚 Book Borrowing System
- **Borrowing Management**: Complete borrowing lifecycle management
- **Due Date Tracking**: Automatic due date calculation (14 days from borrow date)
- **Return Processing**: Book return functionality with status updates
- **Borrowing History**: Complete history of all borrowings per member
- **Availability Updates**: Automatic book availability updates on borrow/return

### 💰 Fine Management System
- **Automatic Fine Calculation**: Automated calculation of late fees for overdue books
- **Weekly Fee Structure**: Fines calculated based on weeks overdue (100 per week)
- **Real-time Updates**: Fines calculated in real-time when books are returned
- **Fine Tracking**: Separate tracking for pending and paid fines
- **Dashboard Statistics**: Visual representation of fine collections

### 📊 Dashboard & Analytics
- **Real-time Statistics**: Live updates of library metrics
- **Visual Charts**: Interactive charts using Recharts library
- **Key Metrics**: 
  - Total books and available books
  - Active borrowings and reservations
  - Overdue books count
  - Fine collections (pending and paid)

## 🛠️ Technology Stack

### Frontend
- **React 19.1.1**: Modern React with latest features
- **Vite 7.1.2**: Fast build tool and development server
- **React Router DOM 7.9.1**: Client-side routing
- **Axios 1.12.2**: HTTP client for API calls
- **Recharts 3.2.1**: Data visualization library
- **ESLint**: Code quality and linting

### Backend
- **Spring Boot 3.5.5**: Java-based backend framework
- **Java 17**: Modern Java features
- **Spring Data MongoDB**: MongoDB integration
- **Spring Security**: Authentication and authorization
- **Spring Boot Mail**: Email notification support
- **Lombok**: Reduced boilerplate code
- **Jakarta Validation**: Input validation

### Database
- **MongoDB Atlas**: Cloud-hosted MongoDB database
- **MongoDB Collections**:
  - `books`: Book catalog
  - `users`: User accounts
  - `members`: Library members
  - `borrowings`: Borrowing records
  - `reservations`: Reservation records

### Infrastructure
- **Maven**: Dependency management and build tool
- **Vercel**: Frontend deployment (configured)
- **Gmail SMTP**: Email service integration

## 📁 Project Structure

```
SE-LibraryManagementSystem/
├── frontend/                 # React frontend application
│   ├── src/
│   │   ├── components/      # React components
│   │   │   ├── BookList.jsx
│   │   │   ├── BookDetails.jsx
│   │   │   ├── Borrowings.jsx
│   │   │   ├── Reservations.jsx
│   │   │   ├── MemberProfile.jsx
│   │   │   ├── DashboardStats.jsx
│   │   │   └── ...
│   │   ├── App.jsx          # Main application component
│   │   ├── api.js           # API service layer
│   │   └── utils.js         # Utility functions
│   ├── package.json
│   └── vite.config.js
│
├── backend/                 # Spring Boot backend application
│   ├── src/main/java/com/management/library/
│   │   ├── BookManagement/      # Book CRUD operations
│   │   ├── BorrowingReservation/ # Borrowing & Reservation logic
│   │   │   ├── controller/
│   │   │   ├── service/
│   │   │   │   ├── FeeService.java      # Fine calculation logic
│   │   │   │   └── IdService.java       # ID generation
│   │   │   └── entity/
│   │   ├── MemberManagement/    # Member management
│   │   ├── UserManagement/      # User authentication
│   │   └── Config/              # Configuration classes
│   ├── src/main/resources/
│   │   └── application.properties
│   └── pom.xml
│
└── README.md               # This file
```

## 🚀 Getting Started

### Prerequisites

- **Node.js** (v18 or higher)
- **npm** or **yarn**
- **Java 17** or higher
- **Maven 3.6+**
- **MongoDB Atlas** account (or local MongoDB instance)

### Installation

#### 1. Clone the Repository

```bash
git clone <repository-url>
cd SE-LibraryManagementSystem
```

#### 2. Backend Setup

```bash
cd backend

# Update MongoDB connection string in application.properties
# File: src/main/resources/application.properties
# Update: spring.data.mongodb.uri with your MongoDB connection string

# Build the project
mvn clean install

# Run the Spring Boot application
mvn spring-boot:run
```

The backend server will start on `http://localhost:8081`

#### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Update API base URL in api.js if needed
# Default: http://localhost:8081

# Start development server
npm run dev
```

The frontend will start on `http://localhost:5173` (or the next available port)

### Configuration

#### Backend Configuration (`application.properties`)

```properties
# Server Configuration
server.port=8081

# MongoDB Configuration
spring.data.mongodb.uri=mongodb+srv://username:password@cluster.mongodb.net/
spring.data.mongodb.database=LibraryDatabase

# Email Configuration (Gmail)
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your-email@gmail.com
spring.mail.password=your-app-password
```

#### Frontend Configuration (`src/api.js`)

Update the API base URL if your backend runs on a different port:

```javascript
const API_BASE_URL = 'http://localhost:8081/api';
```

## 📖 API Endpoints

### Book Management
- `GET /api/books` - Get all books
- `GET /api/books/{id}` - Get book by ID
- `POST /api/books` - Create new book
- `PUT /api/books/{id}` - Update book
- `DELETE /api/books/{id}` - Delete book

### Borrowing Management
- `GET /api/borrowings` - Get all borrowings (optional: `?memberId={id}`)
- `POST /api/borrowings` - Create new borrowing
- `PUT /api/borrowings/{id}` - Update borrowing
- `POST /api/borrowings/{id}/return` - Mark book as returned
- `DELETE /api/borrowings/{id}` - Delete borrowing

### Reservation Management
- `GET /api/reservations` - Get all reservations (optional: `?memberId={id}`)
- `POST /api/reservations` - Create new reservation
- `PUT /api/reservations/{id}` - Update reservation status
- `DELETE /api/reservations/{id}` - Cancel reservation

### User & Member Management
- `POST /api/users` - Register new user
- `POST /api/users/login` - User login
- `GET /api/members` - Get all members
- `GET /api/members/{id}` - Get member by ID
- `POST /api/members` - Create new member

## 💡 Key Features Explained

### Fine Calculation Logic

The system automatically calculates fines for overdue books:

```java
// Fine calculation formula
- Due date: Set to 14 days from borrow date
- Weekly fee: 100 per week
- Calculation: Math.ceil(daysLate / 7.0) * weeklyFee
- Example: 10 days late = 2 weeks = 200 fine
```

**Fine Calculation Flow:**
1. When a book is borrowed, due date is set (borrow date + 14 days)
2. On return, system checks if return date > due date
3. If overdue, calculates weeks overdue
4. Applies weekly fee (100 per week)
5. Updates borrowing record with calculated fine

### Reservation to Borrowing Flow

1. **Member reserves book** → Status: PENDING
2. **Book becomes available** → Admin marks reservation as RECEIVED
3. **System automatically creates borrowing** → Status: ACTIVE
4. **Due date set** → Borrow date + 14 days
5. **Other pending reservations cancelled** → Prevents duplicates

### Book Availability Management

- When book is borrowed: `availableCopies` decreases
- When book is returned: `availableCopies` increases
- When `availableCopies` reaches 0: `availability` set to false
- Reservations can be made for unavailable books

## 🎨 User Roles

### Admin
- Full access to all features
- Book CRUD operations
- Member management
- View all borrowings and reservations
- Process returns and calculate fines
- Access admin dashboard

### Member
- View book catalog
- Reserve books
- Borrow books (if available)
- View personal borrowing history
- View personal reservations
- View and pay fines
- Update profile

## 📊 Database Schema

### Book Entity
```java
- id: String
- title: String
- author: String
- isbn: String
- genre: String
- publicationYear: Integer
- totalCopies: Integer
- availableCopies: Integer
- availability: Boolean
```

### Borrowing Entity
```java
- id: String
- borrowingNumber: String (BRYYYY####)
- memberId: String
- bookId: String
- borrowDate: LocalDate
- dueDate: LocalDate
- returnDate: LocalDate (nullable)
- status: String (ACTIVE/RETURNED)
- lateFee: Integer
```

### Reservation Entity
```java
- id: String
- reservationNumber: String (RSYYYY####)
- memberId: String
- bookId: String
- reservationDate: LocalDate
- status: String (PENDING/RECEIVED/CANCELLED)
```

## 🧪 Testing

### Backend Testing
```bash
cd backend
mvn test
```

### Frontend Testing
```bash
cd frontend
npm run lint
```

## 🚢 Deployment

### Frontend Deployment (Vercel)
```bash
cd frontend
npm run build
# Deploy dist/ folder to Vercel
```

### Backend Deployment
- Deploy Spring Boot JAR to cloud platform (AWS, Heroku, etc.)
- Update MongoDB connection string for production
- Configure environment variables for email service

## 🤝 Contributing

This project was developed by:
- **Pavan Wishvajayasekara** - Project Lead & Developer
- **Malika** - Developer
- **Ishara** - Developer
- **Ravidu** - Developer

## 📝 License

This project is developed for educational purposes as part of a Software Engineering course.

## 🔮 Future Enhancements

- [ ] Email notifications for due dates and fines
- [ ] Book renewal functionality
- [ ] Advanced search and filtering
- [ ] Export reports (PDF/Excel)
- [ ] Mobile application
- [ ] Integration with payment gateways for fine payment
- [ ] Book recommendation system
- [ ] Multi-language support

## 📞 Support

For issues, questions, or contributions, please contact the development team.

---

**Built with ❤️ by the Library Management System Team**
