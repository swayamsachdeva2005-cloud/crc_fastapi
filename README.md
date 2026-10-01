# FastAPI College Event and Lost & Found API

A college management backend project containing two RESTful APIs built with **FastAPI** and **SQLModel**.

The project includes:

- **Task 1 – Lost & Found System:** Allows students to report lost or found items, update their status, and filter items by category or status.
- **Task 2 – Campus Event Seat Reservation API:** Manages college events and allows students to reserve seats while automatically checking event capacity and preventing overbooking or reservations for closed events.

---

## Technologies Used

- **Python 3**
- **FastAPI** – REST API framework
- **SQLModel** – ORM and data validation
- **Pydantic** – Data validation and settings management
- **SQLite** – Database
- **Uvicorn** – ASGI server

---

## Project Structure

```text
.
├── task_1/
│   ├── main.py
│   ├── database.py
│   └── ...
│
├── task_2/
│   ├── main.py
│   ├── database.py
│   └── ...
│
├── requirements.txt
└── README.md
```

---

## Installation

### 1. Clone the Repository

```bash
git clone <your-github-repo-url>
cd <repository-folder>
```

### 2. Create a Virtual Environment

Creating a virtual environment is recommended.

```bash
python -m venv venv
```

### 3. Activate the Virtual Environment

**Windows:**

```bash
venv\Scripts\activate
```

**macOS/Linux:**

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# Task 1 – Lost & Found API

The Lost & Found API allows college students to report items that have been lost or found on campus.

It supports creating reports, updating item information, deleting reports, and filtering items by status or category.

## Run Task 1

```bash
uvicorn task_1.main:app --reload
```

The API will be available at:

```text
http://127.0.0.1:8000
```

### Task 1 Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/items` | Create a new lost/found item report |
| GET | `/items` | List all reported items |
| GET | `/items/{item_id}` | Retrieve a specific item |
| PUT | `/items/{item_id}` | Update item details or status |
| DELETE | `/items/{item_id}` | Delete an item report |
| GET | `/items/status/{status}` | Filter items by status |
| GET | `/items/category/{category}` | Filter items by category |

### Supported Status Values

```text
Lost
Found
Returned
```

### Example Categories

```text
Electronics
Documents
Accessories
Books
Other
```

---

# Task 2 – Campus Event Seat Reservation API

The Campus Event Reservation API manages college events such as:

- Workshops
- Hackathons
- Seminars
- Technical events
- College activities

Students can reserve seats for events. The API checks the event's capacity and prevents reservations when:

- The event is full.
- The event is closed.
- The requested event does not exist.

## Run Task 2

```bash
uvicorn task_2.main:app --reload
```

The API will be available at:

```text
http://127.0.0.1:8000
```

### Task 2 Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/events` | Create a new event |
| GET | `/events` | List all events |
| GET | `/events/{event_id}` | Get details of a specific event |
| PUT | `/events/{event_id}` | Update event information |
| DELETE | `/events/{event_id}` | Delete an event and its reservations |
| POST | `/events/{event_id}/reserve` | Reserve a seat for an event |
| GET | `/events/{event_id}/reservations` | View all reservations for an event |
| GET | `/events/{event_id}/availability` | View event capacity and remaining seats |
| DELETE | `/reservations/{reservation_id}` | Cancel a reservation |

---

# API Documentation

FastAPI automatically provides interactive API documentation using Swagger UI.

After starting either application, open:

```text
http://127.0.0.1:8000/docs
```

You can use Swagger UI to:

- View all available endpoints
- Send GET, POST, PUT, and DELETE requests
- Test API functionality
- View request and response schemas
- Check validation errors

FastAPI also provides ReDoc at:

```text
http://127.0.0.1:8000/redoc
```

---

## Database

The project uses **SQLite** for data storage and **SQLModel** for database operations.

Database tables are created when the respective application starts.

The database stores information such as:

### Lost & Found

- Item ID
- Title
- Description
- Category
- Location
- Reported By
- Status

### Event Reservation

- Event ID
- Event Name
- Event Details
- Event Capacity
- Event Status
- Reservation ID
- Student/Participant Details

---

## Key Features

### Lost & Found

- Create lost/found item reports
- View all reported items
- Search items
