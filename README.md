# HMS App | Hospital Management (MERN)

Patient and admin portal with registration, authentication, profile management, and document uploads. Backend in Node/Express/MongoDB with JWT auth; frontend in React + React Bootstrap.

## About The Project

HMS App provides basic hospital management flows: patients sign up/login, view/update profiles, and upload identity documents; admins register/login, manage their own profiles, and access dedicated dashboards. The backend exposes REST APIs secured by JWT; the frontend offers dashboards, profile pages, and upload flows.

## Built With

- Frontend: React 19, React Router, React Bootstrap, Bootstrap, React Icons
- Backend: Node.js, Express, MongoDB (Mongoose), JWT, Multer, CORS

## Getting Started

### Prerequisites

- Node.js 16+
- npm
- MongoDB running locally (default connection: mongodb://localhost:27017/UIT-Project)

### Backend Setup

```bash
cd backend
npm install
# start server (port 5000)
node index.js               # or: npx nodemon index.js
```

If you use a different MongoDB URI, update `db/config.js`.

### Frontend Setup

```bash
cd frontend
npm install
npm start                   # runs on http://localhost:3000
```

## Usage

- Patients: register (`/register`), log in (`/login`), view/update profile (`/profile/:id`, `/patient/update/:id`), upload documents (`/upload/:id`), and access dashboard (`/dashboard`).
- Admins: register (`/admin/register`), log in (`/admin/login`), view/update profile (`/admin/update/:id`), and access admin dashboard (`/admin/dashboard`).

Backend JWT is expected in `Authorization: Bearer <token>` for protected routes (profile fetch/update, uploads).

## API Overview (backend)

- POST `/register` – patient signup (email unique)
- POST `/login` – patient login (returns JWT)
- POST `/admin/register` – admin signup (govt_id unique)
- POST `/admin/login` – admin login (dept check, returns JWT)
- GET `/user/:id` – get patient (auth required)
- PUT `/user/:id` – update patient (auth required)
- GET `/admin/:id` – get admin (auth required)
- PUT `/admin/:id` – update admin (auth required)
- PUT `/upload/:id` – upload patient document (multer to /uploads, filename prefixed with aadhar)

## Features

- JWT auth for patients and admins
- Role-specific dashboards and routes
- Profile view/update for patients and admins
- Document upload with multer and local storage
- Basic CORS-enabled REST API

## Project Structure

```
hms-app/
├─ backend/
│  ├─ db/            # Mongo connection and Mongoose models (User, Admin)
│  ├─ uploads/       # Stored upload files
│  ├─ index.js       # Express app and routes
│  ├─ package.json
├─ frontend/
│  ├─ src/
│  │  ├─ components/ # Navbar, Landing, Dashboards, Forms, Upload, Profile
│  │  ├─ App.js
│  ├─ package.json
├─ LICENSE           # MIT License
└─ README.md
```

## Scripts

- Backend: `node index.js` (or `npx nodemon index.js`)
- Frontend: `npm start`, `npm run build`, `npm test`

## Roadmap

- Add environment-based config for secrets and DB URI
- Add validation and better error handling
- Add role-based authorization middleware
- Add secure file storage (cloud/object storage) and virus scanning
- Add logging, rate limiting, and production hardening

## Contributing

Contributions are welcome. Please open an issue to discuss changes before submitting a PR.

## License

MIT License. See LICENSE for details.

## Contact

Tuman Sutradhar
- GitHub: https://github.com/tumansutradhar
- Email: connect.tuman@gmail.com
- LinkedIn: https://www.linkedin.com/in/tumansutradhar/

Project Link: https://github.com/tumansutradhar/hms-app

## Acknowledgments

- Express, Mongoose, Multer, and JWT docs
- React, React Router, and React Bootstrap communities
