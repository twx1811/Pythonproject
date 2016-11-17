# exercise from earlier

from flask import Flask
from flask import render_template
from flask import request


app = Flask("MyApp")

@app.route("/signup", methods=['Post'])
def sign_up():
    form_data = request.form
    name = form_data['name']
    print form_data['email']
    #return "All OK"
    return "Hello {0}!".format(name.title())

@app.route("/")
def hello():
    return render_template("hello.html")

@app.route("/<name>")
def hello_someone(name):
    return "Hello {0}!".format(name.title())
    return render_template("hello.html",name=name.title())

@app.route("/bye/<name>")
def goodbye_someone(name):
    return "Goodbye {0}!".format(name.title())

@app.route("/bye/<name>/<time>")
def goodbye_someone_time(name,time):
    return "Goodbye {0}! Have a good {1}!".format(name.title(),time)


app.run()
