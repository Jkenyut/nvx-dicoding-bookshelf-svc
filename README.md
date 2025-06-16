<div align="center">
  <h1 align="center">📚 Bookshelf API Project</h1>
  <p align="center">
    A simple and efficient RESTful API for managing a digital book collection.
  </p>

  <p align="center">
    <a href="https://opensource.org/license/mit"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
    <img src="https://img.shields.io/badge/Node.js-18.x-green.svg" alt="Node.js">
    <img src="https://img.shields.io/badge/Framework-Hapi-orange" alt="Hapi.js">
    <img src="https://img.shields.io/badge/ID-Nanoid-2ca5e0" alt="Nanoid">
  </p>
</div>

---

### **TABLE OF CONTENTS**

* [✨ About The Project](#-about-the-project)
    * [Key Features](#key-features)
    * [Tech Stack](#tech-stack)
* [🚀 Getting Started](#-getting-started)
    * [Prerequisites](#prerequisites)
    * [Installation](#installation)
* [🔧 API Documentation](#-api-documentation)
* [🤝 Contributing](#-contributing)
* [📄 License](#-license)
* [📬 Contact](#-contact)

---

## ✨ **About The Project**

This project is a straightforward RESTful API designed with Node.js and the Hapi framework. It provides a clean and simple interface to manage a digital book collection, allowing users to perform standard CRUD (Create, Read, Update, Delete) operations.

This API was developed as a submission for the "Learning to Build Back-End Applications for Beginners" class by Dicoding.

### **Key Features**

* **Add a New Book**: Save new books to your collection.
* **Get All Books**: Retrieve a list of all stored books.
* **Filter & Search**: Dynamically filter books by `name`, `reading` status, or `finished` status.
* **Get Book Details**: Fetch complete information for a single book using its unique ID.
* **Update Book Data**: Modify the details of an existing book.
* **Delete a Book**: Remove a book from the collection.

### **Tech Stack**

| Technology | Description |
| :--- | :--- |
| **Node.js** | A JavaScript runtime for server-side execution. |
| **Hapi** | A rich and powerful framework for building web applications. |
| **nanoid** | A library for generating compact and secure unique IDs. |

---

## 🚀 **Getting Started**

To get a local copy up and running, follow these steps.

### **Prerequisites**

* Node.js (v18.16.0 or higher is recommended)
* NPM (Node Package Manager)

### **Installation**

1.  **Clone this repository:**
    ```sh
    git clone [https://github.com/username/bookshelf-api.git](https://github.com/username/bookshelf-api.git)
    ```
2.  **Navigate to the project directory:**
    ```sh
    cd bookshelf-api
    ```
3.  **Install all required dependencies:**
    ```sh
    npm install
    ```
4.  **Run the development server:**
    ```sh
    npm run start
    ```
    The server will start on `http://localhost:9000` (or another port depending on your configuration).

---

## 🔧 **API Documentation**

Below are the details for each available endpoint.

<details>
<summary><strong>1. Add a New Book</strong></summary>

Saves a new book object to the data store.

-   **Endpoint**: `POST /books`
-   **Headers**: `Content-Type: application/json`
-   **Request Body**:
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
-   **Validation**:
    -   `name` is required.
    -   `readPage` cannot be greater than `pageCount`.
-   **Success Response** (`201 Created`):
    ```json
    { "status": "success", "message": "Book added successfully", "data": { "bookId": "aBc123DeFg45" } }
    ```

</details>

<details>
<summary><strong>2. Get All Books</strong></summary>

Retrieves a list of all books, with optional filtering.

-   **Endpoint**: `GET /books`
-   **Query Parameters** (Optional):
    -   `name` (string): Filter by name (case-insensitive).
    -   `reading` (number): `1` for true, `0` for false.
    -   `finished` (number): `1` for true, `0` for false.
-   **Success Response** (`200 OK`):
    ```json
    {
        "status": "success",
        "data": {
            "books": [
                { "id": "aBc123DeFg45", "name": "Bumi Manusia", "publisher": "Lentera Dipantara" }
            ]
        }
    }
    ```
</details>

<details>
<summary><strong>3. Get Book Details</strong></summary>

Retrieves the complete information for a book by its ID.

-   **Endpoint**: `GET /books/{bookId}`
-   **Success Response** (`200 OK`):
    ```json
    { "status": "success", "data": { "book": { ...full book object... } } }
    ```
-   **Error Response** (`404 Not Found`):
    ```json
    { "status": "fail", "message": "Book not found" }
    ```
</details>

<details>
<summary><strong>4. Update Book Data</strong></summary>

Updates the data of an existing book by its ID.

-   **Endpoint**: `PUT /books/{bookId}`
-   **Request Body**: Same as adding a new book.
-   **Success Response** (`200 OK`):
    ```json
    { "status": "success", "message": "Book updated successfully" }
    ```
-   **Error Response** (`404 Not Found`):
    ```json
    { "status": "fail", "message": "Failed to update book. Id not found" }
    ```

</details>

<details>
<summary><strong>5. Delete a Book</strong></summary>

Removes a book from the data store by its ID.

-   **Endpoint**: `DELETE /books/{bookId}`
-   **Success Response** (`200 OK`):
    ```json
    { "status": "success", "message": "Book deleted successfully" }
    ```
-   **Error Response** (`404 Not Found`):
    ```json
    { "status": "fail", "message": "Failed to delete book. Id not found" }
    ```
</details>

---

## 🤝 **Contributing**

We welcome contributions! If you'd like to help improve the project:

1.  **Fork** the repository.
2.  Create your **Feature Branch** (`git checkout -b feature/AmazingFeature`).
3.  **Commit** your changes (`git commit -m 'feat: Add some AmazingFeature'`).
4.  **Push** to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a **Pull Request**.

---

## 📄 **License**

This project is licensed under the [MIT License](https://opensource.org/license/mit). See the `LICENSE` file for more details.

---

## 📬 **Contact**

**Satria Nur Saputro**
- Email: [satrianursaputro06@gmail.com](mailto:satrianursaputro06@gmail.com)