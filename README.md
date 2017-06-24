# newsapi

A node interface for NewsAPI

[![npm](https://img.shields.io/npm/v/newsapi.svg)](https://www.npmjs.com/package/newsapi)
[![npm](https://img.shields.io/npm/dt/newsapi.svg)](https://www.npmjs.com/package/newsapi)

Up-to-date news headlines and metadata in JSON from 70+ popular news sites. Powered by NewsAPI.org.

You will need an API key from [https://newsapi.org](https://newsapi.org)

Please look at their documentation to see how to use the API

If you use this in a project, add a 'powered by' attribution link back to NewsAPI.org

## Add to your project
```shell
$ npm install newsapi --save
```

## Test
```shell
$ API_KEY=<your api key> npm test
```

## Example usage
```js
let NewsAPI = require('newsapi');

let newsapi = new NewsAPI('YOUR_API_KEY');

// To query articles:
newsapi.articles({
  source: 'associated-press', // required
  sortBy: 'top' // optional
}).then(articlesResponse => {
  console.log(articlesResponse);
  /*
    {
      status: "ok",
      source: "associated-press",
      sortBy: "top",
      articles: [
        ...
      ]
    }
   */
});

// To query sources:
newsapi.sources({
  category: 'technology', // optional
  language: 'en', // optional
  country: 'us' // optional
}).then(sourcesResponse => {
  console.log(sourcesResponse);
  /*
    {
      status: "ok",
      sources: [
        ...
      ]
    }
  */
});

// For both methods you can also use traditional Node callback style:
newsapi.articles({
  source: 'associated-press',
  sortBy: 'top'
}, (err, articlesResponse) => {
  if (err) console.error(err);
  else console.log(articlesResponse);
});
```
