# Eventra 🎟️

**Discover events. Explore experiences. Book your next moment.**

Eventra is a locally runnable event discovery and ticket-booking platform built for college and campus experiences. Users can browse events, compare ticket options, select seats when available, complete a simulated checkout, and access verified digital tickets. Administrators can manage each event and see its buyers from one focused dashboard.

## ✨ Features

- **Discover events** across technology, workshops, music, sports, culture, competitions, and more.
- **Search and filter** the event catalogue by name or category.
- **Event details** with descriptions, dates, venues, ticket types, prices, and availability.
- **Authentication** with customer registration, login throttling, JWT sessions, and role-based access.
- **Ticket booking** with quantity-based tickets or seat selection when an event has a seat map.
- **Event setup** where administrators configure multiple ticket types, prices, inventory, and optional seat maps while creating an event.
- **Event editing** for updating event information, ticket options, inventory, and expanding seat maps later.
- **Demo checkout** with successful, failed, and cancelled payment outcomes. No real payment details are collected.
- **Digital tickets** with booking references, QR codes, printable ticket views, and public verification.
- **Customer dashboard** with upcoming bookings, past bookings, tickets, and cancellation actions.
- **Admin dashboard** with event status management and event-specific buyer lists showing customers, ticket types, quantities, seats, references, and statuses.
- **MySQL persistence** for users, categories, events, ticket types, seats, bookings, payments, and tickets.

## 🛠️ Tech stack

| Technology | Purpose |
| --- | --- |
| React + Vite | Frontend application |
| React Router | Client-side routing |
| JavaScript | Application logic |
| CSS | Responsive interface styling |
| Node.js | Backend runtime |
| Express.js | REST API |
| MySQL | Application database |
| `mysql2` | MySQL connectivity |
| `bcryptjs` | Password hashing |
| `jsonwebtoken` | Authentication tokens |
| `qrcode` and `qrcode.react` | Digital ticket QR codes |

## 📁 Project structure

```text
eventra/
├── client/             # React/Vite frontend
│   └── src/
├── server/             # Express API and server logic
│   └── src/
├── database/            # MySQL schema and seed data
├── .gitignore
├── package.json
└── README.md
```

## ⚙️ Prerequisites

Install the following:

- [Node.js](https://nodejs.org/) 18 or newer
- [MySQL](https://dev.mysql.com/downloads/) 8 or newer
- [Git](https://git-scm.com/)
- A code editor such as [Visual Studio Code](https://code.visualstudio.com/)

## 🚀 Getting started

### 1. Clone the repository

```powershell
git clone https://github.com/programmer-sultan786/eventra..git
cd eventra.
```

### 2. Create the database

Create a dedicated database in MySQL:

```sql
CREATE DATABASE eventra;
```

Run the SQL files in this order:

1. `database/schema.sql`
2. `database/seed.sql`

The seed data creates sample categories, events, ticket inventory, and the development administrator account.

### 3. Configure the server

Copy `server/.env.example` to `server/.env` and set values for your local MySQL instance:

```dotenv
PORT=4000
DB_HOST=localhost
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_NAME=eventra
JWT_SECRET=replace_with_a_long_random_secret
```

Never commit `server/.env` or real credentials.

### 4. Install dependencies

From the repository root:

```powershell
npm install
npm run install:all
```

### 5. Start Eventra

Start both applications from the root:

```powershell
npm run dev
```

Open:

- Frontend: `http://localhost:5173`
- API health check: `http://localhost:4000/api/health`

The development administrator is:

```text
Email: admin@eventra.local
Password: Admin@123
```

Change this password before any public deployment.

## 💳 Demo payment system

Eventra deliberately uses a simulated payment workflow. Customers can choose:

- Successful payment
- Failed payment
- Cancelled booking

Successful payments confirm the booking and create a digital ticket. Failed and cancelled outcomes release the reserved inventory or seats. No real payment gateway, card details, or money is involved.

## 🎫 Digital tickets and seats

Confirmed bookings provide a digital ticket containing the event, booking reference, ticket information, and a QR code. The QR code opens the public verification route:

```text
/verify/:ticketCode
```

Administrators can configure an optional seat map when creating an event. During booking, customers choose a ticket type first and then available seats. Seats are held during checkout, marked as sold after successful payment, and released after failed, cancelled, or expired bookings.

## 🔐 Security and data safeguards

- Passwords are hashed with `bcryptjs`.
- Protected API routes require JWT authentication.
- Administrator routes require the admin role.
- Booking inventory and seat changes use MySQL transactions and row locks.
- Database queries use parameterized values.
- Login attempts are throttled after repeated failures.
- Environment files and local credentials are excluded from Git.

This is a demonstration project and should receive a full security review before public deployment. Login throttling is in-memory and resets when the server restarts.

## 🗺️ Future enhancements

- Production payment gateway integration
- Email confirmations and booking notifications
- Refresh-token or server-side session revocation
- Event recommendations
- Advanced analytics and reporting
- Additional profile and organizer features

## 📄 License

No license has been specified yet.

---

**Eventra — Every event, one destination.**
