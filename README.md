# exercise-sass
This is example of project using only HTML &amp; CSS. Project was tested in Chrome browser. It's not very responsive.

Goal of project is to let you exercise with Sass - how to install it, and how to use its features, such as modules, variables, etc.

## Start
1. get repository to your computer (`git clone` or download .zip and unzip folder)
2. open `index.html` in your browser (preferably Chrome), you should see following webpage: 
![ezgif-7-2f8855fd5748](https://user-images.githubusercontent.com/528887/108637198-4e249680-7492-11eb-98e2-10e89db37225.gif)

## Prepare project to work with Sass

* Have text editor or IDE installed (I use [Atom](https://atom.io/))
* Have terminal (I use [iTerm2](https://iterm2.com/) for Mac)

### Prepare folder structure
1. In project's directory, create a folder named `sass`.
2. In `sass` folder create file named `main.scss`.
3. Copy content of `css/styles.css` file fully into `sass/main.scss` file with help of code editor.
4. Delete contents of `css/styles.css`.

### Install Sass
1. Install node.js - it's needed to compile Sass via the command line. Download it from the official website [https://nodejs.org/en/download/](nodejs.org) - choose "LTS" tab, and then click on your operating systen. After it downloaded, follow the wizard. 
2. Via terminal, navigate to project folder on your computer.
3. Write command `npm init` and press Enter. This will initialize NPM - the Node Package Manager for JavaScript. NPM makes it easy to add and remove code packages to your project. 
4. In terminal, you will be prompted to answer several questions about the project, press Enter each time, this will make npm proceed with default setup. After setup NPM will generate a `package.json` file in project folder.
5. In terminal, write command `npm install sass` and press Enter. This will install Sass preprocessor package to the project. 

### Use command 
1. Open the `package.json` file in a code editor.
2. In the `scripts` section, put `,` in the end of line of test command.
3. Add Sass command on the next line: `"sass": "sass sass/main.scss css/styles.css --watch"` (this is [how it should looks like](https://github.com/alynioke/exercise-sass-ready/blob/main/package.json#L8)). The watch flag (`--watch`) tells Sass to watch the `main.scss` file in the `sass` directory for changes and output them in `styles.css` in the `css` directory.
4. In the terminal write `npm run sass` - it will use command you just created in `package.json` and will watch for all changes inside `sass/main.scss`.
5. Open`sass/main.scss` in code editor and save this file - in terminal you should green message confirming that code is saved:
![image](https://user-images.githubusercontent.com/528887/108642539-728e6c00-74ae-11eb-963a-1bd54c45bb1b.png)


## Sass exercises
Important: if after some step something doesn't work, try stopping the sass command (by pressing `cmd + c` or `ctrl + c`) and running it again. 

#### Modules 
* Distribute contents of `main.scss` into 4 other files: for footer, header, intro, recipes. 
* Include those files into `main.scss` using `@use` command. 
* Now your code is more readable and has clear separation of concerns!

#### Variables
* Create `variables.scss` file inside `sass` folder. 
* Include `variables.scss` into each of your other files by writing `@import 'variables';` on top of file ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/footer.scss#L1))
* Find common values inside CSS and define variables for each of them inside that file. Now put variable names instead of actual values in each file ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/recipes.scss#L12)
* Values I suggest to substitute with variables: colors, font sizes, logo size and logo font, value of media query.
* Now your code is more manageable and you control all values easier!

#### Nesting
If you have CSS selector combined from 2 classes, it means you can put one class into another by nesting. Do this where you see 2 classes combined. Same could be done for [media query](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/header.scss#L9) and [for pseudo classes](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/header.scss#L21) like `:hover` or `:last-of-type` (which uses special `&` character from sass for concatenation)
* After doing this, now your code is easier to write! Because you don't need to prefix your classes each time with other classes, you can nest them.

#### Extend
In many places in various sass files there is some repeated code. This repeated code answers for centering elements in CSS. It has 3 rules: 
 ```
display: flex;
align-items: center;
justify-content: center;
```
Let's shorten this. 
* Create new file in `sass` folder called `helpers.scss`. 
* Include `helpers.scss` into each of your other files by writing `@import 'helpers';` on top of file ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/recipes.scss#L2))
* Define class there which will answer for centering state which will combine inside those 3 rules. This class will start with `%` symbol, not with dot ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/helpers.scss#L2))
* Use this class to substitute abovementioned rules in each place they appear with `@extend` ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/intro.scss#L5))
* Now there is less code and no repetitions! And code is easier to manage, because if we need to change centering we can do so from 1 place!

#### Operators
* In `footer.scss` create 2 variables: one answering for margin top on mobile, another answering for margin top on desktop ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/footer.scss#L2))
* Substitute martin top values in CSS for variables. 
* Now, define margin bottom for mobile and desktop, as a half of top margin, by using Sass `/` division feature ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/footer.scss#L9))
* Now, values will always be recalculated automatically, we don't need to adjust it manually!

#### Mixins
* in `helpers.scss` define new mixin which will answer for setting width and height of the element based on passed parameter ([example](https://github.com/alynioke/exercise-sass-ready/commit/bd94eda132756ecdae40700227266661f0624007#diff-6b35906a2d871acb71bae44d81be370207a70484f8cc646eede944634b36b0a7R8))
* for recipe image for mobile and desktop Media Query use 1 line mixin to define square dimensions instead of width and height ([example](https://github.com/alynioke/exercise-sass-ready/blob/main/sass/recipes.scss#L35)) 
* Mixins allow you to define styles that can be re-used throughout your stylesheet!
  
