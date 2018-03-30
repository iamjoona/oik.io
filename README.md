Based on the work by Phil Hawskworth:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/philhawksworth/linkylinky)


## Configuration

### 1. Environment variables

Before you can start using the URL shortener, you'll need to tell your build script where it can find your data. We'll make use of Netlify's [form handling](https://www.netlify.com/docs/form-handling/) and access the content via the provided [API](https://www.netlify.com/docs/api/#forms).

To do this we'll need to define the following Environment Variables:

- `ROUTES_FORM_ID` : The ID of the form in your Netlify site which contains all of your active routes (Discover this from the URL of your Routes form in your Forms admin page)
- `API_AUTH` : Your netlify API authentication token. This will let your build script access the routes stored in your form programmatically. (Create one at https://app.netlify.com/account/applications)


### 2. Build hooks

In order to add new redirect rules to the Netlify CDN, we'll need to rebuild and deploy the site when we have a new route. This is done by creating a build hook and then calling it whenever a new submission is posted to the Routes form.
