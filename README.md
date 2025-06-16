# Bookshelf API Project

## Description

This project is a simple RESTful API built with Node.js and Hapi. This API allows users to manage a digital collection of books. Users can add, view, update, and delete book data.

This project is an implementation of the submission for the "Learning to Build Back-End Applications for Beginners" class from Dicoding.

## Key Features

- **Add a New Book**: Saves a new book to the shelf.
- **Get All Books**: Retrieves a list of all stored books.
    - Includes filtering options by `name`, `reading` status, and `finished` status.
- **Get Book Details**: Fetches complete information for a single book using its unique ID.
- **Update Book Data**: Updates an existing book's data based on its ID.
- **Delete a Book**: Removes a book from the shelf based on its ID.

## Technologies Used

- **Node.js**: A JavaScript runtime environment for the server side.
- **Hapi**: A framework for building web applications and services.
- **nanoid**: A library for generating compact and secure unique IDs.

## Installation & Setup

1.  **Clone this repository:**
    ```bash
    git clone [https://github.com/username/bookshelf-api.git](https://github.com/username/bookshelf-api.git)
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd bookshelf-api
    ```
3.  **Install all required dependencies:**
    ```bash
    npm install
    ```
4.  **Run the development server:**
    ```bash
    npm run start
    ```
    The server will run on `http://localhost:9000` (or another port depending on your configuration).

## API Documentation

Below are the details for each available endpoint.

---

### 1. Add a New Book

Saves a new book object to the data store.

-   **Endpoint**: `POST /books`
-   **Method**: `POST`
-   **Headers**:
    -   `Content-Type: application/json`
-   **Request Body** (JSON):

    ```json
    {
        "name": "Bumi Manusia",
        "year": 2005,
        "author": "Pramoedya Ananta Toer",
        "summary": "A historical novel set in the colonial era...",
        "publisher": "Lentera Dipantara",
        "pageCount": 535,
        "readPage": 250,
        "reading": true
    }
    ```

-   **Criteria & Validation**:
    -   `name` (string, required): The book name cannot be empty.
    -   `readPage` (number) cannot be greater than `pageCount` (number).

-   **Success Response** (`201 Created`):
    ```json
    {
        "status": "success",
        "message": "Book added successfully",
        "data": {
            "bookId": "aBc123DeFg45"
        }
    }
    ```

-   **Error Responses**:
    -   `400 Bad Request` (if the name is missing or `readPage` > `pageCount`):
      ```json
      {
          "status": "fail",
          "message": "Failed to add book. Please provide the book name"
      }
      ```
    -   `500 Internal Server Error` (in case of a server-side error):
      ```json
      {
          "status": "error",
          "message": "Failed to add book"
      }
      ```

---

### 2. Get All Books

Retrieves a list of all books. Supports filtering via query parameters.

-   **Endpoint**: `GET /books`
-   **Method**: `GET`
-   **Query Parameters** (Optional):
    -   `name` (string): Filter books by name (case-insensitive search).
        -   Example: `GET /books?name=bumi`
    -   `reading` (number): Filter books by reading status. `1` for `true`, `0` for `false`.
        -   Example: `GET /books?reading=1`
    -   `finished` (number): Filter books by finished status. `1` for `true`, `0` for `false`.
        -   Example: `GET /books?finished=0`

-   **Success Response** (`200 OK`):
    ```json
    {
        "status": "success",
        "data": {
            "books": [
                {
                    "id": "aBc123DeFg45",
                    "name": "Bumi Manusia",
                    "publisher": "Lentera Dipantara"
                },
                {
                    "id": "xYz987WvU654",
                    "name": "Laskar Pelangi",
                    "publisher": "Bentang Pustaka"
                }
            ]
        }
    }
    ```
-   If no books exist, `books` will be an empty array `[]`.

---

### 3. Get Book Details

Retrieves the complete information for a book by its ID.

-   **Endpoint**: `GET /books/{bookId}`
-   **Method**: `GET`
-   **URL Parameters**:
    -   `bookId` (string, required): The unique ID of the book.

-   **Success Response** (`200 OK`):
    ```json
    {
        "status": "success",
        "data": {
            "book": {
                "id": "aBc123DeFg45",
                "name": "Bumi Manusia",
                "year": 2005,
                "author": "Pramoedya Ananta Toer",
                "summary": "A historical novel set in the colonial era...",
                "publisher": "Lentera Dipantara",
                "pageCount": 535,
                "readPage": 250,
                "finished": false,
                "reading": true,
                "insertedAt": "2025-06-16T13:23:00.000Z",
                "updatedAt": "2025-06-16T13:23:00.000Z"
            }
        }
    }
    ```
-   **Error Response** (`404 Not Found`):
    ```json
    {
        "status": "fail",
        "message": "Book not found"
    }
    ```

---

### 4. Update Book Data

Updates the data of an existing book based on its ID.

-   **Endpoint**: `PUT /books/{bookId}`
-   **Method**: `PUT`
-   **URL Parameters**:
    -   `bookId` (string, required): The ID of the book to be updated.
-   **Request Body** (JSON): Same as `POST /books`.

-   **Criteria & Validation**:
    -   `name` (string, required): The book name cannot be empty.
    -   `readPage` (number) cannot be greater than `pageCount` (number).

-   **Success Response** (`200 OK`):
    ```json
    {
        "status": "success",
        "message": "Book updated successfully"
    }
    ```
-   **Error Responses**:
    -   `400 Bad Request` (if validation fails):
        ```json
        {
            "status": "fail",
            "message": "Failed to update book. readPage cannot be greater than pageCount"
        }
        ```
    -   `404 Not Found` (if `bookId` does not exist):
        ```json
        {
            "status": "fail",
            "message": "Failed to update book. Id not found"
        }
        ```

---

### 5. Delete a Book

Removes a book from the data store based on its ID.

-   **Endpoint**: `DELETE /books/{bookId}`
-   **Method**: `DELETE`
-   **URL Parameters**:
    -   `bookId` (string, required): The ID of the book to be deleted.

-   **Success Response** (`200 OK`):
    ```json
    {
        "status": "success",
        "message": "Book deleted successfully"
    }
    ```
-   **Error Response** (`404 Not Found`):
    ```json
    {
        "status": "fail",
        "message": "Failed to delete book. Id not found"
    }
    ```

## 🤝 Contributing

We welcome contributions! If you'd like to help improve the project:

1.  **Fork** the repository.
2.  Create your **Feature Branch** (`git checkout -b feature/AmazingFeature`).
3.  **Commit** your changes (`git commit -m 'feat: Add some AmazingFeature'`).
4.  **Push** to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a **Pull Request**.

## 📄 License

This project is licensed under the [MIT License](https://opensource.org/license/mit). See the `LICENSE` file for more details.

## 📬 Contact

**Satria Nur Saputro**
- Email: [satrianursaputro06@gmail.com](mailto:satrianursaputro06@gmail.com)