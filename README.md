# Implementing JWT Authentication in Golang

fork 
In this article, we will learn about implementing JWT Authentication in Golang REST APIs and securing it with Authentication Middleware. We will be building a simple, yet neatly organized Golang REST API with packages like Gin for Routing (mostly), GORM for persisting user data to a MySQL Database, and so on.

![Implementing JWT Authentication in Golang](https://codewithmukesh.com/wp-content/uploads/2022/04/Implementing-JWT-Authentication-in-Golang-with-Gin-Gorm-MySQL.png)

Topics covered:

- JWT Explained
- What we will Build?
- Gin Framework – Quick Introduction
- Setting up Database with GORM
- User Registration & Password Hashing
- Generating JWTs
- Authentication Middleware to Valid JWTs
- Gin Routing & Grouping
- Testing Golang API with VSCode REST Client

Read the entire article here: https://codewithmukesh.com/blog/jwt-authentication-in-golang/


### mysqlのセットアップ
```sh
$ go run .
2024/04/23 10:58:51 Connected to Database!
2024/04/23 10:58:52 Database Migration Completed!
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] POST   /api/token                --> jwt-authentication-golang/controllers.GenerateToken (3 handlers)
[GIN-debug] POST   /api/user/register        --> jwt-authentication-golang/controllers.RegisterUser (3 handlers)
[GIN-debug] GET    /api/secured/ping         --> jwt-authentication-golang/controllers.Ping (4 handlers)
[GIN-debug] [WARNING] You trusted all proxies, this is NOT safe. We recommend you to set a value.
Please check https://pkg.go.dev/github.com/gin-gonic/gin#readme-don-t-trust-all-proxies for details.
[GIN-debug] Listening and serving HTTP on :8080
[GIN] 2024/04/23 - 10:59:03 | 201 |  1.133523077s |       127.0.0.1 | POST     "/api/user/register"
```


### 新規ユーザの登録

![alt text](image.png)



![alt text](image-1.png)



###  JSON Web Token (JWT)

![alt text](image-2.png)


[text](https://jwt.io/) 

上記でペイロードに  user名と電子メールが含まれていることが確認できる


###  認証

上記で 以下のトークンが得られたので正確な tokenで secure.restを送る
```sh
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im11a2VzaC5tdXJ1Z2FuIiwiZW1haWwiOiJtdWtlc2hAZ28uY29tIiwiZXhwIjoxNzEzODQxNDYzfQ.dbZT8b3PoaCkAm7D_DTAYxuQbu5Jk6GQY5ox1CgqKJU
```


![alt text](image-3.png)



### dammy

![alt text](image-4.png)