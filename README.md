# Remarkable Actions
Generate a CI/CD [remark](https://github.com/gnab/remark) slideshow from a single markdown and GitHub actions.

[Example Slideshow](https://rreichel3.github.io/Remark-Pages-Example) 

[Example Repo](https://github.com/rreichel3/Remark-Pages-Example)


## Setup

### Create a branch to serve your page
This branch should be different from your `main` or `master` branch. I'd recommend just calling it something simple like `pages`.  

### Author Your Presentation
Create a markdown file in your repo with your presentation and save it as `presentation.md` in the root of the repository. This can be as simple or complex as you'd like.  

If you want to name it something else or place it elsewhere no big deal - you'll need to add the `markdown-path` option to your actions config and it should pick it up. 

If you want to quickly test if you're up and running, feel free to use this boilerplate:
```markdown
class: center, middle

# Title

---

# Agenda

1. Introduction
2. Deep-dive
3. ...

---

# Introduction
```


### Add an Actions File
I recommend using the following boilerplate in the file `.github/workflows/deploy-presentation.yml` This will ensure you only build a new presentation when a new commit hits your default branch:
```yaml
on:
  # Trigger the workflow on push or pull request,
  # but only for the master branch
  push:
    branches:
      - main
      - master

jobs:
  deploy_presentation:
    runs-on: ubuntu-latest
    name: Generate a Remark Presentation
    steps:
    - id: generate-presentation
      uses: rreichel3/remarkable-action
      #with:
        #pages-branch: pages (Default)
        #markdown-path: ./presentation.md (Default)
```

### Browse to your page!
Create a commit on your default branch, let the action run then try to browse to your page! 
