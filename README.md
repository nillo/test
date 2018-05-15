[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lernajs.io/)
### What is this repository for? ###

### Setup ###
- Make sure you have node 8.x.x install and npm 5.6.x installed on your machine.
- `npm login.


### Development ###
To start creating or modifying code, we have to understand how packages are linked to each other when using [npm link](https://docs.npmjs.com/cli/link).
Also, this repo is set up with [lerna](https://github.com/lerna/lerna), so you also want to know how that works :)
Start linking a package that you want to work on to your main repo that actually uses the package.

Once your package is linked to your repo, run `npm run watch`. This will watch your source directory and transpile everything in it.

#### Test your package in an example ####
To test your changes, we could use the `example` folder; it's an empty RN project, where you could test out the changes you made. Follow the following steps to get started:

1. run `npm run transpile:watch` in the root of your project to transpile the code in the `src` folder to the `lib` folder on the fly
1. Got to your package you want to use, run `npm link` to create a reference to this folder
1. run `cd example` and run `npm i`. Note if this dependency is not published yet, just temporarily remove it from dependencies in `package.json`, as otherwise you will get an error.
1. run `npm link @tp-app/<package>` to create a symlink in you `node_modules`
1. (Optional) [Link your native modules](#link-native-packages-manually)
1. run `npm start` and select your OS.

#### Tests ####
Run `npm run test:dev` to start jest while developing

### Link native packages manually ###
**iOS**

1. Open xcode and rightclick on the "Libraries" folder and select "Add files to <your-project>"
1. Browse to this dependecy in you `node_modules` folder, go to the `ios` folder and select the `.xcodeproj` file 
1. Then select your project in Xcode and go to `Build Phases` and add the `Products/<lib-name>.a` file found in the library you just added to `Link Binaries with Libraries`

**Android**

### Publishing a package ###
Before actually publish your package, it's recommended to publish it locally first, so you could see for yourself if it's working properly.

#### (Optional) Set up your local npm registry environment ####
1. run `npm i -g sinopia` and `npm i -g lerna` if you haven't
1. run `sinopia`. Now you are on your own private npm registry. You are able to publish npm packages locally before actually publish them.

### Publish your package locally OR to the talpa radio NPM registry ####
1. *(optional, since this also triggers when performing `npm publish`)* `npm run prepublish`. If no errors / warnings poping up, you are ready to release!
1. Login to the registry:
  - Locally: `npm login --registry=http://localhost:4873`
  - Private Talpa Radio Registry: `npm login --registry=http://npm.beheer-talparadio.net:4873`
1. Publish your package (where `@app/cookie-consent` is the package you want to publish, obviously)
 - Locally: `npm publish --registry=http://localhost:4873` to publish all the packages. Or run `npm run publish -- --scope=@app/cookie-consent --registry=http://localhost:4873` to publish one package.
 - Private Talpa Radio Registry: `npm publish` to publish all the packages. Or run `npm run publish -- --scope=@app/cookie-consent` to publish one package.
1. Check if the package contains the right version on [http://npm.beheer-talparadio.net:4873](http://npm.beheer-talparadio.net:4873)

### How to use a dependency ###
For documentation purposes, we now reference `<package>` to the package in the /packages folder. This could be `cookie-consent` for example. `<lib-name>` referres to the native module.
 
1. Run `npm i -S @app/<package>`
1. Run `react-native link` to link the libraries, or link them [manually](#link-native-packages-manually)

### Who do I talk to? ###
* Taher Abdel Hadi - Product owner, can guide you to the right person for technical info 
# test
