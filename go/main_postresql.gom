package main
import (
    "database/sql"
    "fmt"
    _ "github.com/lib/pq"
)
const (
    HOST = "192.168.0.2"
    PORT = 5432
	DB_USER="postgres"
	DB_PASSWORD="changeme"
	DB_NAME="krbn"
)

/*
DROP TABLE IF EXISTS links;

CREATE TABLE links (
	id SERIAL PRIMARY KEY,
	url VARCHAR(255) NOT NULL,
	name VARCHAR(255) NOT NULL,
	description VARCHAR (255),
        last_update DATE
);
*/

///d
func checkErr(err error) {
    if err != nil {
        fmt.Println(err)
    }
}

func main() {
    psqlInfo := fmt.Sprintf("host=%s port=%d user=%s "+
      "password=%s dbname=%s sslmode=disable",
      HOST, PORT, DB_USER, DB_PASSWORD, DB_NAME)
    db, err := sql.Open("postgres", psqlInfo)
    if err != nil {
      panic(err)
    }

    defer db.Close()
  
    sqlStatement := `
  INSERT INTO links (url, name, description)
  VALUES ($1, $2, $3)
  RETURNING id`
    id := 0
    err = db.QueryRow(sqlStatement,  "jon@calhoun.io", "Jonathan", "Calhoun").Scan(&id)
    if err != nil {
      panic(err)
    }
    fmt.Println("New record ID is:", id)
  }