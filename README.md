
# go-getting-started

A barebones Go app from the [Getting Started with Go on Heroku](https://devcenter.heroku.com/articles/getting-started-with-go) article - check it out.

- Repo at <https://github.com/heroku/go-getting-started.git>

On Windows, we'll need WSL, Docker, Golang, Git, and Heroku. Be patient. This might take a while. 

-----

## Preparation - WSL

Install Windows Subsystem for Linux (WSL) <https://docs.microsoft.com/en-us/windows/wsl/install>

```PowerShell
wsl --install
```

Then restart your machine. If you  need a distribution, open PS as Admin and run

```PowerShell
wsl --install -d Ubuntu
```

It may take a while to download and install. 
Then, the Ubuntu (a popular Linux distribution) window will open. 
It will continue installing for a while. 

- Finally, it will ask for a username (e.g. denise).
- Then, it will ask for a password for that user. 
- Confirm the password when prompted.
- It will prompt you to run `sudo apt update`. Go ahead and do so. 
- When it finishes, exit the terminal with CTRL D ("done").
- Back in PS, verify WSL installation with `wsl -l -v`.

## Install Packages with Chocolatey

```PowerShell
choco install golang -y
choco install heroku-cli -y
choco install vscode -y
choco install git -y
choco install docker-desktop -y
choco install docker-toolbox -y
refreshenv
choco list --local
 ```

 The following are helpful to debug any errors. 

 ```PowerShell
 & 'C:\Program Files\Docker\Docker\DockerCli.exe' -SwitchDaemon
 & "C:\Program Files\Docker\Docker\resources\com.docker.diagnose.exe" check
 ```

## Login To Docker

Login with your Docker ID to push and pull images from Docker Hub. 
If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Choose a Docker username, enter email, chose a password. 
Verify your email. 

```PowerShell
docker login
```

Enter your Docker username and password. Test by running a sample Docker app.

```PowerShell
docker run -d -p 80:80 docker/getting-started
```

Run Docker Desktop as Admin. Verify the container is running. 
Use the controls to stop the container. 


## Running Locally

Use the Windows start key to start Docker Desktop / Run as Administrator. 

In GitHub, fork [the repo](https://github.com/heroku/go-getting-started.git) so you can mess with it. 

Then, in the git clone command below, use your GitHub account (instead of heroku or denisecase).

```PowerShell
git clone https://github.com/denisecase/go-getting-started.git
cd go-getting-started
# go build -o bin/go-getting-started -v . 
# or `go build -o bin/go-getting-started.exe -v .` in git bash
go build -o bin/go-getting-started.exe -v
```

On Windows you will need to do two things before being able to run `heroku local`:
Run `go build -o bin/go-getting-started.exe -v` instead of the command listed above.
Alter Procfile so it’s contents are: `web: bin\go-getting-started.exe` instead of what is in the checkout. 
Note the .exe at the end - and the backslash instead of forward slash.
Don’t commit changes to Procfile though, otherwise your application’s web process won’t be able to start on Heroku.

- Now run `heroku local`.
- Click "allow access" to cotinuue. 
- Open brower to [localhost:5000](http://localhost:5000/).

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
