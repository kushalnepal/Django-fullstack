# NTC User Management System

A full-stack application for managing users, organizations, and hierarchical structures with role-based access control. Built with Django REST Framework (backend) and Next.js (frontend).

[![Django](https://img.shields.io/badge/Django-6.0-green)](https://www.djangoproject.com/)
[![Next.js](https://img.shields.io/badge/Next.js-14-green)](https://nextjs.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

## 📱 Repositories

- **Backend:** [NTC-UMS-Backend](https://github.com/kushalnepal/NTC-UMS-Backend)
- **Frontend:** [NTC-UMS-Frontend](https://github.com/kushalnepal/NTC-UMS-Frontend)

## 🌐 Live Demo

- **Frontend:** https://ntc-ums-frontend.kushalnepal.com.np
- **Backend API:** https://ntc-ums-backend.kushalnepal.com.np

## 🚀 Features

### Backend Features

#### User Authentication

- JWT-based authentication using djangorestframework-simplejwt
- Custom user model supporting username, email, and phone login
- Secure password hashing
- Login/Logout functionality with token refresh
- Multi-domain support in tokens

#### Admin Request System

- Public endpoint for requesting admin access to organizations
- Support for requesting admin role at Organization, Department, or Wing level
- Automatic membership creation upon approval

#### Multi-Level Organization Hierarchy

- **Domain** - Root level (e.g., "NTC")
- **Organization** - Companies under a domain (e.g., "NTC Telecom")
- **Department** - Departments within an organization (e.g., "IT Department")
- **Wing** - Sub-units within departments (e.g., "Software Wing")

#### Role-Based Access Control

- **Admin** - Full CRUD permissions on users and hierarchy
- **User** - Read-only access to hierarchy data
- Custom roles with JSON permissions support
- Generic Foreign Key for flexible entity relationships

#### User Management

- Create, Read, Update, Delete users
- User profile management
- Multi-membership support (users can belong to multiple entities)

### Frontend Features

#### User Authentication

- Secure login and signup functionality
- JWT token-based authentication
- Persistent session management
- Multi-identifier login (username, email, or phone)

#### Dashboard

- Overview of system statistics
- Quick access to main features
- User membership information display

#### Member Management

- View and manage system users
- Role-based access control
- User profile management
- Create, update, and delete users (Admin only)

#### Organization Hierarchy

- Visual representation of organizational structure
- Multi-level hierarchy navigation
- Hierarchical user relationships
- Easy navigation between levels

#### Token Management

- API token generation
- Token refresh functionality

## 🛠️ Tech Stack

### Backend

- **Framework:** Django 6.0
- **Language:** Python 3.10+
- **API:** Django REST Framework
- **Authentication:** JWT (djangorestframework-simplejwt)
- **Database:** SQLite (development) / PostgreSQL (production)

### Frontend

- **Framework:** Next.js 14 (App Router)
- **Language:** JavaScript/React
- **State Management:** React Context API
- **HTTP Client:** Fetch API

## 📡 API Endpoints

### Authentication

| Method | Endpoint                      | Description          |
| ------ | ----------------------------- | -------------------- |
| POST   | `/api/v1/auth/signup/`        | Register a new user  |
| POST   | `/api/v1/auth/login/`         | User login           |
| POST   | `/api/v1/auth/admin-request/` | Request admin access |
| POST   | `/api/v1/auth/token/`         | Obtain JWT token     |
| POST   | `/api/v1/auth/token/refresh/` | Refresh JWT token    |

### Hierarchy

| Method | Endpoint                               | Description          |
| ------ | -------------------------------------- | -------------------- |
| GET    | `/api/v1/auth/hierarchy/`              | Get user's hierarchy |
| GET    | `/api/v1/auth/hierarchy-members/`      | Get all members      |
| POST   | `/api/v1/auth/hierarchy-members/`      | Create user (Admin)  |
| PUT    | `/api/v1/auth/hierarchy-members/<id>/` | Update user (Admin)  |
| DELETE | `/api/v1/auth/hierarchy-members/<id>/` | Delete user (Admin)  |

### Organization

| Method   | Endpoint                 | Description        |
| -------- | ------------------------ | ------------------ |
| GET/POST | `/api/v1/domains/`       | Domains CRUD       |
| GET/POST | `/api/v1/organizations/` | Organizations CRUD |
| GET/POST | `/api/v1/departments/`   | Departments CRUD   |
| GET/POST | `/api/v1/wings/`         | Wings CRUD         |
| GET/POST | `/api/v1/roles/`         | Roles CRUD         |
| GET/POST | `/api/v1/memberships/`   | Memberships CRUD   |

## 🏗️ Project Structure

```
Django-fullstack/
├── python/                   # Django Backend
│   ├── accounts/            # User authentication app
│   │   ├── models.py        # Custom user model
│   │   ├── views.py         # API views
│   │   ├── serializers.py   # DRF serializers
│   │   └── urls.py          # URL routing
│   ├── organization/        # Organization app
│   │   ├── models.py        # Domain, Org, Dept, Wing models
│   │   ├── views.py         # Organization views
│   │   └── serializers.py   # Serializers
│   ├── storefront/          # Django project settings
│   │   ├── settings.py      # Main settings
│   │   └── urls.py          # Root URL config
│   ├── manage.py
│   └── requirements.txt
│
└── frontend/                # Next.js Frontend
    ├── src/
    │   ├── app/             # App Router pages
    │   │   ├── dashboard/   # Protected routes
    │   │   ├── login/       # Login page
    │   │   └── signup/      # Signup page
    │   ├── components/      # React components
    │   ├── context/         # Auth context
    │   └── utils/           # API utilities
    ├── package.json
    └── next.config.js
```

## 🔧 Installation

### Backend Setup

```bash
cd python
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

## 🔐 Authentication

Include JWT token in headers:

```
Authorization: Bearer <your-token-here>
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📝 License

MIT License - see LICENSE file for details.

## 👨‍💻 Author

Kushal Nepal - [GitHub](https://github.com/kushalnepal)

---

Built with ❤️ using Django + Next.js
