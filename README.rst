Hello World with Flask
======================

In this tutorial, you will create a web app and deploy it to Pivotal Cloud Foundry. You will use a Flask create the app. You'll first run the app locally, and then deploy it to Cloud Foundry using git.

Prerequisites
-------------

* Create a Pivotal Web Services account (https://account.run.pivotal.io/z/uaa/sign-up)
* Install the Cloud Foundry Command Line Interface (cf CLI) from https://github.com/cloudfoundry/cli#downloads
* Installing git 
* Ensure your Python environment is setup



Step 1: Create a Web App
------------------------

1. Create and load your virtualenv::

	virtualenv --no-site-packages venv 
	source venv/bin/activate


2. Create your application in app.py::

	import os
	from flask import Flask
	app = Flask(__name__)

	@app.route("/")
	def hello():
		return "Hello from Python Flask running on Cloud Foundry!"

	if __name__ == "__main__":
		port = int(os.environ.get("PORT", 5000))
		app.run(host='0.0.0.0', port=port)


Step 2: Test the App Locally
----------------------------
	
1. Run your application locally::

	python app.py
	

2. You should be able to navigate in your browser to `http://localhost:5000' <http://localhost:5000/>`_ to view your hello world application. You'll notice for Flask the one unique portion is to attempt to read the port variable if it exists, this is to enable Heroku to know which port to listen to. 

3. Press `CTRL-C` to stop the process.

You are now ready to deploy this simple Python/Flask web app to Cloud Foundry.


Step 3: Deploy the Web App to Pivotal Cloud Foundry
-----------------------------------------------------

Follow the instructions given on the below URL to push the flask app to Cloud Foundry.

https://pivotal.io/platform/pcf-tutorials/getting-started-with-pivotal-cloud-foundry/introduction


Summary
-------

In this tutorial, you created a web app usign python flask and deployed it to Pivotal Cloud Foundry.
You learned how to push apps to Pivotal Cloud Foundry using `git`.
