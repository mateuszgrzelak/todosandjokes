# TodosAndJokes

Project of website that allow# TodosAndJokes

Project of website that allows, after logging in, add todos and read jokes. The whole project has been devided into 2 parts: frontend (todosandjokes-client) and backend (todosandjokes-server). The main purpose of creating this application is to show programming skills and ability to separate visual layer from business logic.

## Test Account

`username: username`

`password: password`

It may take some time before page loads and you log in, because applications hosted on heroku after some time 'go sleep' and first request sent to app wakes it up, which may take some time.

## Description

Project was written using 2 programming languages: java and typescript. Backend uses Spring framework, frontend uses Angular 9. All jokes are taken from [Joke API](https://official-joke-api.appspot.com/random_ten).

### Backend

Server is responsible for creating accounts, user authentication, authorization via JWT and returning specific data. All accounts are stored in [PostgreSQL](https://www.postgresql.org/). Passwords are encrypted using [brcypt](https://en.wikipedia.org/wiki/Bcrypt). JWT payload consists of: username, expriration date and email. To check that the JWT attached to request is valid, a new filter has been created that checks if token is not forged and his expiration date is up to date. In database, relation beetwen entities 'UserAccount' and 'Todo' is one to many, which means that one account can be associated with many Todo. Email validation is done using the newly created annotation that uses regexp.

CI/CD performed by GitHub Actions was used to deploy application on heroku. Code responsible for that is placed in folder [.github/workflows](https://github.com/mateuszgrzelak/todosandjokes-server/blob/master/.github/workflows/maven.yml). All commits sent to branch master cause testing and building app and if all tests pass, then application is deployed on Heroku using heroku-maven-plugin which requires attached environment variable named HEROKU_API_KEY to succesful send project. Package caching was also used to improve performance of building app.

### Frontend

@Angular/animations dependency was used to animate page transitions. Code responsible for that is placed in file [animations.ts](https://github.com/mateuszgrzelak/todosandjokes-client/blob/master/src/app/animations.ts). @auth0/angular-jwt is responsible for attaching JWT to each request sent to the server whose domain name is placed in 'whitelistedDomains' in configuration. To show the page loading sign, a loader-inreceptor.service.ts was created, which is responsible for showing and hiding spinner which inform if request is being processed. Progress spinner was taken from [Angular Material](https://material.angular.io/). Moving background elements were downloaded from [angular-particle](https://www.npmjs.com/package/angular-particle-updated).

## Build And Run

All steps required to build and run application are listed in submodules. 

## Website appearance

<p align="center"> 
<img src="https://github.com/mateuszgrzelak/todosandjokes/blob/master/github_img/login.gif">
</p>

<p align="center"> 
<img src="https://github.com/mateuszgrzelak/todosandjokes/blob/master/github_img/content.gif">
</p>

<p align="center"> 
<img src="https://github.com/mateuszgrzelak/todosandjokes/blob/master/github_img/todosList.png">
</p>

<p align="center"> 
<img src="https://github.com/mateuszgrzelak/todosandjokes/blob/master/github_img/jokesList.png">
</p>
