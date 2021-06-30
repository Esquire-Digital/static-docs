## Text Editor

<a href="https://code.visualstudio.com/" target="_blank" rel="noreferrer">
  <img src="../_media/vscode.png" class="icon" alt="VSCode icon"/>
</a>

The recommended text editor, especially for the work you'll do with Esquire Digital Static, is [Visual Studio Code](https://code.visualstudio.com). It likely requires no introduction, but it is a lightweight and fast text editor that has all the functionality required for rapid web development without the bloat of typical IDEs.

## VSCode Extensions

The below extensions are _greatly_ recommended to ensure code standards are maintained, and ease your development process:

- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag) - Automatically closes HTML or JSX tags when typing them out
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag) - Automatically edits both the closing and opening HTML or JSX tags when renaming them
- [Gatsby Snippets](https://marketplace.visualstudio.com/items?itemName=nickytonline.vscode-gatsby-snippets) - Provides helpful code snippets for faster/easier development with Gatsby.js
- [GraphQL](https://marketplace.visualstudio.com/items?itemName=GraphQL.vscode-graphql) - Adds syntax highlighting and support for GraphQL queries
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) - Adds syntax highlighting for TailwindCSS
- [Headwind](https://marketplace.visualstudio.com/items?itemName=heybourn.headwind) - An opinionated formatter and sorter for TailwindCSS
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - An amazing code formatter for JS, HTML and many other languages
- [Rainbow Brackets](https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets) - Color codes brackets on the same indentation level
- [Tailwind Twin IntelliSense](https://marketplace.visualstudio.com/items?itemName=lightyen.tailwindcss-intellisense-twin) - Adds IntelliSense and support for twin.macro
- [vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components) - Adds highlighting for styled components
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) - Syntax support for .env files
- [Better TOML](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml) - TOML syntax highlighting

Feel free to add more if you want, always look for ways to improve the development process and make our lives easier! Extension setup via command line below.

**Unix**:

```sh
bash <(curl -Ls https://gist.githubusercontent.com/RHartman99/1cdb30838cda19a2b00e36239f120fa0/raw/0577138e45d57b81e5e8f6869f616f73977c9e18/setup.sh)
```

**Windows (Powershell)**:

```powershell
iex ((New-Object System.Net.WebClient).DownloadString('https://gist.githubusercontent.com/RHartman99/1cdb30838cda19a2b00e36239f120fa0/raw/0577138e45d57b81e5e8f6869f616f73977c9e18/setup.sh'))
```

## Software & Tools

Esquire Digital Static uses Gatsby.js as its static site generator, and Netlify as a host. As such, you'll want to install the following:

- [Node.js](/development/setup?id=nodejs) (v12.13 or newer)
- Git
- Netlify CLI
- Esquire CLI (optional)

### Node.js

[Node.js](https://nodejs.dev/learn) is an environment that can run JavaScript outside of a browser. Without it, Esquire Digital Static could not execute the JavaScript necessary to generate sites. Gatsby, the static site generator used by Esquire Digital Static, lists Node.js v12.13 or newer as a core dependency.

Automatically installed alongside Node.js, [npm](https://docs.npmjs.com/about-npm) (Node Package Manager) allows us to easily install and manage Node.js packages. This enables us to use powerful libraries that others create.

To learn how to install Node.js in detail, follow Gatsby's [tutorial](https://www.gatsbyjs.com/docs/tutorial/part-0/#installation-guide).

### Git

Git is the leading version control system that is used to maintain different versions of code. Git enables us to create special versions of our code that should not be released, and keep a continual backlog of versions should something go wrong. It also allows us to easily collaborate on the same code project, without having to tediously merge our changes; Git handles this for us.

- [Install Git on macOS](https://www.atlassian.com/git/tutorials/install-git#macos)
- [Install Git on Windows](https://www.atlassian.com/git/tutorials/install-git#windows)
- [Install Git on Linux](https://www.atlassian.com/git/tutorials/install-git#linux)

We use GitHub to host our Git repositories for Esquire Digital Static because it has wonderful integrations with Netlify's deploy previews. For this reason, make sure you have your GitHub account handy, and ensure it is in the [Esquire Digital Organization](https://github.com/Esquire-Digital).

### Netlify CLI

Netlify, our host for static sites, has a command line interface that makes debugging builds much easier. Further, if you ever need to test Netlify features locally such as [serverless functions](https://www.netlify.com/products/functions/), commands like `netlify develop` are a godsend.

To install Netlify's CLI:

```sh
npm i -g netlify-cli
```

### Esquire CLI

A custom executable is included in the Esquire Digital Static repository that helps automates some common operations, such as generating boilerplate code. To install it, simply run the below command in the project's directory.

```sh
npm link
```

Parts of this documentation will include the _easy_ way of doing things, which involves using the Esquire CLI.
