
# go-getting-started

A barebones Go app from the [Getting Started with Go on Heroku](https://devcenter.heroku.com/articles/getting-started-with-go) article - check it out.

- Repo at <https://github.com/heroku/go-getting-started.git>

## Running Locally

Make sure you have [Go](http://golang.org/doc/install) version 1.17 or newer and the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) installed.

In GitHub, fork [the repo](https://github.com/heroku/go-getting-started.git) so you can mess with it. 

Then, in the git clone command below, use your GitHub account (instead of heroku or denisecase).

```PowerShell
git clone https://github.com/denisecase/go-getting-started.git
cd go-getting-started
go build -o bin/go-getting-started -v . # or `go build -o bin/go-getting-started.exe -v .` in git bash
```



Your app should now be running on [localhost:5000](http://localhost:5000/).

## Heroku: Set up Deployment

```PowerShell
heroku login
```

Create a Herokup app. 

Optional - add Heroku Postgres.

- Add database. On the Heroku app dashboard, go to Resources / Add-ons / Heroku Postgres / Hobby Dev - Free.
- Get all in one DATABASE_URL. On the Heroku app dashboard, go to Settings / Config vars / reveal to see DATABASE_URL.
- Get DB vars. On the Heroku app dashboard, go to Resources / Heroku Postgres  / Settings / Database Credentials / View Credentials. Add these to your database.yml.

Configure autodeployment. On the Heroku app dashboard, go to Deploy / Set Deployment Method to GitHub / Set Connect to GitHub to username / repo (e.g., denisecase/) / Enable Automatic Deploys.

Monitor deployment. After deploying / on the app dashboard, go to Overview / click View Build Progress. 

- If successful, click "View App".
- If unsuccessful, click "More" / "View Logs".


## Documentation

For more information about using Go on Heroku, see these Dev Center articles:

- [Go on Heroku](https://devcenter.heroku.com/categories/go)
