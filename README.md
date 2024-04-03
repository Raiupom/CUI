# [CUI - a terminal styled website](https://raiupom.github.io/CUI)

Highly customizable, easy-to-use, and minimal terminal styled website template, powered by Next.js.

After you cloned this repository, simply run `yarn install && yarn dev` and start editing `config.json` to build your website!

## Ship your CUI site

**CUI** requires the `yarn` package manager. You can install `yarn` [here](https://classic.yarnpkg.com/lang/en/docs/install/).

Simply run the following commmand in your terminal:

```bash
sh -c "$(curl -fsSL https://raw.github.com/Raiupom/CUI/main/install/install.sh)"
```

This will install **CUI** to the current directory. You can start building your website with:

```bash
cd CUI && yarn dev
```

Start editing `config.json` and try saving and see the updated changes!

Alternatively, you can clone this repository to a location of your choosing

```bash
git clone https://github.com/Raiupom/CUI.git && cd CUI
```

Then install dependencies and start developing there:

```bash
yarn install && yarn dev
```

### Docker Usage

First, clone the project and edit `config.json` to your liking. Then run the following to start the container in the background:

```shell
docker-compose up -d
```

If you **know** what you were doing, you can also try changing `Dockerfile` & `docker-compose.yml`!
Learn more about Docker [here](https://docs.docker.com/get-started/overview/ 'here').

## Configuration

### Basic Configuration

90% of **CUI**'s configurations are done through the `config.json` file.

```javascript
{
  "readmeUrl": // create a Github README and link it here!
  "title": // title of the website
  "name": // your name, included in 'about' command
  "ascii": // ascii art to display
  "social": {
    "github": // your handle
    "linkedin": // your handle
  },
  "email": // your email
  "ps1_hostname": "CUI" // hostname in prompt
  "ps1_username": "visitor", // username in prompt
  "resume_url": "../resume.pdf", // path to your resume
  "non_terminal_url": "W",
  "colors": {
    "light": {
      ...
    },
    "dark": {
      ... // you can use existing templates in themes.json or use your own!
    }
  }
}
```

Feel free to change it as you see fit!

### Themes

You can find several pre-configured themes in `themes.json`, and you can replace the colors in `config.json` with the theme color you like! The themes are based on the themes on [this website](https://glitchbone.github.io/vscode-base16-term/#/).

### Favicons

Favicons are located in `public/`, along with the other files you may want to upload to your website. I used this [website](https://www.favicon-generator.org/) to generate favicons.

### Banner

You may also want to change the output of the `banner` command. To do that, simply paste your generated banner in `src/utils/bin/commands.ts`. I used this [website](https://manytools.org/hacker-tools/ascii-banner/) to generate my banner.

### Advanced Configuration

If you want to further customize your page, feel free to change the source code to your liking!

## Deploy on Github

You can simply deploy this Next.js app by creating a github repository in minutes.

1. Replace `repository_name` in `next.config.js` with your repository name.
```javascript
module.exports = {
  basePath: process.env.GITHUB_ACTIONS && "/repository_name", // your repository name
  trailingSlash: true,
};
```
2. To get permission to auto deploy this app when `git push`, you need provide a created *fine-grained personal access token*. For details, see ["About personal access tokens"](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). 
If you already have one, named `token_name`, change `${{ secrets.GITHUB_TOKEN }}` to `${{ secrets.token_name }}` in `.github/workflows/deploy.yml`.
3. In `.gitignore`, make sure `/.next`, `/node_modules` and `/out` have been included.
```bash
.next
node_modules
out
```
4. Create your repository in GitHub, and `url` of your site should be like `https://username.github.io/repository_name/`. Then push local repository to GitHub as follows.
```bash
cd /path/to/repository
git init
git add .
git status
git commit
git remote add origin git@github.com:username/repository_name.git
git branch -M main
git push -u origin main
```
5. Check the `gh-pages` branch has been created, and `Actions` workflow have been completed.
6. Go repository's `Settings`, then `Pages` in sidebar, and click on `Visit site`.

## Credit

Based on 
- Cveinnt's [LiveTerm](https://github.com/Cveinnt/LiveTerm)
- M4TT72's [Terminal](https://github.com/m4tt72/terminal)
