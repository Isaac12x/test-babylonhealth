# URL shortener/shrinker

Shorten your urls like never before :)

## How to run it

First and foremost, please do clone the repo with
`git clone git@github.com:Isaac12x/test-babylonhealth.git && cd app`

Once you're in there, you should do the following:

`docker build -t urlshortener . && docker run -p 38080:80 urlshortener`

If that doesn't work for you, please use sudo (and later fix your docker installation).

Now you should be good to go. If still you can't start the app because it has some sort of error please do send me an email at ialbetsram@gmail.com with the error trace from your command line (pipe it into a file with `> file.txt`) and your system specs (if you're using linux/UNIX send me the output of `uname -v` and `cat /proc/version` and your docker version `docker -v`).

### Notes

Since I wanted this to be more challenging I used flask (with its limitations - Werkzeug dev is not optimized to serve in productions) and then containerized the app and added a nginx to handle incoming traffic (your 1000 req/s) and then uWSGI to interface with nginx as the request server and pass that into the app layer which is done in Flask.

A good way to optimize this app would be to use a production database. To keep things `simple` enough I've decided to use SQLite but of course if we were to put this in production, this should be a fastDB.

Also, I have created a routes and an app instead of a single file app because if it needs to be scalable, means is working and that means we might be interested in extending the functionality. Doing it now, is trivial. Doing it at a later date can be cumbersome (doesn't need to be but can be).

This is going to be hosted on heroku which gives you very long urls, if it was to be used I would buy a 3-4 letter domain name and use that as the base url.