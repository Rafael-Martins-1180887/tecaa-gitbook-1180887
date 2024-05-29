# Example 2

Suppose we have a REST API for a Fruit object, defined as such:

```
Endpoint: /api/fruits

Methods:

GET /api/fruits: Retrieves a list of fruits.
GET /api/fruits/{id}: Retrieves a single fruit by ID.
POST /api/fruits: Creates a new fruit.
PUT /api/fruits/{id}: Updates an existing fruit.
DELETE /api/fruits/{id}: Deletes a fruit.
```

## Negative Example

Here is an example of a documentation containing this smell:

> #### Fruit API Documentation
>
> The `Fruit` API allows you to manage fruits in the system. It provides endpoints to create, retrieve, update, and delete fruits.
>
> **API Endpoints**
>
> * **GET /api/fruits**
>   * **Description**: Retrieves a list of all fruits.
>   * **Internal Details**: This endpoint queries the `fruits` table in the database and retrieves all entries. It uses a SQL `SELECT * FROM fruits` statement and maps the result to a list of `Fruit` objects. The database connection is handled by a connection pool with a maximum of 10 connections.
> * **GET /api/fruits/{id}**
>   * **Description**: Retrieves a single fruit by its unique ID.
>   * **Internal Details**: This endpoint uses a SQL `SELECT * FROM fruits WHERE id = ?` statement. The ID is passed as a parameter to prevent SQL injection. The result is mapped to a `Fruit` object, which includes attributes like `name`, `color`, and `quantity`.
> * **POST /api/fruits**
>   * **Description**: Creates a new fruit entry.
>   * **Internal Details**: This endpoint uses a SQL `INSERT INTO fruits (name, color, quantity) VALUES (?, ?, ?)` statement. It internally validates the `name` to ensure it is unique and not null. If the `color` is not specified, it defaults to "unknown". The transaction is managed to ensure atomicity.
> * **PUT /api/fruits/{id}**
>   * **Description**: Updates an existing fruit entry.
>   * **Internal Details**: This endpoint uses a SQL `UPDATE fruits SET name = ?, color = ?, quantity = ? WHERE id = ?` statement. It locks the row to prevent race conditions and ensures that the `id` exists before updating.
> * **DELETE /api/fruits/{id}**
>   * **Description**: Deletes a fruit entry.
>   * **Internal Details**: This endpoint uses a SQL `DELETE FROM fruits WHERE id = ?` statement. It checks for referential integrity to ensure no other table references the fruit before deletion. The operation is logged for auditing purposes.

Whilst the initial API description and the description inside each endpoint is simple and focuses only on giving context to the API, the "Internal Details" sections are a clear example of this smell, giving too much detail on the internal works of the program.

## Positive Example

In the case of REST (and similar) APIs, the  recommended way to provide API documentation free of this smell is by focusing on giving practical examples for each endpoint:

> #### Fruit API Documentation
>
> The `Fruit` API allows you to manage fruits in the system. It provides endpoints to create, retrieve, update, and delete fruits.
>
> **API Endpoints**
>
> * **GET /api/fruits**
>   * **Description**: Retrieves a list of all fruits.
>   * **Response**: Returns a JSON array of fruit objects.
>   *   **Example Response**:
>
>       ```json
>       [
>         {
>           "id": 1,
>           "name": "Apple",
>           "color": "Red",
>           "quantity": 10
>         },
>         {
>           "id": 2,
>           "name": "Banana",
>           "color": "Yellow",
>           "quantity": 20
>         }
>       ]
>       ```
> * **GET /api/fruits/{id}**
>   * **Description**: Retrieves a single fruit by its unique ID.
>   * **Path Parameters**:
>     * `id` (integer): The unique identifier of the fruit.
>   * **Response**: Returns a JSON object representing the fruit.
>   *   **Example Response**:
>
>       ```json
>       {
>         "id": 1,
>         "name": "Apple",
>         "color": "Red",
>         "quantity": 10
>       }
>       ```
> * **POST /api/fruits**
>   * **Description**: Creates a new fruit entry.
>   *   **Request Body**:
>
>       ```json
>       {
>         "name": "Strawberry",
>         "color": "Red",
>         "quantity": 30
>       }
>       ```
>   * **Response**: Returns the created fruit object with its ID.
>   *   **Example Response**:
>
>       ```json
>       {
>         "id": 3,
>         "name": "Strawberry",
>         "color": "Red",
>         "quantity": 30
>       }
>       ```
> * **PUT /api/fruits/{id}**
>   * **Description**: Updates an existing fruit entry.
>   * **Path Parameters**:
>     * `id` (integer): The unique identifier of the fruit.
>   *   **Request Body**:
>
>       ```json
>       {
>         "name": "Green Apple",
>         "color": "Green",
>         "quantity": 15
>       }
>       ```
>   * **Response**: Returns the updated fruit object.
>   *   **Example Response**:
>
>       ```json
>       {
>         "id": 1,
>         "name": "Green Apple",
>         "color": "Green",
>         "quantity": 15
>       }
>       ```
> * **DELETE /api/fruits/{id}**
>   * **Description**: Deletes a fruit entry.
>   * **Path Parameters**:
>     * `id` (integer): The unique identifier of the fruit.
>   * **Response**: Returns a success message.
>   *   **Example Response**:
>
>       ```json
>       {
>         "message": "Fruit deleted successfully."
>       }
>       ```

This way the user clearly understands by example what to send and what to expect to receive as response in each of the endpoints, while the internal mechanisms of how it happens remain a black box.
