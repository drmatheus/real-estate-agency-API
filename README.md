# Real Estate Agency API

This API provides functionality for a real estate agency, allowing users to register properties, users, schedule visits, and list properties by specific categories.

## Getting Started

### Prerequisites

Before running the project, make sure you have the following prerequisites installed:

- [Node.js](https://nodejs.org) installed on your machine.
- [npm](https://www.npmjs.com/) or [Yarn](https://yarnpkg.com/) package manager.
- [PostgreSQL](https://www.postgresql.org/) database installed and running.

## Installation

1. Clone the repository:

   ```
   git clone git@github.com:drmatheus/real-estate-agency-API.git
   ```

2. Navigate to the project directory:

   ```
   cd real-estate-agency-API
   ```

3. Install the dependencies:

   ```
   npm install
   ```

   or

   ```
   yarn install
   ```

## Database Setup

1. Create a new PostgreSQL database for the project.

2. Configure the database connection in the .env file.

3. Run the database migrations:
   ```
   npm run typeorm migration:run -d ./src/data-source
   ```
   or
   ```
   yarn typeorm migration:run -d ./src/data-source
   ```

## Running the Project

To start the project locally, run the following command:

```
yarn dev
```

or

```
npm run dev
```

The API will be accessible at http://localhost:3000.

## Usage

### **List Users**

GET /users

> Description: List all users.
>
> Authentication: Required.

### **Retrieve User Data**

GET /users/:id

> Description: Retrieve user data by ID.
>
> Authentication: Required.

### **Create a New User**

POST /users

> Description: Create a new user.
>
> Authentication: Not required.
>
> Request Body:

        {
        "name": "John Doe",
        "email": "johndoe@example.com",
        "password": "secretpassword123",
        "admin": true
        }

### **Update User Data**

PATCH /users/:id

> Description: Update user data.
>
> Authentication: Required.
>
> Request Body:

        {
        "name": "Updated Name"
        }

### **Delete User**

DELETE /users/:id

> Description: Delete a user.
>
> Authentication: Required.

### **List Real Estates**

GET /realEstate

> Description: List all real estates.
>
> Authentication: Not required.

### **Create a New Real Estate**

POST /realEstate

> Description: Create a new real estate.
>
> Authentication: Required.
>
> Request Body:

        {
            "sold": false,
            "value": 250000,
            "size": 150,
            "address": {
                "street": "Main Street",
                "zipCode": "12345",
                "number": "123",
                "city": "Exampleville",
                "state": "EX"
            },
            "categoryId": optional
        }

### **Retrieve Real Estate Data**

GET /realEstate/:id

> Description: Retrieve real estate data by ID.
>
> Authentication: Not required.

### **Schedule a Visit**

POST /schedules

> Description: Schedule a visit for a real estate.
>
> Authentication: Required.
>
> Request Body:

        {
        "realEstateId": "123456",
        "date": "2023-06-25",
        "time": "10:00"
        }

### **Get Schedules for a Real Estate**

GET /schedules/realEstate/:id

> Description: Get schedules for a specific real estate.
>
> Authentication: Required.

### **Get Real Estate by Category**

GET /categories/:id/realEstate

> Description: Get all real estate properties belonging to a specific category based on the category ID.
>
> Authentication: Not required.

### **Get All Categories**

GET /categories

> Description: Get all categories of real estate properties.
>
> Authentication: None required.

### **Create Category**

POST /categories

> Description: Create a new category for real estate properties.
>
> Authentication: Required.
>
> Request Body:

        {
        "name": "Apartment"
        }

**_Note: Routes that require authentication need to include valid authentication credentials, such as a token or session, in the request headers._**
