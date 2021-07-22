## 🚅 Easygo Storybook Quick Start

1.  **Clone the application.**

    ```shell
    # Clone the repo
    git clone git@github.com:thmsmtylr/easygo.git
    ```

1.  **Install the dependencies.**

    Navigate into your new site’s directory and install the necessary dependencies.

    ```shell
    # Navigate to the directory
    cd easygo/

    # Install the dependencies
    yarn
    ```

1.  **Open the source code and start editing!**

    Open the `easygo` directory in your code editor to view the components!

1.  **Browse your stories!**

    Run `yarn storybook` to see your component's stories at `http://localhost:6006`

1.  **Deploy to Chromatic**

    Run `npx chromatic --project-token=CHROMATIC_TOKEN` to deply your components.

## 🔎 What's inside?

A quick look at the top-level files and directories included with this template.

    .
    ├── .storybook
    ├── node_modules
    ├── public
    ├── scripts
    ├── src
    ├── .babelrc
    ├── .gitignore
    ├── yarn.lock
    ├── package.json
    ├── LICENSE
    ├── rollup.config.json
    └── README.md

2.  **`.storybook`**: This directory contains Storybook's [configuration](https://storybook.js.org/docs/react/configure/overview) files.

3.  **`node_modules`**: This directory contains all of the modules of code that your project depends on (npm packages).

4.  **`public`**: This directory will contain the development and production build of the site.

5.  **`scripts`**: This directory will contain all the modules required should you want to setup Typescript in your project.

6.  **`src`**: This directory will contain all of the code related to what you will see on your application.

7.  **`.babelrc`**: This file tells [babel](https://babeljs.io/) how to transpile the application's code.

8.  **`.gitignore`**: This file tells git which files it should not track or maintain during the development process of your project.

9.  **`.rollup.config.json`**: This is a configuration file for [rollup.js](https://rollupjs.org/guide/en/). Rollup is a module bundler for JavaScript which compiles small pieces of code into something larger and more complex, such as libraries or applications.

10. **`package.json`**: Standard manifest file for Node.js projects, which typically includes project specific metadata (such as the project's name, the author among other information). It's based on this file that npm will know which packages are necessary to the project.

11. **`LICENSE`**: The template is licensed under the MIT licence.

12. **`yarn.lock`**: This is an automatically generated file based on the exact versions of your npm dependencies that were installed for your project. **(Do not change it manually).**

13. **`README.md`**: A text file containing useful reference information about the project.
