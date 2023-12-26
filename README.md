# casbin_gf

GoFrame Permission Plugin

Support MySQL, SQLite, PostgreSQL, Oracle, SQL Server Power By GoFrame ORM

## Use

Download and install

```shell
go get github.com/kshdb/casbin_gf
```

Demo

```go
package main

import (
	"fmt"
	"log"
	"github.com/kshdb/casbin_gf"
)

func main() {
	enforcer, err := casbin.NewEnforcer(&casbin.Options{
		Model:     "./example/model.conf",
		Debug:     false,
		Enable:    true,
		AutoLoad:  true,
		Table:   "casbin_policy_test",
		Link:    "mysql:root:123456@tcp(127.0.0.1:3306)/topic1",
	})

	if err != nil {
		log.Fatalf("Casbin init failure:%s \n", err.Error())
	}

	// add a permission node for role
	ok, err := enforcer.AddPolicy("role_1", "node_1")

	if err != nil {
		log.Fatalf("Add policy exception:%s \n", err.Error())
	}

	if ok {
		log.Println("Add policy successful")
	} else {
		log.Println("Add policy failure")
	}
}
```

## Example

View demo [example/main.go](example/main.go)

## Model Demo

View demo [example/model.conf](example/model.conf)