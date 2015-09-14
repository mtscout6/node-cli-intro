# Node CLI Tool Introduction

Tools like Make, Gulp, Grunt, Rake, etc. are great for scripting many of the tedious tasks we do as
developers on a daily basis. However, they can be heavy handed and ceremonious for many things you
will actually need on some projects.  When you do find the need to break out a new CLI tool
JavaScript is a powerful language to use to make that happen. Since JavaScript has quickly become a
must have language for most developers to learn, it's likely that developers from many different
technology stacks will be able to jump in and contribute. With that said though JavaScript in its
ES5 form today can itself be rather ceremonious and a barrier to adoption.

Since many of you are new to working with NodeJS this is a sample project aimed to assist you in
learning how to setup a NodeJS project. It will also push you a step further to use test driven
development, next generation JavaScript like [ES2015](https://babeljs.io/docs/learn-es2015/), and
developer tools like ESLint that assist your efforts to produce a clean code base.

## Project Goals

- __OS Agnostic__ - CLI tools should work on any OS.
- __ES2015 -> Next Gen JavaScript__ - Using tools like [Babel](http://babeljs.io/) to write your
    scripts and deploy compiled scripts.
- __Asyncronous__ - Non-blocking disk IO and network requests, or potential process forking.
- __Extensibility__ - The CLI tool code should also double as a node module library, whenever
    possible.
- __Testable__ - Test coverage is a first class citizen to developing your CLI tool.
- __Documentation__ - Enable others to use what you wrote

## The Project

Releasing projects usually tends to be a multi-stage process. Generally this includes a version
change, code release, and documentation updates. This project will be a general cli tool solution
that can do this against any NodeJS based project hosted on GitHub. The release process should:

- Version Bump following [SemVer](http://semver.org/) guidelines
  - Modifies the package.json file's version field
  - Commits the changed file to source control
- Build the src
  - Remove old compiled code to ensure nothing old sticks around
- Git tag the src repo, and push the tags to the remote origin repo
- Document the release using the [GitHub release
    api](https://developer.github.com/v3/repos/releases/)

### Resources to consider

- [npm](https://docs.npmjs.com/)
  - [npm scripts](https://docs.npmjs.com/misc/scripts)
  - [package.json](https://docs.npmjs.com/files/package.json)
- [Babel](http://babeljs.io/)
- Command line parsers
  - [yargs](https://www.npmjs.com/package/yargs)
  - [commander](https://www.npmjs.com/package/commander)
- [Mocha](http://mochajs.org/)
- [Chai](http://chaijs.com/)
- [chai-as-promised](https://www.npmjs.com/package/chai-as-promised)
- [fs](https://nodejs.org/api/fs.html)
- [fs-promise](https://www.npmjs.com/package/fs-promise)
- [child-process-promise](https://www.npmjs.com/package/child-process-promise)
- [path](https://nodejs.org/api/path.html)
- [rimraf](https://www.npmjs.com/package/rimraf)
- [mkdirp](https://www.npmjs.com/package/mkdirp)
- [gh-release](https://www.npmjs.com/package/gh-release)
- [shell scripting node](http://shapeshed.com/command-line-utilities-with-nodejs/)
- [EditorConfig](http://editorconfig.org/)
- [ESLint](http://eslint.org/)

### Suggested project layout

```
/path/to/project
├─┬ bin
│ └── (shell scripts that invoke modules in lib, there should not be too much code here)
├─┬ lib (ignored from source control)
│ └── (compiled js files)
├─┬ node_modules (ignored from source control)
│ └── (npm dependencies install here by default)
├─┬ src
│ └── (source es6 js files)
├─┬ test
│ ├── mocha.opts (if you are using mocha)
│ └── (unit tests)
├── .eslintrc
├── .editorconfig
├── .gitignore
├── package.json
└── README.md
```

## Suggested approach to solving this problem

1. Setup your build process
  - In statically typed languages before you do anything you need to be able to build your
      application, or it will not work. In JavaScript this can be deceiving since it's a scripting
      language and it generally works just by loading it in a browser or by executing it with Node.
      Since this project will use Babel to "compile" your JavaScript from ES2015 to ES5 standards
      there will be a build component.
  - A useful tool to use is ESLint as it does static code analysis to highlight issues with
      your code before you run it. There are many editor integrations that work well with ESLint,
      set this up so your can get better code editor support.
  - Since developers work in many different environments EditorConfig is a great tool that
      integrates with most editors that ensures that you are writing the same file format as your
      peers.
2. Setup your test process
  - In order to develop your tool with a TDD style, you'll need your test framework setup. Set it up
      with Mocha, Chai, and Chai-as-promised (This last one is for making assertions in your
      asynchronous code)
3. Setup your continuous integration process
  - This isn't required, but useful. [Travis CI](https://travis-ci.org/) is a free service for
      running your tests whenever you commit and push your code to GitHub. 
4. Build your tool
  - Using TDD build your tool to meet the above mentioned requirements.
