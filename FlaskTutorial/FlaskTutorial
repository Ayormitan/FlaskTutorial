from flask import Flask, redirect, url_for, render_template, request, session, flash

#Import flask from library

app = Flask(__name__)
app.secret_key = "Ayoo"
#The instance of the flask class created
#Created/defined a home route
@app.route("/")
def home():
	return render_template ("index.html")

#Another route can be the second page
@app.route("/Signup", methods=["POST", "GET"])
def Signup():
	if request.method == "POST":
		name = request.form["name"]
		username = request.form["username"]
		password = request.form["password"]
		session["user"] = username
		return redirect(url_for("user"))
	else:
		return render_template("Signup.html")
@app.route("/user")
def user():
	if "user" in session:
		user = session["user"]
		flash("you successfully login")
		return render_template("user.html")
	else:
		return redirect(url_for("/Signup"))

@app.route("/logout")
def logout():
	session.pop("user", None)
	flash("you successfully logout")
	return redirect(url_for("Signup"))

@app.route("/google")
def google():
	return redirect("https://www.google.com")

#checks if the instance of the file created is being run directly/ if its the main page debug and run on port 8080
if __name__ == "__main__":	
	app.run(debug=True, port=8080)
