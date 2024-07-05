# README

## Calculator Using Golang

This project is a simple HTTP server written in Go that performs basic arithmetic operations (addition, subtraction, multiplication, and division) on two numbers provided in a JSON request. The server listens on port 8090.

### Prerequisites

- Go 1.13 or higher

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/saro0307/calculator-using-golang.git
   ```
2. Navigate to the project directory:
   ```sh
   cd calculator-using-golang
   ```

### Usage

1. Build and run the server:
   ```sh
   go run main.go
   ```
   The server will start listening on `http://localhost:8090`.

2. Send a POST request with a JSON payload to the server:
   ```sh
   curl -X POST http://localhost:8090/ -d '{"num1": 10, "num2": 5}' -H "Content-Type: application/json"
   ```

### Example

**Request:**

```json
{
  "num1": 10,
  "num2": 5
}
```

**Response:**

```json
{
  "add": 15,
  "mul": 50,
  "sub": 5,
  "div": 2
}
```

### API Endpoint

- **`POST /`**
  - **Request Body:** JSON object with the fields `num1` and `num2`, both of which are float64.
  - **Response Body:** JSON object with the results of addition (`add`), multiplication (`mul`), subtraction (`sub`), and division (`div`).

### Code Explanation

1. **Structs:**
    - `numbers`: Represents the input JSON object with `num1` and `num2` as fields.
    - `numsResponseData`: Represents the response JSON object with the results of the arithmetic operations.

2. **Functions:**
    - `process(numsdata numbers) numsResponseData`: Takes a `numbers` object as input and returns a `numsResponseData` object with the results of the arithmetic operations.
    - `calc(w http.ResponseWriter, request *http.Request)`: HTTP handler function that decodes the JSON request, processes the numbers, and encodes the JSON response.

3. **Main Function:**
    - `main()`: Sets up the HTTP server to handle requests at the root endpoint (`"/"`) using the `calc` function.

### Error Handling

The current implementation does not include extensive error handling. It is recommended to add checks for division by zero and ensure valid JSON payloads in production code.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Acknowledgements

This simple arithmetic server was created as a learning project and is intended for educational purposes.

---

Feel free to contribute, report issues, or fork this repository for your own use!
