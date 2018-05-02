# gosample

## STEPS and integration with VScode

1. go get -u github.com/kavishrox/gosample
2. go get github.com/gorilla/mux github.com/lib/pq
3. Create a products table as follows:

```
CREATE TABLE products
(
    id SERIAL,
    name TEXT NOT NULL,
    price NUMERIC(10,2) NOT NULL DEFAULT 0.00,
    CONSTRAINT products_pkey PRIMARY KEY (id)
)
```

4. Set .vscode launch.json settings as follows

```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch test function",
      "type": "go",
      "request": "launch",
      "mode": "test",
      "program": "${workspaceRoot}/src/github.com/kavishrox/gosample/main_test.go",
      "args": [
        "-test.run",
        "MyTestFunction"
      ],
      "env": {
        "APP_DB_USERNAME": <DB-USERNAME>,
        "APP_DB_PASSWORD": <DB-PASSWORD>,
        "APP_DB_NAME": <DB-NAME>
      }
    },
    {
      "name": "Launch Package",
      "type": "go",
      "request": "launch",
      "mode": "debug",
      "program": "${workspaceRoot}/src/github.com/kavishrox/gosample/main.go",
      "env": {
        "APP_DB_USERNAME": <DB-USERNAME>,
        "APP_DB_PASSWORD": <DB-PASSWORD>,
        "APP_DB_NAME": <DB-NAME>
      }
    }
  ]
}

5. Voila ! Run debugger from vscode
