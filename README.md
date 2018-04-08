Using Celery with Flask and RabbitMQ
=======================

This repository is based on https://github.com/miguelgrinberg/flask-celery-example

Redis is replaced by RabbitMQ and some bugs are fixed to keep it up to date.

The application provides two examples of background tasks using Celery:

- Example 1 sends emails asynchronously.
- Example 2 launches one or more asynchronous jobs and shows progress updates in the web page.

Here is a screenshot of this application:

<center><img src="http://blog.miguelgrinberg.com/static/images/flask-celery.png"></center>

Installing and Configure RabbitMQ on Ubuntu 16.04
-----------
Install:

`sudo apt-get install rabbitmq-server`

Configure:

`sudo rabbitmqctl add_user myuser mypassword`
`sudo rabbitmqctl add_vhost myvhost`
`sudo rabbitmqctl set_user_tags myuser mytag`
`sudo rabbitmqctl set_permissions -p myvhost myuser ".*" ".*" ".*"`

To start the server:
`sudo rabbitmq-server`

To stop it:
`sudo rabbitmqctl stop`

Quick Setup
-----------

1. Clone this repository.
2. Create a virtualenv and install the requirements.
3. Open a terminal window and start a local RabbitMQ server.
4. Open the second terminal window. Set two environment variables `MAIL_USERNAME` and `MAIL_PASSWORD` to a valid Gmail account credentials (these will be used to send test emails). Then start a Celery worker: `$celery worker -A app.celery --loglevel=info`.
5. Start the third terminal window for your application: `$python app.py`.
6. Go to `http://localhost:5000/` and enjoy this application!


Reference:
[Using Celery with Flask](http://blog.miguelgrinberg.com/post/using-celery-with-flask).
[Using RabbitMQ]http://docs.celeryproject.org/en/latest/getting-started/brokers/rabbitmq.html
