## Very Important Note: 
```
For this project for example we are linting typescript files and html files, 
So it is extremly necessary that you have installed typescript globally in your project 
because when eslint will start as soon as you commit, it will need typescript to compile ts files of your repository.
```

# Angular Project with Eslint

This Angular project has Eslint, prettier, Husky and lint-staged implemented on it such that you won't be able to commit your code until your all stashed changes in commit has passed the lint test.
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.1.4.

## Brief Idea:
Usually Eslinnt prettier husky are all basic things that you need to make your project such that it will restrict commmits for failed lint tests. 
But, it depends on what framework or library you're using for your project (Example:- React/Angular/Vue), and this will decide what further dependencies you'll need to install on your project. 

This repo is completely for implementing linting on Angular Project.

## Steps to follow:

1) Install eslint as dev dependency on your angular project.

    1) `npm install --save-dev eslint`


2) Configure eslint by running. 

    1) `npx eslint --init`

    + Select *To check syntax, find problems, and enforce code style* for the question **how would you like Eslint to be used?**

    + Select *Standard* as option for question **which style guide you want to follow?**

    + Select *JSON format* when asked about **which format do you want your config files to be in?**


3) This will create an **.eslintrc.json** file with the content including the configurations for our rules.

    ```
    Copy the code from the .eslintrc.json file available in this repository and paste it inside you .eslintrc.json file
    ````


4) Create **.eslintignore** file in your project to ignore the config on the folders you want to avoid. (check that file in this repository)


5) Install prettier 

    `npm install --save-dev prettier`


6) create **.prettierrc.json** and **.prettierignore** and files in your repo and add following content respectively:

      ```
      {
          "bracketSpacing": true,
          "semi": true,
          "singleQuote": true,
          "trailingComma": "all",
          "printWidth": 80,
          "tabWidth": 2
        }
      ```

      ```
      #you can copy paste your .gitignore file code here
      ```


7) Add following in scripts section of **package.json**

    ```
    "scripts": {
      "lint": "ng lint"
    }
    ```

    + install all dependencies that are required to run this command, your devdependency in package.json will contain some packages like below mentioned. (some         may vary, so do check the version compatibility)

    ```
        "devDependencies": {
          ...
          "eslint": "^8.40.0",
          "@angular-eslint/schematics": "16.0.3",
          "@typescript-eslint/eslint-plugin": "5.59.7",
          "@angular-eslint/builder": "16.0.3",
          "@angular-eslint/eslint-plugin": "16.0.3",
          "@angular-eslint/eslint-plugin-template": "16.0.3",
          "@angular-eslint/template-parser": "16.0.3",
          "@typescript-eslint/parser": "5.59.7",
          ...
        }
    ```


8) Check the eslint rules implementation by running

    1) ` npx eslint .` or `npm run lint`


9) Install husky and lint-staged

    1) `npm install --save-dev husky`

    2) `npm install --save-dev lint-staged`


10) Add below code in **package.json**
    ```
    "scripts": {
       ...
       "execute-husky": "npx husky install && npx husky add .husky/pre-commit \"npx lint-staged\""   
       ... 
    },
    "lint-staged": {
      "src/**/*.{ts,html}": "eslint ."
    },
    "husky": {
      "hooks": {
        "pre-commit": "lint-staged"
      }
    }
    ```

11) Run the command 

    ` npm run execute-husky`



# You are all Set! :tada:

