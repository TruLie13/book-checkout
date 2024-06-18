# Book Checkout API

This is a simple RESTful API for managing a collection of books, including operations to check out and check in books, created using the Gin framework in Go.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [Get All Books](#get-all-books)
  - [Get Book by ID](#get-book-by-id)
  - [Create a New Book](#create-a-new-book)
  - [Check Out a Book](#check-out-a-book)
  - [Check In a Book](#check-in-a-book)
- [Data Structure](#data-structure)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/book-checkout.git
    ```

2. Navigate to the project directory:
    ```sh
    cd book-checkout
    ```

3. Install the required dependencies:
    ```sh
    go get -u github.com/gin-gonic/gin
    ```

4. Run the application:
    ```sh
    go run main.go
    ```

The application will be running at `http://localhost:8080`.

## Usage

You can use tools like `curl`, `Postman`, or any other API client to interact with the API endpoints.

## API Endpoints

### Get All Books

- **URL:** `/books`
- **Method:** `GET`
- **Description:** Retrieves a list of all books.
- **Response:**
    ```json
    [
        {
            "id": "1",
            "title": "The Worshipper of the Image",
            "author": "Richard Le Gallienne",
            "quantity": 2
        },
        ...
    ]
    ```

### Get Book by ID

- **URL:** `/books/:id`
- **Method:** `GET`
- **Description:** Retrieves a book by its ID.
- **Response:**
    ```json
    {
        "id": "1",
        "title": "The Worshipper of the Image",
        "author": "Richard Le Gallienne",
        "quantity": 2
    }
    ```

### Create a New Book

- **URL:** `/books`
- **Method:** `POST`
- **Description:** Creates a new book entry.
- **Request Body:**
    ```json
    {
        "id": "4",
        "title": "New Book Title",
        "author": "New Author",
        "quantity": 10
    }
    ```
- **Response:**
    ```json
    {
        "id": "4",
        "title": "New Book Title",
        "author": "New Author",
        "quantity": 10
    }
    ```

### Check Out a Book

- **URL:** `/checkout`
- **Method:** `PATCH`
- **Description:** Checks out a book (decreases the quantity by 1).
- **Query Parameter:** `id` (the ID of the book to check out)
- **Response:**
    ```json
    {
        "id": "1",
        "title": "The Worshipper of the Image",
        "author": "Richard Le Gallienne",
        "quantity": 1
    }
    ```

### Check In a Book

- **URL:** `/checkin`
- **Method:** `PATCH`
- **Description:** Checks in a book (increases the quantity by 1).
- **Query Parameter:** `id` (the ID of the book to check in)
- **Response:**
    ```json
    {
        "id": "1",
        "title": "The Worshipper of the Image",
        "author": "Richard Le Gallienne",
        "quantity": 3
    }
    ```

## Data Structure

The data structure for a book is as follows:

```go
type book struct {
    ID       string `json:"id"`
    Title    string `json:"title"`
    Author   string `json:"author"`
    Quantity int    `json:"quantity"`
}
