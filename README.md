# flask-react-app
Flask + ReactJS application template hosted on NGINX

# setting up and configuring nginx

sudo add-apt-repository ppa:nginx/stable            // app latest nginx repo
sudo apt-get install nginx                          // install nginx
sudo service nginx start                            // start nginx server
sudo service nginx stop                             // stop nginx server

sudo apt-get purge nginx nginx-common               // completely remove nginx
sudo apt-get autoremove                             // remove unused dependencies

sudo rm /etc/nginx/sites-enabled/default            // remove default page
sudo xed /etc/nginx/sites-available/example.com     // create demo app

------------------------------------------------------------------------------
example.com:
------------------------------------------------------------------------------

// serve flask app in debug mode

server {
    server {
	    listen 8080;

	    location / {
		    proxy_pass http://127.0.0.1:8000/;
	    }
    }
}


// serve react app

server {
	listen 8080;

    root /var/www/build;             // build folder contains compiled react app
    server_name localhost:8080
    index index.html index.htm;
}

------------------------------------------------------------------------------

# create a symbolic link

sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
sudo service nginx restart


# creating flask app in virtual environment

sudo apt-get install python3-venv                   // install python3 virtual environment
python3 -m venv example_env                         // create virtual environment
source example_env/bin/activate                     // activate virtual environment
deactivate                                          // deactivate venv while in session
pip install flask                                   // install flask
pip install uwsgi                                   // install uWSGI module











