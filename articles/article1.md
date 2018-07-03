# Service Worker at your service

Progressive Web Apps bring a lot of potential to the web. The new possibilities make it possible to build native web apps that integrate closer with people’s devices.

## Service Workers
It took a bit of a time for Service Workers to fit in. It’s not like any other technology we’ve had on the web, until now.

They’re a part of the web-app, yet they’re not able to touch the DOM in any way. Service Workers are a proxy that live between the web-app and the user. They work in a separate thread and can cache assets, hook into requests, and communicate with the website trough messages.

Service Workers are installed on the user browser after the page has loaded for the first time. After the first install event, the worker can start interfering with requests using the fetch event. When a new version of the Service Worker is deployed, the browser will automatically detect byte differences and activate the worker version on next visit.

## Lighthouse

There are a lot of quality checks to do when building PWAs, here are some of them:

- App can load on offline/slow connections and page load performance is fast
- App is built using Progressive Enhancement principles
- App is using HTTPS for secure communications
- Users will be prompted to Add to Home screen
- Installed web app will launch with Custom Splash Screen and address bar will match brand colours
- To confirm the above requirements are met, a tool called Lighthouse is the golden standard. Lighthouse is a Chrome extension that will analyze any site for Progressive Web App best practices. It shouldn’t be taken as gospel (even though we did), but it’s super helpful.
