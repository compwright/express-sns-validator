# express-sns-validator

[![Build Status](https://travis-ci.org/compwright/express-sns-validator.svg?branch=master)](https://travis-ci.org/compwright/express-sns-validator)
[![Dependency Status](https://img.shields.io/david/compwright/express-sns-validator.svg?style=flat-square)](https://david-dm.org/compwright/express-sns-validator)
[![Download Status](https://img.shields.io/npm/dm/express-sns-validator.svg?style=flat-square)](https://www.npmjs.com/package/express-sns-validator)
[![Sponsor on GitHub](https://img.shields.io/static/v1?label=Sponsor&message=❤&logo=GitHub&link=https://github.com/sponsors/compwright)](https://github.com/sponsors/compwright)

ExpressJS middleware for verifying Amazon SNS notifications using [sns-validator](https://www.npmjs.com/package/sns-validator) (no dependency on the AWS SDK).

## Requirements

* NodeJS 10+
* ExpressJS 4+
* body-parser 1.4+

## Installation

```bash
npm install --save express-sns-validator
```

## Usage

Add to the route handler you will use to subscribe to Amazon SNS notifications. If the request does not validate, an HTTP 400 will be returned.

> Note: you need [body-parser](https://npmjs.com/package/body-parser) to parse the JSON body from SNS.

```javascript
const express = require('express')
const bodyParser = require('body-parser')
const snsMiddleware = require('express-sns-validator')

const app = express()

app.use(bodyParser.json()) // required for express-sns-validator to work properly

app.post('/notifications/sns', snsMiddleware(), (req, res) => {
  // do stuff with req.body
});
```

## License

MIT License
