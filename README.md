# Eleventy - 11ty - starter kit

1:07

11ty is a minimalist and very fast way to create static sites (SSG) using markdowns and engine templates in JS ecosystem.
The **purpose** of this project is to be used as a starter point to enable even **faster develpment**.
Although there're litlle things to set up when starting with 11ty, the starter kit ease you those tasks.

## How this project is configured

The starter kit has been thougth as a basic strucure for a micro-blog or wiki-page to be deployed using github pages mainly.
Although, it will work perfectly fine in case you want to deploy it on any other shared hosting service or so.
There are some commands cutomized for github pages service that would require updates from your side and maybe extra manual steps not covered here.

With that said. The starter kit uses [Nunjucks](#while-developing) for HTML main pages generation and in-built markdown capabailities for each post.

## Basic installation

If you want to see how to set a 11ty project from scratch, go [here](#installation-from-scratch)

- Download and install nodejs > 14v
- Clone the starter kit repository
- Get in the folder
- Type the following commands:

```sh
npm i
```

```sh
npm start
```

- Finally, click on the link for opening your browser

## Execution commands scripts

- Run development mode and start coding

```sh
npm run dev && code .
```

- Build the project

```sh
npm run build
```

## While developing

- If using a template engine, it's highly likely that its format isn't recognised by vscode default settings, so install the proper extension.
- For this project, the template engine chosen is Nunjucks (a jinja2 template based, developed by mozilla)
  - Recommended vscode plugin:

    Name: Nunjucks Template
    Id: eseom.nunjucks-template
    Description: Formatting, Syntax Highlighting, Hover, and Snippets for Nunjucks
    Version: 0.5.1
    Publisher: eseom
    VS Marketplace Link: <https://marketplace.visualstudio.com/items?itemName=eseom.nunjucks-template>

## Official sites for docs reference

- [Eleventy 11ty](https://www.11ty.dev/)
- [Eleventy 11ty Docs](https://www.11ty.dev/docs/)
- [Eleventy 11ty Images](https://www.11ty.dev/mascot/)
- [Nunjucks](https://mozilla.github.io/nunjucks/)
- [Jinja2](https://jinja.palletsprojects.com/en/3.1.x/)

## Demo link

[11ty starter kit tutorial]

### Installation from scratch

- Once nodejs is installed, create a folder to host the project and get in it
- Type the following commands:

```sh
git init && npm init -y
```

```sh
echo "node_modules\ndist\n.vscode" > .gitignore
```

- Install the required and desired dependencies

```sh
npm i @11ty/eleventy -DE
```

- Creating a folder structure and placing basic files

```sh
mkdir src/_data src/_includes src/js src/css src/assets
```

```sh
touch .eleventy.js src/index.njk src/js/index.js src/css/index.css
```

- Changing default 11ty settings -> File: .eleventy.js

```js
module.exports = function (eleventyConfig) {
  return {
    dir: {
      input: 'src',
      output: 'dist'
    }
  }
}
```

- Customazing package.json

```json
{
  "main": ".eleventy.js",
  "scripts": {
    "start": "eleventy --serve",
    "dev": "eleventy --serve",
    "clean": "rm -rf dist",
    "build": "npm run clean && eleventy",
    "deploy": "npm run build && npx gh-pages -d dist"
  },
}
```

- Installing template engine and recommended [plugin](#while-developing)
- Update your global settings.json vscode file, or create a specific one for the project, following the plugin instructions

```sh
mkdir .vscode && touch settings.json
```

```json
"vsicons.associations.files": [
  { "icon": "nunjucks", "extensions": ["njk"], "format": "svg" }
],
"emmet.includeLanguages": {
  "njk": "html"
},
```

- Create your custom structure and HTML pages for your views

```sh
mkdir src/posts
```

```sh
touch src/about.njk src/contact.njk src/blog.njk
```

- Place your posts views (if following this example) within its folder

```sh
touch src/posts/whatever-the-name-of-your-post.md
```
