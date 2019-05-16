# Betterdep Forum
A forum application for the Betterdep site built with the following technologies:
* [React](https://facebook.github.io/react/)
* [Redux](http://redux.js.org/)
* [Webpack](https://webpack.js.org/)
* [ExpressJS](https://expressjs.com/)
* [PassportJS](http://passportjs.org/)
* [MongoDB](https://www.mongodb.com/)

### Application Features
* Users can post a discussion
* Users can reply their opinions regarding discussion
* Users can favorite discussions
* Users have their own profile page
* Admin can create new forum categories
* The first user created will be the admin

## How to deploy a local server

The following software is required to run the server locally:
* Node.js > 6.0
* NPM / Yarn
* Git
* MongoDB

First, install the necessary dependencies using either NPM or Yarn:
```
$ npm i
```
```
$ yarn
```

This app currently uses GitHub authentication, we you must configure GitHub OAuth application. You can register a new application from this link https://github.com/settings/developers

We need to grab the following information from the OAuth application.
* Client ID
* Client Secret
* Callback URL

The `Callback URL` is the domain where GitHub will redirect the user after a successful login. You can use a domain name or local host. But we need to append the URL with the path `/api/user/authViaGitHub/callback`. So, the complete url will look like:
`https://localhost:8080/api/user/authViaGitHub/callback`

Next, credentials must be configured in the `config/credentials.js` file, which should be empty like this right now:
```js
module.exports = {
  GITHUB_CLIENT_ID: '',
  GITHUB_CLIENT_SECRET: '',
  GITHUB_CALLBACK_URL: '',
  DBURL: '',
};
```

Add your local database that you are currently running. Our team used MongoDB, so our DBURL looked like this:
```
mongodb://localhost:27017/reforum
```

Now we are ready to run the application. You can run either run the development environment of the application which will include Hot-Reload for JS codes using Webpack and the Redux dev tool extension, or you can run the production edition. The default port for developer edition is `8080`, and for production is `process.env.PORT`.

To run the app in development environment:
```
$ npm run start:dev
```

To run the app in production environment:
```
$ npm run start
```

Now, if you visit [http://localhost:8080](http://localhost:8080) (if you ran the dev), or the production URL, you will see that the application is up and running. It will first show you a `Sorry, couldn't find the forum` message. This message is displayed when no forums have been created yet, so we can now create forums as an admin. Sign up via github and visit the admin panel [http://localhost:8080/admin](http://localhost:8080/admin) to begin adding forums. As mentioned previously, this website is configured so that the first user will automatically become that admin.

## License
[MIT License](https://github.com/shoumma/Mister-Poster/blob/master/LICENSE).