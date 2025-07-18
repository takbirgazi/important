# Important Code for daily use

## Git Commands

* Check Git Configuration:
``` git config --list ```
* Add user name:
``` git config --global user.name "your user name" ```
* Add user email:
``` git config --global user.email "yourname@email.com" ```
* Set a default branch to main:
``` git config --global init.defaultBranch main ```
* Add:
``` git add . ```
* Commit:
``` git commit -m "Messages" ```
* Push First Time To Main Branch:
   ``` git push -u origin main ```
   Next Time:
   ``` git push ```
* Remove The Last Commit
``` git reset --soft HEAD~1 ```
* Pull Existing Project
``` git pull ```
* Pull from Other Branch
``` git pull origin branchname ```
* Check Remote Repository
``` git remote -v ```
* Add Remote Repository
```git remote add origin https://github.com/username/repository_name.git```
* Change Remote Repository
``` git remote set-url origin https://github.com/username/new_repository_name.git ```
* Remove Remote Repository
```git remote remove origin```
* Push Forcefully Existing Branch like main
``` git push -f -u origin main ```
* Check Origin 
``` git remote show origin ```
* Clone with default branch
``` git clone https://github.com/username/repository_name.git ```
* Clone with specific branch
``` git clone -b branchname https://github.com/username/repository_name.git ```
* Switch an existing branch
``` git checkout branchname ```
* Create and Switch a new branch with the current branch code
``` git checkout -b newbranchname ```
* Check branch
``` git branch ```
* Delete a branch
``` git branch -d branchname ```
* Branch Merging
``` git merge branchname ```
* Remove .env from git
``` git rm --cached --ignore-unmatch .env ```

*Find your password to pull your private repository*
* Log In to Your GitHub Account
* Go to Profile And Click Settings
* Click Developer settings
* Select Tokens (classic) at Personal access tokens
* Select Generate new token (classic) at Generate new token
* Check All And Click the Generate token Button.
* Copy The Token. That is your Password.


## React JS

**React.js Install Use [Vite](https://vitejs.dev/guide/)**

```js
// npm 7+, extra double-dash is needed:
npm create vite@latest my-react-app -- --template react

// yarn
yarn create vite my-react-app --template react

// pnpm
pnpm create vite my-react-app --template react

// bun
bun create vite my-react-app --template react
```
**React-router URLs don't work when refreshing or writing manually**
```js
// Use this code when hosting it cPannel Home Folder
// Create .htaccess file and paste it

<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-l
  RewriteRule . /index.html [L]
</IfModule>
```
```js
// Use this code when hosting it cPannel Sub Folder
// Create .htaccess file and paste it

 Options -MultiViews
        RewriteEngine On
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^ index.html [QSA,L]
```

## Express Server

**Install**

```js
// npm Initialize 
npm init
```
```js
// Install Express, CORS, dotenv, MongoDB
npm install express cors dotenv mongodb
```
**Express Setup**

```js
const express = require('express');
const app = express();
require('dotenv').config();
const cors = require('cors');
const { MongoClient, ServerApiVersion, ObjectId } = require('mongodb');
const port = process.env.PORT || 5000;
app.use(express.json());
app.use(cors());

// Use app.use(cors()) OR ⤵️

// app.use(cors({
//     origin: ["http://localhost:5173", "https://assignment-10-5fcf9.web.app"]
//   }))

// app.use((req, res, next) => {
//   res.setHeader("Access-Control-Allow-Origin", "https://assignment-10-5fcf9.web.app");
//   res.header(
//     "Access-Control-Allow-Headers",
//     "Origin, X-Requested-With, Content-Type, Accept"
//   );
//   next();
// });
```
**Express Server Deployment steps**

1. comment await commands outside api methods for solving gateway timeout error

```js
// Comment following commands

await client.connect();
await client.db("admin").command({ ping: 1 });
```

2. create vercel.json file for configuring server

```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "index.js",
      "methods": ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"]
    }
  ]
}
```

3. Add Your production domains to your cors configuration. Don't use the URL we have provided inside origin. Replace them with your own. 

```js
// Must remove "/" from your production URL ➡️ http://localhost:5173/

app.use(
  cors({
    origin: [
      "http://localhost:5173",
      "https://cardoctor-bd.web.app",
      "https://cardoctor-bd.firebaseapp.com",
    ]
  })
);
```

4. Deploy to Vercel

```bash
vercel
vercel --prod
```
- After completed the deployment . click on inspect link and copy the production domain
- setup your environment variables in vercel
- check your public API


<img src="assets/images/code.jpg"/>

**Server Deployment Done**
**If you are using a cookie, follow this extra process. We recommend using local storage to store tokens on the client side to avoid deployment issues.**
1. Let's create cookie options for both the production and local server

```js
const cookieOptions = {
  httpOnly: true,
  secure: process.env.NODE_ENV === "production",
  sameSite: process.env.NODE_ENV === "production" ? "none" : "strict",
};

// localhost:5000 and localhost:5173 are treated as same site.  so sameSite value must be strict in the development server.  in production, sameSite will be none
// in development server secure will false.  in production secure will be true
```

**now we can use this object for the cookie option to modify cookies**

```js
//Creating Token

app.post("/jwt", logger, async (req, res) => {
  const user = req.body;
  console.log("user for token", user);
  const token = jwt.sign(user, process.env.ACCESS_TOKEN_SECRET);

  res.cookie("token", token, cookieOptions).send({ success: true });
});

//Clearing Token

app.post("/logout", async (req, res) => {
  const user = req.body;
  console.log("logging out", user);
  res
    .clearCookie("token", { ...cookieOptions, maxAge: 0 })
    .send({ success: true });
});
```
 
