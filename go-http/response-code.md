# Response Code

Code :

```go
 w.WriteHeader(http.StatusBadRequest)
```

atau

```go
fmt.Println("Success", http.StatusOK)
```

## List of Frequently Used Response Code

200 -> http.StatusOk -> Ok

201 -> http.StatusCreated -> Created

204 -> http.StatusNoContent -> No Content

400 -> http.StatusBadRequest -> Bad Request

401 -> http.StatusUnauthorized -> Unauthorized

404 -> http.StatusNotFound -> Not Found

405 -> http.StatusMethodNotAllowed -> Method Not Allowed

409 -> http.http.StatusConflict -> Conflict

500 -> http.StatusInternalServerError -> Internal Server Error

