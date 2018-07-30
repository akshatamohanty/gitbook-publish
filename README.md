## About
This module helps publish a Gitbook to gh-pages using the command `gitpub`


## What it does
Once installed, the `gitpub` command is automatically available. Running the command:
- Builds the gitbook using `gitbook build`
- Checks out to the `gh-pages` branch
- Deletes the previous version in `gh-pages`
- Extracts the files from the _book_ folder and places them outside
- Commits the new version to `gh-pages`


## Usage
- Install the package: `npm install gitbook-publish@latest`
- Navigate to the branch that contains all the markdown files for your Gitbook
- Delete the `gh-pages` branch if it already exists
- Run command: `gitpub`

## Integration with Travis
An example file for Travis Integration. The USER_NAME, GITHUB_TOKEN and GITHUB_REPO environement variables will need to be set in the Travis environment.
```
    language: node_js
    node_js:
      - "6"
    before_script:
      - npm install gitbook-cli
      - npm install gitbook-publish@latest
    script: 
      - gitpub
      - git branch
      - git remote -v
      - git config --global user.email "akshatamohanty@gmail.com"
      - git config --global user.name "Akshata"
      - git push --force "https://{USER_NAME}:${GITHUB_TOKEN}@github.com/${GITHUB_REPO}" gh-pages 
```

## Future Improvements
- Add flag to push with github username and password
- Automatically detech if `gh-pages` exists
- Inbuilt Travis Integration
