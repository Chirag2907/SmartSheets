# SmartSheets Project Documentation

### Introduction

This document provides comprehensive documentation for the SmartSheets project. SmartSheets is a web-based application designed to manage and organize data efficiently. 

The idea was to develop a modern version of SocialCalc, aiming to recreate the core functionalities of SocialCalc while also introducing new features and improvements that align with current web development standards.

The documentation is divided into two main sections: Frontend and Backend, detailing the technologies, architecture, key functionalities, and interactions between the components.

## Frontend Docs

The Project's frontend is built using <b>Vite with React</b> and <b>TailwindCSS</b>.

#### Setup Instructions

1. Clone the repository
```bash
git clone https://github.com/D3VPAND3Y/SmartSheets.git
```

2. Navigate to the frontend directory
```bash
cd SmartSheets/frontend
```

3. Install the dependencies
```bash
npm install
```

4. Start the development server
```bash
npm run dev
```

#### Functionalities at frontend

1. **User Authentication**: Users can sign up, log in, and log out of the application.
2. **Sheet Management**: Users can create and Edit Sheets.
3. **Collaboration**: Users can share sheets with other users.
4. **Real-time Updates**: Users can see changes made by other users in real-time.

#### Editting features:

1. **Copy-Paste**: Users can copy and paste cells.
2. **Sort**: Users can sort rows and columns.
3. **Undo-Redo**: Users can undo and redo changes.
4. **Delete**: Users can delete cells.
5. **Insert**: Users can insert rows and columns.
6. **Resize**: Users can resize rows and columns.
7. **Rename**: Users can rename the sheet.
8. **Download**: Users can save the sheet locally.
9. **Import**: Users can import CSV files to the sheet.
10. **Collaboration**: Users can share the sheet with other users.
11. **Share**: Users can share the sheet link with other users.
12. **Create New**: Users can create a new sheet.

#### Libraries Used

1. **React**: A JavaScript library for building user interfaces.
2. **Vite**: A build tool that aims to provide a faster and leaner development experience for modern web projects.
3. **TailwindCSS**: A utility-first CSS framework for building custom designs.
4. **HandsonTable**: A JavaScript grid component for web applications.
5. **HyperFormula**: A high-performance formula parser and evaluator for JavaScript.

#### Pages

1. **Sheet**: The main component that renders the sheet grid.
2. **SignIn Page**: The component that renders the sign-in form.
3. **SignUp Page**: The component that renders the sign-up form.
4. **Landing Page**: The component that renders the file cards of existing sheets.
5. **Collaborate Page**: The component that renders the collaboration form.

## Backend Docs

The Project's backend is built using **NodeJS**, **Express** and <b>MongoDB</b>.
**Socket.io** is used for real-time communication between the frontend and backend.

#### Setup Instructions

After cloning the repository, follow the steps below to set up the backend:

1. Navigate to the backend directory
```bash
cd SmartSheets/backend
```

2. Install the dependencies
```bash
npm install
```

3. Start the development server
```bash
nodemon index.js
```

#### Functionalities at backend

1. **User Authentication**: Users can sign up, log in, and log out of the application.
2. **Storage**: Users can store and retrieve sheets from the database.
3. **Collaboration**: Users can share sheets with other users.
4. **Real-time Updates**: Users can see changes made by other users in real-time.

#### Endpoints and Routes

#### Sheet Controller

1. **Create New Sheet**
   - **Endpoint:** `GET /new`
   - **Protected:** Yes (requires `authMiddleWare`)
   - **Description:** Creates a new sheet with a specified ID. Validates input and checks if the sheet already exists.
   - **Query Parameter:** `id` (required)

2. **Get Owned Sheets**
   - **Endpoint:** `GET /owned`
   - **Protected:** Yes (requires `authMiddleWare`)
   - **Description:** Retrieves a list of sheets owned by the authenticated user. The data of the sheets is excluded from the response.

3. **Get Collaborated Sheets**
   - **Endpoint:** `GET /collaborated`
   - **Protected:** Yes (requires `authMiddleWare`)
   - **Description:** Retrieves a list of sheets where the authenticated user is a collaborator. The data of the sheets is excluded from the response.

4. **Get Sheet by ID**
   - **Endpoint:** `GET /:sheetId`
   - **Protected:** No
   - **Description:** Retrieves a specific sheet by its `sheetId`.

5. **Add Collaborator to Sheet**
   - **Endpoint:** `POST /:sheetId/collaborate`
   - **Protected:** Yes (requires `authMiddleWare`)
   - **Description:** Adds the authenticated user as a collaborator to the specified sheet.

#### Authentication Controller

1. **Get Current User**
   - **Endpoint:** `GET /me`
   - **Protected:** Yes (requires `authMiddleWare`)
   - **Description:** Retrieves the current authenticated user’s details.

2. **Sign Up**
   - **Endpoint:** `POST /signup`
   - **Protected:** No
   - **Description:** Creates a new user account. Validates the input and checks for existing email. Returns a JWT token upon successful creation.

3. **Sign In**
   - **Endpoint:** `POST /signin`
   - **Protected:** No
   - **Description:** Authenticates a user with email and password. Returns a JWT token if credentials are correct.

#### Summary of Endpoints

- **Sheet-Related Endpoints:**
  1. `GET /new` - Create a new sheet (protected)
  2. `GET /owned` - Get owned sheets (protected)
  3. `GET /collaborated` - Get collaborated sheets (protected)
  4. `GET /:sheetId` - Get sheet by ID (public)
  5. `POST /:sheetId/collaborate` - Add collaborator to sheet (protected)

- **User Authentication Endpoints:**
  1. `GET /me` - Get current user (protected)
  2. `POST /signup` - Sign up a new user (public)
  3. `POST /signin` - Sign in a user (public)

#### Socket.io

The backend uses **Socket.io** to establish a real-time connection with the frontend. The server listens for events such as `connection`, `join`, `leave`, and `update`. The server emits events such as `update` and `disconnect`.