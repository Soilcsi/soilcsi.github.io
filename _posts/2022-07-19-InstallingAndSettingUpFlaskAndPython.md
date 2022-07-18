---
title: Installing and setting up Flask and Python
date: 2022-07-19 2:39:00 +/+0600
categories: [Writing a Web Scrapper API using Python & Flask]
tags: [Python, Flask, API, BeautifulSoup4, Web Scrapper]
published: true
---

# Installing and setting up Flask and Python
So I published a torrent search type app few days ago. called "Torrentio", do check it out.
The app is written in Flutter but this article is about the backend. The backend API is written in Python using Flask.
The server application uses BeautifulSoup4 to scrape data from various torrent sites like 1337x, tpb, etc. In this article, I aim to describe how I made the API. I will assume you have Python installed and is somewhat familiar with its structure and syntax. Can you write a calc app on your own? you're good, so let's begin.

## Installing Flask & BeautifulSoup4
Open a terminal, or console whatever you got.
```
$ pip install flask beautifulsoup4
```
> try pip3 or python3 -m pip, depends on your system
> Another note you should install Postman or any rest API testing tool you like. I'm gonna use postman throughout this article.

## Hello World with Flask
Fire up your IDE.
```
import flask

app = flask.Flask(__name__)

@app.route("/", methods=['GET'])
def home():
    return "Hello, World!"

if __name__ == '__main__':
    app.run()


```
First, you import flask and initiate an object  **app**.
The next line starting with "@" you're seeing is something called **decorators** in Python. Here are some lines I copied from Google about decorators.

A decorator is **a design pattern in Python that allows a user to add new functionality to an existing object without modifying its structure**. Decorators are usually called before the definition of a function you want to decorate.
You can read [this](https://www.geeksforgeeks.org/decorators-in-python/) article to know more about decorators in Python.

Using this `@app.route("/", methods=['GET'])` you are defining an endpoint of your API. In this case, the endpoint is `/` which is the root. The function we defined in the next line is called when someone enters this route.
If your endpoint was `https://example.com/cat_images` you would
write `@app.route("/cat_images", methods=['GET'])`

Now the second param of this decorator is the list of methods our endpoint will support. There are various HTTP methods like POST, GET, DELETE, UPDATE, etc. In our case, our root endpoint will only support the GET method.

And after this decorator is the function that will be executed when someone accesses this route. well. self-explanatory py code.

Now run it.
You will receive some output like the below.
```
 * Serving Flask app 'article' (lazy loading)
 * Environment: production
[31m   WARNING: This is a development server. Do not use it in a production deployment.[0m
[2m   Use a production WSGI server instead.[0m
 * Debug mode: off
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
```

Visit the URL provided in this case `http://127.0.0.1:5000` and you will be greeted by `Hello, World!`
Well, baby steps. We will get there, eventually.