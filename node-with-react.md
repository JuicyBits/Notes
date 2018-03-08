### _Section 2:_ Server Side Architecture
- Use `cat` in terminal to show file contents

- **Node** - JavaScript runtime used to execute code outside of the browser
- **Express** - Library that runs in the Node runtime
  - Has helpers to make dealing with HTTP traffic easier


- `NodeJS` makes use of **CommonJS modules** for importing and sharing JS files, _not_ ES2015 modules:
  `const express = require('express');`
  NOT
  `import express from 'express';`

#### Heroku Deployment Checklist
- Dynamic Port Binding
  - Use port provided by Heroku
- Specify Node Environment
  - Tell Heroku which version of node to use
- Specify start script
  - Tell Heroku what command to run to start server
- Create `.gitignore` file
  - Don't include project dependencies, as Heroku will do that for you

### First Time Heroku Deploy
- Commit codebase to `git`
- Install `Heroku CLI` and `Create App`
- Deploy App with `git`
- Heroku deploys project

### *Section 3:* Authentication with Google OAuth
#### OAuth Flow
**Passport Limitations**
- Automates majority of OAuth flow, but not ALL
  - Requires some tweaking at times

**Passport Library Components**
- Passport
  - General helpers for handling auth in `Express` apps
- Passport Strategy
  - Helpers for authenticating with one very specific method (e.g. email/password, Google, Facebook)
