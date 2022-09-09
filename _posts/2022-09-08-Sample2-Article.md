---
layout:     post
title:      Another Sample Blog Title
subtitle:   Another Sample Blog Subtitle
date:       2022-09-08
author:     CYC
header-img: img/home-bg-o.jpg
catalog: True
tags:
    - Sample
    - Original
---

> The following are all text and code for testing
> Copied from one of the [Go Practice Projects](https://github.com/YechengChu/practice-go-project/blob/master/proj1/README.md)

# 📝 用Golang实现用户注册登录功能

> In this mini project, postgres and redis are used, my notes on the simple use of postgres and redis are avaliable
> - Click [here](https://github.com/YechengChu/practice-go-project/raw/master/proj1/Golang操作postgres数据库.pdf) to download my note for the use of postgres
> - Click [here](https://github.com/YechengChu/practice-go-project/raw/master/proj1/Redis使⽤.pdf) to download my note for the use of redis

## 目标

- 打开localhost:3000/signup，填写注册信息
   - 用户名(验证要求：手机号码或邮箱)
   - 密码(拥有大小写字母及数字，至少8位)
- 打开localhost:3000/signin，显示登录框(可填写用户名和密码)，登录框下方有按钮可以调到signup页面注册
   - 若登录成功 -> 跳转localhost:3000/profile，显示用户名及Login Succeeded
   - 若登录失败 -> 停留当前页面，显示Login Failed
- 登录状态保持在前端，未登录状态打开localhost:3000/profile，跳转至localhost:3000/signin

## 模块需求

- 任选一种web framework [https://github.com/mingrammer/go-web-framework-stars](https://github.com/mingrammer/go-web-framework-stars)
- 数据库使用postgres
- 登录状态缓存使用redis

## 运行
```
$ chmod +x redis.sh
$ ./redis.sh
$ go build -o app
$ ./app
```
注：需要安装postgres和redis
## 展示
运行后，先会别要求输入postgres的连接数据，当postgres连接成功后就可以打开网页了
打开浏览器输入网址
```
localhost:3000
```
就会进入index页面
![Screen Shot 2020-07-29 at 19.52.12.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023563507-ae0ef904-5d8a-4aba-b217-93440e57f550.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.52.12.png&originHeight=900&originWidth=1440&size=44978&status=done&style=none&width=1440)
点击profile，会跳转登陆界面
![Screen Shot 2020-07-29 at 19.52.57.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023603809-eb23c2f6-cdd2-422e-96b3-500307e73ad2.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.52.57.png&originHeight=900&originWidth=1440&size=57174&status=done&style=none&width=1440)
登陆界面有按钮可以跳转注册页面
![Screen Shot 2020-07-29 at 19.53.56.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023644047-2a148f72-d181-475e-92b0-580396eab961.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.53.56.png&originHeight=900&originWidth=1440&size=55170&status=done&style=none&width=1440)
注册界面会对用户提供的用户名和密码进行检查
![Screen Shot 2020-07-29 at 19.54.50.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023753711-083227af-e530-4317-9931-9833b65c790a.png#align=left&display=inline&height=268&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.54.50.png&originHeight=357&originWidth=761&size=32817&status=done&style=none&width=571)
![Screen Shot 2020-07-29 at 19.55.07.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023764999-90e29d7b-c8b1-4a26-a580-df4919e7a0d5.png#align=left&display=inline&height=270&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.55.07.png&originHeight=360&originWidth=771&size=33569&status=done&style=none&width=578)
![Screen Shot 2020-07-29 at 19.55.22.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023774066-2d1c37a4-fa0f-474b-9340-adecb51811e6.png#align=left&display=inline&height=277&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.55.22.png&originHeight=370&originWidth=775&size=31470&status=done&style=none&width=581)

注册成功后会跳转profile界面
![Screen Shot 2020-07-29 at 19.57.16.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023847930-d7a6bde3-f120-4e0e-8532-64f435ab2b4f.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.57.16.png&originHeight=900&originWidth=1440&size=53620&status=done&style=none&width=1440)
点击home可以到index界面，此时导航栏的显示是登陆状态的显示(有logout，无register和login)
![Screen Shot 2020-07-29 at 19.57.49.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596023946268-376ee6fd-d017-4744-b6cb-05411b6f22c9.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2019.57.49.png&originHeight=900&originWidth=1440&size=44211&status=done&style=none&width=1440)
点击logout即可退出，退出后会被跳转到首页，此时导航栏显示为未登陆状态的显示
![Screen Shot 2020-07-29 at 20.01.30.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596024206236-05288c0c-b4e5-4cbd-b120-0f1a0ccbb18d.png#align=left&display=inline&height=900&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2020.01.30.png&originHeight=900&originWidth=1440&size=44966&status=done&style=none&width=1440)
点击login，进行登陆，登陆时会检查用户名和密码是否存在于数据库中
![Screen Shot 2020-07-29 at 20.03.52.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596024277291-9aa8412e-12c4-460f-90e2-6302cdb65c79.png#align=left&display=inline&height=326&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2020.03.52.png&originHeight=434&originWidth=771&size=31826&status=done&style=none&width=578)
## 各golang文件功能
### sqlHandeler.go
负责postgres数据库的操作，包括

- 连接数据库
- 断开数据库
- 向数据库插入数据
- 在数据库中查询数据
### redisHandler.go
负责redis数据库的操作，包括

- 连接redis server
- 断开与redis server的连接
- 向redis中添加session token和用户名
- 根据session token确定用户是否登陆
- 根据session token来查询用户名
- 从redis中删除session token和其对应的用户名
### main.go
项目的入口，负责

- 调用sqlHandler和redisHandler的连接和断开方法
- 启动路由
- 加载网页模版
- 启动网页
- 提供渲染所有页面的方法(render function)
### routes.go
主要负责路由

- 根据url调用handlers.user中的方法
- 负责展示index页面
### handlers.user.go
负责处理用户的操作并调用main中的方法来渲染和用户操作相对应的html
handlers.user提供的操作有

- 用户登陆
- 展示登陆界面
- 生成session token
- 展示用户profile
- 用户登出
- 展示注册界面
- 用户注册
### models.user.go
具体负责通过sqlHandler提供的方法与postgres数据库交互来提供用户的信息验证

- 检查用户名和密码是否对应
- 具体负责注册新用户
   - 检查用户名是否可用
   - 检查用户名是否为邮箱或手机
   - 检查密码格式是否正确
- 检查用户名是否可用（如果用户名不在数据库中即为可用）
### middleware.auth.go
确保用户已经登陆/已经登出

- 确保用户已经登陆，如未登陆会产生panic
- 确保用户未登陆，如已经登陆会产生panic
## 各html文件介绍
### header.html
html文件的header格式
### footer.html
html文件的footer格式
### menu.html
在header中被使用
会根据用户是否登陆展示不同的项目
### index.html
网站主界面
### register.html
用户注册界面
### login.html
用户登陆界面
### logged.html
profile展示界面
## Note
Code adapted from [https://github.com/demo-apps/go-gin-app](https://github.com/demo-apps/go-gin-app)

---

## 附录
### 目录结构
![Screen Shot 2020-07-29 at 20.01.18.png](https://cdn.nlark.com/yuque/0/2020/png/1609946/1596024101771-107002b9-eb5a-42b9-81a3-aa7e4ada64a4.png#align=left&display=inline&height=531&margin=%5Bobject%20Object%5D&name=Screen%20Shot%202020-07-29%20at%2020.01.18.png&originHeight=531&originWidth=774&size=131095&status=done&style=none&width=774)
### 代码
#### sqlHandeler.go
```go
package main

import (
	"database/sql"
	"fmt"
	"strconv"
	"strings"

	"io/ioutil"

	_ "github.com/lib/pq"
)

var (
	host     = "localhost"
	port     = 5432
	user     = "postgres"
	password = ""
	dbname   = "postgres"
)

var db *sql.DB

func checkErr(err error) {
	if err != nil {
		panic(err)
	}
}
func getDbInfo() {
	var userHost string
	fmt.Print("Server[localhost]: ")
	fmt.Scanln(&userHost)
	if strings.TrimSpace(userHost) != "" {
		host = userHost
	}

	var userDB string
	fmt.Print("Database[postgres]: ")
	fmt.Scanln(&userDB)
	if strings.TrimSpace(userDB) != "" {
		dbname = userDB
	}

	var userPort string
	fmt.Print("Port[5432]: ")
	fmt.Scanln(&userPort)
	if strings.TrimSpace(userPort) != "" {
		intPort, err := strconv.Atoi(userPort)
		checkErr(err)
		port = intPort
	}

	var userName string
	fmt.Print("Username[postgres]: ")
	fmt.Scanln(&userName)
	if strings.TrimSpace(userName) != "" {
		user = userName
	}

	fmt.Print("Password for user postgres: ")
	fmt.Scanln(&password)
}

func insert(givenAcc string, givenPass string) {
	psqlInfo := fmt.Sprintf("INSERT INTO users(account, password) VALUES('%s','%s');", givenAcc, givenPass)
	_, err := db.Exec(psqlInfo)
	checkErr(err)
}

func query(givenAcc string) (hasAccount bool, pass string) {
	hasAccount = false
	pass = ""
	psqlInfo := fmt.Sprintf("SELECT password FROM users WHERE account='%s';", givenAcc)
	info, err := db.Query(psqlInfo)
	checkErr(err)
	// fmt.Printf("info has type %T\n", info)
	for info.Next() {
		err = info.Scan(&pass)
		checkErr(err)
		hasAccount = true
	}
	return
} // query

func initDB() {
	getDbInfo()
	openDBSQL := fmt.Sprintf("host=%s port=%d user=%s "+
		"password=%s dbname=%s sslmode=disable",
		host, port, user, password, dbname)

	sqlBytes, err := ioutil.ReadFile("createTable.sql")
	checkErr(err)
	sqlCommand := string(sqlBytes)

	var errOpenDB error
	db, errOpenDB = sql.Open("postgres", openDBSQL)
	// fmt.Printf("db has type of %T\n", db)
	checkErr(errOpenDB)
	_, err = db.Exec(sqlCommand)
	checkErr(err)
}

func closeDB() {
	db.Close()
}
```
#### redisHandler.go
```go
package main

import (
	"fmt"
	"os"

	"github.com/gomodule/redigo/redis"
)

var c redis.Conn

func errCheck(info string, err error) {
	if err != nil {
		fmt.Printf("%s %v\n", info, err)
		os.Exit(-1)
	}
}

func connectRedis() {
	var err error
	c, err = redis.Dial("tcp", "127.0.0.1:6379")
	errCheck("Connect to redis error:", err)
}

func closeRedis() {
	c.Close()
}

func addInRedis(sessionIDGiven string, account string) {
	_, err := c.Do("SET", sessionIDGiven, account)
	errCheck("redis set failed:", err)
}

func isLoggedInRedis(sessionIDGiven string) bool {
	is_key_exit, err := redis.Bool(c.Do("EXISTS", sessionIDGiven))
	errCheck("error:", err)
	return is_key_exit
}

func getInRedis(sessionIDGiven string) string {
	account, err := redis.String(c.Do("GET", sessionIDGiven))
	errCheck("redis get failed:", err)
	return account
}

func removedInRedis(sessionIDGiven string) {
	_, err := c.Do("DEL", sessionIDGiven)
	errCheck("redis delete failed:", err)
}
```
#### main.go
```go
// main.go

package main

import (
	"net/http"

	"github.com/gin-gonic/gin"
)

var router *gin.Engine

func main() {
	// init the database
	initDB()
	defer closeDB()
	// init the redis Server
	connectRedis()
	defer closeRedis()

	// Set the router as the default one provided by Gin
	router = gin.Default()

	// Process the templates at the start so that they don't have to be loaded
	// from the disk again. This makes serving HTML pages very fast.
	router.LoadHTMLGlob("templates/*")

	// initialize the routes
	initializeRoutes()

	// Start serving the application
	router.Run(":3000")
}

// Render one of HTML, JSON or CSV based on the 'Accept' header of the request
// If the header doesn't specify this, HTML is rendered, provided that
// the template name is present
func render(c *gin.Context, data gin.H, templateName string) {
	token, _ := c.Cookie("token")

	// 设置html中的is_logged_in
	data["is_logged_in"] = isLoggedInRedis(token)
	// fmt.Println(data["is_logged_in"])

	switch c.Request.Header.Get("Accept") {
	case "application/json":
		// Respond with JSON
		c.JSON(http.StatusOK, data["payload"])
	case "application/xml":
		// Respond with XML
		c.XML(http.StatusOK, data["payload"])
	default:
		// Respond with HTML
		c.HTML(http.StatusOK, templateName, data)
	}
}
```
#### routes.go
```go
// routes.go

package main

import (
	"github.com/gin-gonic/gin"
)

func initializeRoutes() {
	// Handle the index route
	router.GET("/", showIndexPage)

	// Group user related routes together
	userRoutes := router.Group("/")
	{
		// Handle the GET requests at /signin
		// Show the login page
		// Ensure that the user is not logged in by using the middleware
		userRoutes.GET("signin", ensureNotLoggedIn(), showLoginPage)

		// Handle POST requests at /profile
		// Ensure that the user is not logged in by using the middleware
		userRoutes.POST("profile", ensureNotLoggedIn(), performLogin)

		// Handle GET requests at /logout
		// Ensure that the user is logged in by using the middleware
		userRoutes.GET("logout", ensureLoggedIn(), logout)

		// Handle GET request at /profile
		userRoutes.GET("profile", viewProfile)

		// Handle the GET requests at /signup
		// Show the registration page
		// Ensure that the user is not logged in by using the middleware
		userRoutes.GET("signup", ensureNotLoggedIn(), showRegistrationPage)

		// Handle POST requests at /signup
		// Ensure that the user is not logged in by using the middleware
		userRoutes.POST("signup", ensureNotLoggedIn(), register)
	}
}

func showIndexPage(c *gin.Context) {
	// Call the render function with the name of the template to render
	render(c, gin.H{
		"title": "Home Page",
	}, "index.html")
}
```
#### handlers.user.go
```go
// handlers.user.go

package main

import (
	"fmt"
	"math/rand"
	"net/http"
	"strconv"

	"github.com/gin-gonic/gin"
)

func showLoginPage(c *gin.Context) {
	// Call the render function with the name of the template to render
	render(c, gin.H{
		"title": "Login",
	}, "login.html")
}

func performLogin(c *gin.Context) {
	// Obtain the POSTed username and password values
	username := c.PostForm("username")
	password := c.PostForm("password")

	// Check if the username/password combination is valid
	if isUserValid(username, password) {
		// If the username/password is valid set the token in a cookie
		token := generateSessionToken()
		fmt.Println(token)
		c.SetCookie("token", token, 3600, "", "", false, true)
		addInRedis(token, username)
		// redirect to profile page
		c.Redirect(http.StatusMovedPermanently, "/profile")
	} else {
		// If the username/password combination is invalid,
		// show the error message on the login page
		c.HTML(http.StatusBadRequest, "login.html", gin.H{
			"ErrorTitle":   "Login Failed",
			"ErrorMessage": "Invalid credentials provided"})
	}
}

func generateSessionToken() string {
	// We're using a random 16 character string as the session token
	// This is NOT a secure way of generating session tokens
	// DO NOT USE THIS IN PRODUCTION
	return strconv.FormatInt(rand.Int63(), 16)
}

func viewProfile(c *gin.Context) {
	token, _ := c.Cookie("token")
	loggedIn := isLoggedInRedis(token)
	if loggedIn {
		username := getInRedis(token)
		render(c, gin.H{
			"title":   "Successful Login",
			"payload": username}, "logged.html")
	} else {
		c.Redirect(http.StatusTemporaryRedirect, "/signin")
	}
}

func logout(c *gin.Context) {
	token, _ := c.Cookie("token")
	removedInRedis(token)
	// Clear the cookie
	c.SetCookie("token", "", -1, "", "", false, true)

	// Redirect to the home page
	c.Redirect(http.StatusTemporaryRedirect, "/")
}

func showRegistrationPage(c *gin.Context) {
	// Call the render function with the name of the template to render
	render(c, gin.H{
		"title": "Register"}, "register.html")
}

func register(c *gin.Context) {
	// Obtain the POSTed username and password values
	username := c.PostForm("username")
	password := c.PostForm("password")

	if _, err := registerNewUser(username, password); err == nil {
		// If the user is created, set the token in a cookie and log the user in
		token := generateSessionToken()
		c.SetCookie("token", token, 3600, "", "", false, true)
		addInRedis(token, username)
		// redirect to profile page
		c.Redirect(http.StatusMovedPermanently, "/profile")
	} else {
		// If the username/password combination is invalid,
		// show the error message on the login page
		c.HTML(http.StatusBadRequest, "register.html", gin.H{
			"ErrorTitle":   "Registration Failed",
			"ErrorMessage": err.Error()})
	}
}
```
#### models.user.go
```go
// models.user.go

package main

import (
	"errors"
	"regexp"
	"strings"
	"unicode"
)

// Check if the username and password combination is valid
func isUserValid(username, password string) bool {
	hasAcc, passwordInDB := query(username)
	if hasAcc {
		if passwordInDB == password {
			return true
		}
	}
	return false
}

// Register a new user with the given username and password
func registerNewUser(username, password string) (string, error) {
	if strings.TrimSpace(password) == "" {
		return "", errors.New("The password can't be empty")
	} else if !isUsernameAvailable(username) {
		return "", errors.New("The username isn't available")
	}
	//pattern := `\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*` //匹配电子邮箱
	pattern := `^[0-9a-z][_.0-9a-z-]{0,31}@([0-9a-z][0-9a-z-]{0,30}[0-9a-z]\.){1,4}[a-z]{2,4}$`
	reg := regexp.MustCompile(pattern)
	isEmail := reg.MatchString(username)
	// 匹配手机
	regular := "^((13[0-9])|(14[5,7])|(15[0-3,5-9])|(17[0,3,5-8])|(18[0-9])|166|198|199|(147))\\d{8}$"
	reg2 := regexp.MustCompile(regular)
	isMobile := reg2.MatchString(username)
	// 验证用户名
	if (isEmail || isMobile) != true {
		return "", errors.New("Your user name should either be phone number or email address!")
	}
	// 验证密码长度
	if len(password) < 8 {
		return "", errors.New("Your password is too short!")
	}
	// 验证密码是否有大小写
	var hasUpperCase, hasLowercase bool
	for _, c := range password {
		switch {
		case unicode.IsUpper(c):
			hasUpperCase = true
			if hasLowercase {
				break
			}
		case unicode.IsLower(c):
			hasLowercase = true
			if hasUpperCase {
				break
			}
		}
	}
	if (hasLowercase && hasUpperCase) != true {
		return "", errors.New("Your password should contain both upper and lower cases!")
	}

  insert(username, password)

	return username, nil
}

// Check if the supplied username is available
func isUsernameAvailable(username string) bool {
  hasAcc,_ := query(username)
	if hasAcc {
		return false
	}
	return true
}
```
#### middleware.auth.go
```go
// middleware.auth.go

package main

import (
	"net/http"

	"github.com/gin-gonic/gin"
)

// This middleware ensures that a request will be aborted with an error
// if the user is not logged in
func ensureLoggedIn() gin.HandlerFunc {
	return func(c *gin.Context) {
		// If the token is not in redis
		// the user is not logged in
		token, _ := c.Cookie("token")
		loggedIn := isLoggedInRedis(token)
		if !loggedIn {
			//if token, err := c.Cookie("token"); err != nil || token == "" {
			c.AbortWithStatus(http.StatusUnauthorized)
		}
	}
}

// This middleware ensures that a request will be aborted with an error
// if the user is already logged in
func ensureNotLoggedIn() gin.HandlerFunc {
	return func(c *gin.Context) {
		//If the token is in the redis
		// the user is already logged in
		token, _ := c.Cookie("token")
		loggedIn := isLoggedInRedis(token)
		if loggedIn {
			// if token, err := c.Cookie("token"); err == nil || token != "" {
			c.AbortWithStatus(http.StatusUnauthorized)
		}
	}
}
```
#### redis.sh
```bash
#!/bin/sh
redis-server
```
#### createTable.sql
```plsql
DROP TABLE IF EXISTS users;
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    account VARCHAR(50) NOT NULL,
    password VARCHAR(50) NOT NULL
);
```
#### header.html
```html
<!--header.html-->

<!doctype html>
<html>

  <head>
    <!--Use the title variable to set the title of the page-->
    <title>{{ .title }}</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta charset="UTF-8">

    <!--Use bootstrap to make the application look nice-->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
    <script async src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js" integrity="sha384-0mSbJDEHialfmuBBQP6A4Qrprq5OVfW37PRR3j5ELqxss1yVqOtnepnHVP9aJ7xS" crossorigin="anonymous"></script>
  </head>

  <body class="continer">
    <!--Embed the menu.html template at this location-->
    {{ template "menu.html" . }}
```
#### footer.html
```html
<!--footer.html-->

  </body>

</html>
```
#### menu.html
```html
<!--menu.html-->

<nav class="navbar navbar-default">
  <div class="container">
    <div class="navbar-header">
      <a class="navbar-brand" href="/">
        Home
      </a>
    </div>
    <ul class="nav navbar-nav">
      {{ if not .is_logged_in }}
        <!--Display this link only when the user is not logged in-->
        <li><a href="/signin">Profile</a></li>
      {{end}}
      {{ if not .is_logged_in }}
        <!--Display this link only when the user is not logged in-->
        <li><a href="/signup">Register</a></li>
      {{end}}
      {{ if not .is_logged_in }}
        <!--Display this link only when the user is not logged in-->
        <li><a href="/signin">Login</a></li>
      {{end}}
      {{ if .is_logged_in }}
        <!--Display this link only when the user is logged in-->
        <li><a href="/profile">Profile</a></li>
      {{end}}
      {{ if .is_logged_in }}
        <!--Display this link only when the user is logged in-->
        <li><a href="/logout">Logout</a></li>
      {{end}}
    </ul>
  </div>
</nav>
```
#### index.html
```html
<!--index.html-->

<!--Embed the header.html template at this location-->
{{ template "header.html" .}}

  <h1>Hello Gin!</h1>

<!--Embed the footer.html template at this location-->
{{ template "footer.html" .}}
```
#### register.html
```html
<!--register.html-->

<!--Embed the header.html template at this location-->
{{ template "header.html" .}}

<h1>Register</h1>

<div class="panel panel-default col-sm-6">
  <div class="panel-body">
    <!--If there's an error, display the error-->
    {{ if .ErrorTitle}}
    <p class="bg-danger">
      {{.ErrorTitle}}: {{.ErrorMessage}}
    </p>
    {{end}}
    <!--Create a form that POSTs to the `/u/register` route-->
    <form class="form" action="/signup" method="POST">
      <div class="form-group">
        <label for="username">Username</label>
        <input type="text" class="form-control" id="username" name="username" placeholder="Username">
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" name="password" class="form-control" id="password" placeholder="Password">
      </div>
      <button type="submit" class="btn btn-primary">Register</button>
    </form>
  </div>
</div>


<!--Embed the footer.html template at this location-->
{{ template "footer.html" .}}
```
#### login.html
```html
<!--login.html-->

<!--Embed the header.html template at this location-->
{{ template "header.html" .}}

<h1>Login</h1>


<div class="panel panel-default col-sm-6">
  <div class="panel-body">
    <!--If there's an error, display the error-->
    {{ if .ErrorTitle}}
    <p class="bg-danger">
      {{.ErrorTitle}}: {{.ErrorMessage}}
    </p>
    {{end}}
    <!--Create a form that POSTs to the `/u/login` route-->
    <form class="form" action="/profile" method="POST">
      <div class="form-group">
        <label for="username">Username</label>
        <input type="text" class="form-control" id="username" name="username" placeholder="Username">
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" class="form-control" id="password" name="password" placeholder="Password">
      </div>
      <button type="submit" class="btn btn-primary">Login</button>
    </form>
    <br>
    <form action="/signup" method="GET">
    <button type="submit" class="btn btn-primary">Sign up</button>
    </form>
  </div>
</div>


<!--Embed the footer.html template at this location-->
{{ template "footer.html" .}}
```
#### logged.html
```html
<!--index.html-->

<!--Embed the header.html template at this location-->
{{ template "header.html" .}}
  <h1>用户名:{{.payload}}</h1>
  <h1>Login succeeded!</h1>
<!--Embed the footer.html template at this location-->
{{ template "footer.html" .}}
```
