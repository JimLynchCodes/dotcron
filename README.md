# dotcron
Runs scripts in `package.json` on a schedule defined by a `.cron` file.


# dotcron

<img src="https://raw.githubusercontent.com/motdotla/dotenv/master/dotenv.png" alt="dotenv" align="right" />

Dotcron is a zero-dependency module that loads environment variables from a `.env` file into [`process.env`](https://nodejs.org/docs/latest/api/process.html#process_process_env). Storing configuration in the environment separate from code is based on [The Twelve-Factor App](http://12factor.net/config) methodology.

[![BuildStatus](https://img.shields.io/travis/motdotla/dotenv/master.svg?style=flat-square)](https://travis-ci.org/motdotla/dotenv)
[![Build status](https://ci.appveyor.com/api/projects/status/github/motdotla/dotenv?svg=true)](https://ci.appveyor.com/project/motdotla/dotenv/branch/master)
[![NPM version](https://img.shields.io/npm/v/dotenv.svg?style=flat-square)](https://www.npmjs.com/package/dotenv)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/feross/standard)
[![Coverage Status](https://img.shields.io/coveralls/motdotla/dotenv/master.svg?style=flat-square)](https://coveralls.io/github/motdotla/dotenv?branch=coverall-intergration)
[![LICENSE](https://img.shields.io/github/license/motdotla/dotenv.svg)](LICENSE)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

## Install

```bash
# with npm
npm install dotcron

# or with Yarn
yarn add dotcron
```

## Usage

Create a file named `.cron` alongside `package.json` in the root directory of the project. Inside of the file put only one line containing a number or special character for each of the six cron fields.

eg:

.cron
```
10 0/5 * * ? *
```


## Create a Cron Script

In the `package.json` file create a new script named `cron`:
```
 "scripts": {
    "start": "node index.js",
    "test": "jest",
    "cron": "npm start"
  },
```


## Start the Cron Job

This runs the command for "cron" on the specified schedule.
```
npm run cron
```

## Stop the Cron Job

Stop a cron job by adding the `--stop` or `-S` flag.
```
npm run cron --stop
```

## List Scheduled Cron Jobs

List scheduled cron jobs instead of scheduling one by adding the `--list` or `-L` flag.
```
npm run cron --list
```


## Named Cron Configurations
If you want to schedule a given project with multiple different cron expressions, you can use named configurations.

Instead of creating a `.cron` file, add a dot and the name to the file name: `.cron.<name>`. Put one cron expression in each file.

eg: 

.cron.foo
```
10 0/5 * * ? *
```

.cron.foo
```
5 10/1 * * ? *
```

Then in `package.json` scripts section add one command for each cron file with a colon between `cron` and the name.

eg:
```
 "scripts": {
    "start": "node index.js",
    "test": "jest",
    "cron:foo": "npm start",
    "cron:bar": "npm start"
  },
```


### Cron Expression Allowed Fields

| Name          | Required      | Allowed Values  | Allowed Special Characters | 
| :-----------: |:-------------:| :--------------:| :------------------------: |
| Seconds       | Y             |      0-59       |         , - * /            |
| Minutes       | Y             |      0-59       |         , - * /            |
| Hours         | Y             |      0-59       |         , - * /            |
| Day of Month  | Y             |      0-59       |         , - * /            |
| Day of Week   | Y             |      0-59       |         , - * /            |
| Year          | Y             |      0-59       |         , - * /            |



## FAQ

### Do I need to add any JavaScript code to my project for this?

No. 🙂


## Contributing Guide

See [CONTRIBUTING.md](CONTRIBUTING.md)

## Change Log

See [CHANGELOG.md](CHANGELOG.md)

