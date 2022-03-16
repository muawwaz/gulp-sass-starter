# gulp-scss-starter

![License](https://img.shields.io/github/license/andreyalexeich/gulp-scss-starter)
![GitHub stars](https://img.shields.io/github/stars/andreyalexeich/gulp-scss-starter.svg?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/andreyalexeich/gulp-scss-starter.svg?style=social)<br>
<a href="https://qiwi.com/n/ANDREYALEXEICH"><img src="https://img.shields.io/badge/%D0%97%D0%B0%D0%B4%D0%BE%D0%BD%D0%B0%D1%82%D1%8C%20%D0%BD%D0%B0%20%D0%BF%D0%B8%D0%B2%D0%BE-Qiwi-orange?style=for-the-badge&logo=qiwi"></a>


## :fire: Features
* class naming according to [BEM](https://ru.bem.info/)
* used BEM structure
* using [SCSS](https://sass-lang.com/) preprocessor
* uses transpiler [Babel](https://babeljs.io/) to support modern JavaScript (ES6) in browsers
* used by [Webpack](https://webpack.js.org/) to build JavaScript modules
* hard code guide is used
* used to check the code for errors before commit

## :hammer_and_wrench: Installation
* install [NodeJS](https://nodejs.org/en/)
* install globally:
    * [Yarn](https://yarnpkg.com/getting-started): ```npm i -g yarn```
    * [Gulp](https://gulpjs.com/): ```npm i -g gulp```
    * [Bem Tools](https://www.npmjs.com/package/bem-tools-core): ```npm i -g bem-tools-core```
* download the build using [Git](https://git-scm.com/downloads): ```git clone https://github.com/andreyalexeich/gulp-scss-starter.git```
* go to the downloaded build folder: ```cd gulp-scss-starter```
* download required dependencies: ```yarn```
* to get started, enter the command: ```yarn run dev``` (development mode)
* to build the project, enter the command ```yarn run build``` (build mode)

If you did everything correctly, you should have a browser with a local server open. The build mode involves project optimization: image compression, minification of CSS and JS files for uploading to the server.


## :open_file_folder: File structure

```
gulp-scss-starter
├── dist
├── gulp-tasks
├── src
│   ├── blocks
│   ├── fonts
│   ├── img
│   ├── js
│   ├── styles
│   ├── views
│   └── .htaccess
├── gulpfile.babel.js
├── webpack.config.js
├── package.json
├── .yarnrc.yml
├── .babelrc.js
├── .bemrc.js
├── .eslintrc.json
├── .stylelintrc
├── .stylelintignore
└── .gitignore
```

* Folder Root:
    * ```.babelrc.js``` - Babel settings
    * ```.bemrc.js``` - BEM settings
    * ```.eslintrc.json``` - ESLint settings
    * ```.gitignore``` - prevent Git from tracking files
    * ```.stylelintrc``` - Stylelint settings
    * ```.stylelintignore``` - prevent Stylelint from tracking files
    * ```.yarnrc.yml``` - Yarn setting
    * ```gulpfile.babel.js``` - Gulp settings
    * ```webpack.config.js``` - Webpack settings
    * ```package.json``` - list of dependencies
* Folder ```src``` - used during development:
    * BEM blocks: ```src/blocks```
    * fonts: ```src/fonts```
    * images: ```src/img```
    * JS files: ```src/js```
    * site pages: ```src/views/pages```
    * SCSS files: ```src/styles```
    * HTML files: ```src/views```
    * Apache web server configuration file with settings [gzip](https://habr.com/ru/post/221849/) (lossless compression): ```src/.htaccess```
* Folder ```dist``` - folder from which the local development server is launched (when running ```yarn run dev```)
* Folder ```gulp-tasks``` - folder with Gulp-tasks

## :keyboard: Commands
* ```yarn run lint:styles``` - check SCSS files. For VSCode, you need to install [plugin](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint). For webstorm
or PHPStorm needs to enable Stylelint in ```Languages ​​& Frameworks - Style Sheets - Stylelint```
* ```yarn run dev``` - start the server for project development
* ```yarn run build``` - build a project with optimization without starting the server
* ```yarn run build:views``` - build HTML files
* ```yarn run build:styles``` - compile SCSS files
* ```yarn run build:scripts``` - build JS files
* ```yarn run build:images``` - build images
* ```yarn run build:webp``` - convert images to ```.webp``` format
* ```yarn run build:sprites```- build sprites
* ```yarn run build:fonts``` - build fonts
* ```yarn run build:favicons``` - build favicons
* ```yarn run build:gzip``` - build Apache configuration
* ```yarn run bem-m``` - add BEM block
* ```yarn run bem-c``` - add component
* ```yarn run lint:styles --fix``` - fix errors in SCSS files according to Stylelint settings
* ```yarn run lint:scripts``` - check JS files
* ```yarn run lint:scripts --fix``` - fix errors in JS files according to ESLint settings

## :bulb: Suggestions for use
### Component approach to website development
* each BEM block has its own folder inside ```src/blocks/modules```
* the folder of one BEM block contains one HTML file, one SCSS file and one JS file (if the block uses a script)
     * The HTML file of the block is imported into the file ```src/views/index.html``` (or into the necessary file of the page from which the block will be called)
     * Block SCSS file is imported into ```src/blocks/modules/_modules.scss```
     * Block JS file is imported into ```src/js/import/modules.js```

An example of a folder structure with a BEM block:
```
blocks
├── modules
│   ├──header
│   │   ├── header.html
│   │   ├── header.js
│   │   ├── header.scss
```
In order not to manually create the corresponding folder and files, it is enough to write the following commands in the console:
* ```yarn run bem-m my-block``` - to create a BEM block in ```src/block/modules``` (for basic BEM blocks), where ```my-block`` ` - BEM block name;
* ```yarn run bem-with my-component``` - to create a component in ```src/blocks/components``` (for components), where ```my-component``` is the name of the component

### Project pages
* project pages are located in the folder ```src/views/pages```
    * main page: ```src/views/index.html```

### Fonts
* fonts are in ```src/fonts``` folder
    * use [formats](https://caniuse.com/#search=woff) ```.woff``` and ```.woff2```
    * fonts are included in the file ```src/styles/base/_fonts.scss```
    * you can convert local fonts using [this service](https://onlinefontconverter.com/)

### Images
*images are in ```src/img``` folder
    * images are automatically converted to ```.webp``` format. Detailed information on using [here] (https://vk.com/@vk_it-webp)
    * image for generating favicons must be located in ```src/img/favicon``` and have a size of at least ```1024px x 1024px```

### SVG sprites
To create sprites, ```.svg``` images must be in the ```src/img/sprites``` folder. For example, we have files ```icon-1.svg```, ```icon-2.svg``` and ```icon-3.svg```, and we need to refer to ``` icon-2.svg```. To do this, in HTML, you need to use the ```<use>``` tag:
```html

<svg>
    <use xlink:href="img/sprites/sprite.svg#logo"></use>
</svg>
```
Change styles of svg icon from sprite in CSS:
```css
svg use {
     fill: red;
}
```
There is a situation when the icon styles cannot be changed. This is due to the fact that when exporting from Figma, extra code is added to svg. For example:
```html
<svg width="18" height="19" viewBox="0 0 18 19" fill="none" xmlns="http://www.w3.org/2000/svg">
   <path d="M4.90918 4.04542L13.091 9.54088L4.90918 14.9545L4.90918 4.04542Z" fill="#1B1B1D"/>
</svg>
```
You need to remove ```fill="none"``` and ```fill="#1B1B1D"```. It should turn out like this:
```html
<svg width="18" height="19" viewBox="0 0 18 19" xmlns="http://www.w3.org/2000/svg">
   <path d="M4.90918 4.04542L13.091 9.54088L4.90918 14.9545L4.90918 4.04542Z"/>
</svg>
```

### Third party libraries
* all third-party libraries are installed in the ```node_modules``` folder
    * to load them use the command ```yarn add package_name``` (e.g. ```yarn add jquery```)
    * to include JS-files of libraries, import them at the very beginning of the JS-file of the BEM block (that is, the BEM block that the script uses), for example:
    ```javascript
    import $from "jquery";
    ```
    * to include style files of libraries, import them into the file ```src/styles/vendor/_libs.scss```
    * JS-files and style files of libraries cannot be changed independently

## :point_right: Need SCSS + Pug?
Use [this](https://github.com/andreyalexeich/gulp-pug-starter/) build.

## :yellow_heart: Do you like the project?
Report [bugs](https://github.com/andreyalexeich/gulp-scss-starter/issues), put a star in the upper right corner, [donate](https://qiwi.com/n/ANDREYALEXEICH) me for beer :beer:

## :envelope: Contacts
For all questions, write to [Telegram](https://t.me/andreyalexeich)