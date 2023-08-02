# Blogging-platform

#Local Installation

Install Node.js
Install MongoDB
git clone https://github.com/VinaySingh8173/Blogging-platform.git
cd react-redux-blog
npm install
Create a free PostMark account for sending (confirm email, forgot pwd) emails.
Export Postmark credentials to environment
export POSTMARK_API_TOKEN=<getApiTokenFromWInPostmark>
Alternatively, you can run the app on Heroku, add Postmark addon (which adds a free account and sets POSTMARK_API_TOKEN to the app running on Heroku). You can then get that POSTMARK_API_TOKEN by running: heroku config:get POSTMARK_API_TOKEN and then export the token to the terminal. This will now allow you to send email from localhost.
####Preventing Emails From Getting Blocked by GMail, Yahoo etc. NOTE: In order to send email via PostMark or Sendgrid, you need to verify sender's email(from address). In PostMark you can do that by setting your company or other private email(e.g. raja@rao.com) and verifying that. Then you can use THAT company or private email(e.g. raja@rao.com) in the FROM address.

#Running Locally You need two terminal windows open, one for client and the other for server.

####Development

In terminal 1,
export JWT_SECRET=somesecretstring <-- This is used to generate JWT tokens.
export POSTMARK_API_TOKEN=<getApiTokenFromWInPostmark> <-- Email
`export FROM_EMAIL= <-- "From"-Email Address that you verified w/ PostMark
run npm start. This runs the app server (Express).
In terminal 2, run: npm run dev. This runs the development server(webpack-dev-server).
Open browser and go to: localhost:8080
export JWT_SECRET=somesecret
export POSTMARK_API_TOKEN=bla-bla-bla-9619-a6d1185548cd
export FROM_EMAIL=yourcompanyemail@company.com
export NODE_ENV=development
####Note: If you open localhost:3000 in browser, you'll see a "stale" production app, so while in development, always go to localhost:8080

####Production In production, we need to compile the latest client js and place it to public folder. This allows the main app server(Express) to also show the final app.

Generate latest React app: npm run build.
In terminal 1, run npm start. It will be running both the server and the client.
Open browser and go to : localhost:3000.
#Cloning Locally And Pushing To Heroku Running your own instance on Heroku.

git clone https://github.com/VinaySingh8173/Blogging-platform.git
cd react-redux-blog
heroku login (enter heroku credentials)
heroku init
heroku create
heroku addons:create mongolab <-- Add Mongolab test DB (free tier)
heroku addons:create postmark:10k <-- Postmark Email (free tier)
git push heroku master
###Making changes to your app and pushing it to Heroku Everytime you make changes to the front end, you need to build it, and do git commit before pushing it to Heroku test server.

npm run build #build new React app JS
git add . #Add change to git
`git commit -m ""
git push heroku master
heroku open
I usually have something like below that combines all the steps. I just change the commit message everytime.

npm run build && git add . && git commit -m "made changes" && git push heroku master && heroku open
