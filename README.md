# ty-re-rx
React, Typescript, and Redux practice project.

Here I'm outlining the whole setup process so that other colleagues might set up their environments in the same way.

#1. PROJECT SETUP
    1.1. Create GitHub repository.

    1.2. Create project folder and suggested subfolders (files will be created in future steps):
            root
                /dev
                    /components
                    /helpers
                    /utils
                    index.tsx
                    style.css
                /dist
                    bundle.tsx
                /node_modules
                .gitignore
                index.html
                package.json
                README.md
                webpack.config.js


#2. NODE
    2.1. Install node.js locally. Files on link: https://nodejs.org/en/

    2.2. Install VS Code extension 'npm' to use npm commands in terminal. Restart VSC.

    2.3. Setup package.json file (package.json file is created):
        * npm init

    2.4. Fill in project information.


#3. REACT
    3.1. Install React and ReactDOM as dependencies. Work projects use versions 0.14.9 so we'll use them too.
        * npm install react@0.14.9 react-dom@0.14.9 --save
    
    3.2. Create simple index.html file with container:
        <div id="mainApp"></div>

    3.3. Create index.jsx file and add:
        import * as React from 'react';
        import * as ReactDom from 'react-dom';
        const root = document.getElementById("mainApp");
        ReactDom.render(
            <header>
                <h1>Typescript, React, and Redux</h1>
            </header>, 
            root
        );


#4. WEBPACK
    4.1. Install Webpack as devDependency. Work projects use version 3.10.0 so we'll use that version.
        * npm install webpack@3.10.0 --save-dev
    
    4.2. Create webpack.config.js file.
    
    4.3. Add entry and output:
        entry: './dev/index.jsx',
        output: {
            filename: './dist/bundle.jsx',
            path: path.resolve(__dirname, 'dist')
        }
    
    4.4. Add module handlers for .jsx files:
        module: {
            rules: [
                { 
                    test: /\.jsx$/, 
                    loader: 'babel-loader', 
                    exclude: /node_modules/, 
                    query: { 
                    cacheDirectory: true, 
                    presets: ['react', 'es2015']
                    } 
                }
            ]
        }

    OPTIONAL:
        * UglifyJS
            1. Install uglify-webpack-plugin 
            2. Require plugin in webpack.config.js: 
                const UglifyJSPlugin = require('uglifyjs-webpack-plugin');
            3. Reference plugin in webpack.config.js:
                plugins: [
                    new UglifyJSPlugin()
                ]


#5. REDUX
    5.1. Install Redux as dependency.
        * npm install redux --save


#6. TYPESCRIPT
    6.1. Install Typescript
    6.2. 
    6.3. Rename index.jsx to index.tsx


#7. GIT
    7.1. Create a .gitignore file
    7.2. Add files and folders to ignore during push
        .vscode/
        node_modules/
        *.txt


#8. VS CODE
    
    * Setup build task & configure as default task (Ctrl + Shift + B):
        1. Open folder in VS Code. 
        2. Tasks > Configure Task > Create tasks.json file from template > Other
        3. You'll get a template file where you're supposed to change object property values to the following:
            "label": "build",
            "type": "shell",
            "command": "webpack"
        4. Tasks > Configure Default Build Task > build
